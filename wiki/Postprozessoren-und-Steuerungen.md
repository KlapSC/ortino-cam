# Postprozessoren und Steuerungen

Jede Steuerung versteht ihren eigenen G-Code-Dialekt. Ein **Postprozessor** übersetzt die berechneten Werkzeugwege in diesen Dialekt: Kopf, Fuß, Werkzeugwechsel, Einheiten, Kommentare, Wartezeiten. Er besteht aus einer kleinen Textdatei (TOML-Einstellungen plus Vorlagen im Jinja-Format). Die Bewegungszeilen erzeugt das Programm selbst, deshalb ist die Ausgabe **deterministisch**: Gleiche Eingabe ergibt identischen G-Code.

> **Ehrlich zum Stand:** An einer echten Maschine erprobt ist bisher nur die **Ultimate Bee mit xPRO V5** (GRBL, Version 0.3.3). Alle anderen Profile sind nicht an einer Maschine erprobt. Bei **UCCNC, Centroid, ShopBot, MASSO und PlanetCNC** kommt hinzu: Sie sind nur nach den Unterlagen der Hersteller geschrieben. Manche Seiten waren dabei nicht abrufbar, gelesen wurden Auszüge. Name und Beschreibung dieser Profile tragen den Hinweis »nicht erprobt«. Fahre bei jeder Steuerung zuerst einen **Luftschnitt**, bevor du schneidest.

## Mitgelieferte Profile

| Profil | Steuerung | Direkt anbindbar? | Besonderheiten |
|---|---|---|---|
| `grbl` | GRBL 1.1 (mm) | **ja** | Werkzeugwechsel als Pause (`M0`) mit Meldung, Bögen `G2`/`G3`, Endung `.nc` |
| `grblhal` | grblHAL | ja | wie GRBL |
| `fluidnc` | FluidNC | ja | wie GRBL, Endung `.gcode` |
| `mach3` | Mach3 und Mach4 | nein, nur Export | `M6`-Werkzeugwechsel, Zeilennummern, Endung `.tap` |
| `linuxcnc` | LinuxCNC | nein, nur Export | `M6`, Endung `.ngc` |
| `uccnc` | UCCNC | nein, nur Export | `M6`, Wartezeiten in Millisekunden. **Nicht erprobt.** |
| `centroid` | Centroid Acorn und Oak (CNC12) | nein, nur Export | `M6`, Kommentare mit Semikolon, Programmende `M30`, Endung `.cnc`. **Nicht erprobt.** |
| `shopbot` | ShopBot PRS und PRSalpha | nein, nur Export | **G-Code, kein OpenSBP (`.sbp`)**. Zoll, Zeilennummern, Bögen als Linien, Werkzeugwechsel als Pause. **Nicht erprobt.** |
| `masso` | MASSO G3 und Touch | nein, nur Export | `T5 M06`, Wartezeiten in Millisekunden, kein `G43`. **Nicht erprobt.** |
| `planetcnc` | PlanetCNC TNG (Mk3 und Mk4) | nein, nur Export | `M6`, Rahmen aus `%`-Zeilen, Programmende `M2`. **Nicht erprobt.** |

**Direkt anbinden** (G-Code live an die Maschine senden) lässt sich nur eine GRBL-kompatible Steuerung: GRBL 1.1, grblHAL oder FluidNC über USB oder Netzwerk, siehe [Fräsen an der Maschine](Fräsen-an-der-Maschine). Für alle anderen exportierst du eine Datei und lädst sie in der Steuerung. Profile mit `M6`-Werkzeugwechsel kann das Programm **nicht** an eine GRBL-Steuerung streamen, denn GRBL kennt `M6` nicht. Das Programm lehnt das ab und schlägt ein GRBL-Profil vor.

### Das Profil wählen

Das Profil kommt aus dem Maschinenprofil (zum Beispiel `grbl` bei der Ultimate Bee). Im Schritt »Fräsen« kannst du es unter **Postprozessor** ändern. Ein Katalogeintrag wie die Onefinity Elite Gen 1 bringt das passende Profil (`masso`) schon mit.

### Was du bei den neuen Profilen wissen solltest

* **Kein `G43`:** Kein Profil setzt einen Längenversatz. Der Z-Nullpunkt gehört zum Werkstück. Wer Werkzeugtabelle oder Wechsler der Steuerung nutzt, ergänzt die passende Zeile in `tool_change_block`.
* **Alle Achsen in jeder Zeile** bei den Profilen mit `M6`: So bleibt das Programm richtig, wenn die Steuerung beim Wechsel Achsen bewegt. Die Dateien werden dadurch größer.
* **Wartezeiten in Millisekunden** bei UCCNC und MASSO (`G4 P2000` heißt dort zwei Sekunden). Bei UCCNC kann zudem ein eigener »M3 Delay« der Steuerung hinzukommen: Stelle einen der beiden auf 0. Wer in UCCNC auf Sekunden umgestellt hat, setzt in einer Kopie des Profils `dwell_ms = false`.
* **ShopBot** versteht G-Code nur als Teilmenge. OpenSBP gibt ortino.CAM nicht aus. Die Bogenkonvention und Klammerkommentare sind nicht belegt. Wer sie geprüft hat, kann `arcs = true` in einer Kopie einstellen.
* **PlanetCNC:** Ob `G4 P` dort Sekunden oder Millisekunden meint, ist nicht belegt. Gebaut ist nach Sekunden. Der Luftschnitt zeigt es, falls es nicht stimmt.
* **Absaugung** (`M7`, `M8`, `M9`, `M62` bis `M65`) funktioniert mit allen Profilen. Welche Ausgangsbefehle deine Steuerung kennt, weiß das Programm für die neuen Profile nicht (die Prüfliste meldet dann »unbekannt«).

## Wie sicher ist die Ausgabe?

* Koordinaten werden einzeln gerundet, es summiert sich nichts auf. In Zoll gibt das Programm mindestens vier Stellen bei Koordinaten und zwei beim Vorschub aus.
* **Bögen werden nachgerechnet:** GRBL lehnt einen Bogen ab, dessen Anfangs- und Endradius nach dem Runden zu stark abweichen (`error:33`), und der Auftrag bliebe mit laufender Spindel im Material stehen. ortino.CAM rechnet jeden Bogen mit den gerundeten Ausgabezahlen nach und gibt zweifelhafte Bögen als kurze Strecken aus. Danach liest ein zweiter, unabhängiger Prüfer den fertigen G-Code noch einmal und verweigert ihn, falls ein Bogen die Grenze trotzdem verletzte.
* Kommen mehrere Werkzeuge vor und gibt das Profil keinen Stopp aus, fügt das Programm trotzdem einen ein (`M5`, Meldung, `M0`) und warnt. Es fährt nie mit den Bahnen des nächsten Werkzeugs weiter, ohne dass die Steuerung angehalten hat.

Das alles prüft, **was ortino.CAM ausgibt**. Ob deine Steuerung die Datei annimmt und richtig fährt, zeigt nur ein Luftschnitt.

## Eigene Postprozessoren

Du kannst jedes Profil als Vorlage nehmen und ändern.

* **In der Oberfläche:** Im Postprozessor-Dialog ein Profil als Vorlage wählen, bearbeiten, den **Selbsttest** laufen lassen, die **Live-Vorschau** am aktuellen Projekt ansehen und speichern.
* **Als Datei:** Lege eine `.toml`-Datei in den Ordner `posts` im Datenverzeichnis (unter Windows `%APPDATA%\ortino.CAM\posts\`). Sie wird beim Start geladen. Hat sie die gleiche `id` wie ein mitgeliefertes Profil, überschreibt sie es.
* **Per Kommandozeile:** `ortino posts` listet alle Profile, `ortino gcode projekt.ocam --post meinprofil` erzeugt Code (mehr unter [Claude, MCP und API](Claude-MCP-und-API)).

Die wichtigsten Einstellungen:

| Schlüssel | Bedeutung |
|---|---|
| `id`, `name` | Kennung und Anzeigename (Pflicht) |
| `extension`, `eol` | Dateiendung, Zeilenende (`"\r\n"` für Windows-Steuerungen) |
| `units`, `decimals` | `mm` oder `inch`, Nachkommastellen |
| `arcs`, `arc_tolerance` | Bögen als `G2`/`G3` oder in Linien aufgelöst |
| `line_numbers`, `comments` | Zeilennummern, Kommentarstil (Klammern, Semikolon oder keine) |
| `tool_change` | `pause`, `m6` oder `none` |
| `spindle_wait`, `dwell_ms` | Wartezeit nach dem Spindelstart, Millisekunden statt Sekunden |
| `spindle_on`, `spindle_off` | Texte für Spindel an und aus (`M3 S{rpm}`, `M5`) |
| `header`, `footer`, `tool_change_block` | Vorlagen für Kopf, Fuß und Werkzeugwechsel |

In den Vorlagen stehen Variablen wie `project.name`, `sheet.thickness`, `tools`, `safe_z` und `time_min` zur Verfügung. Undefinierte Variablen sind ein Fehler, damit Tippfehler auffallen. Der **Selbsttest** erzeugt aus einem festen Testprogramm mit zwei Werkzeugen G-Code und prüft unter anderem Spindel an und aus, Programmende, Einheit, Bögen und Werkzeugwechsel. **Er ersetzt nicht das Probefahren.**

## Dein Profil beitragen

Hast du ein Profil für eine Steuerung gebaut oder verbessert? Dann freuen wir uns über einen Pull Request mit der Datei im Ordner `postprozessoren/` des öffentlichen Repositorys, dazu ein Satz, **auf welcher Steuerung und Firmware du es getestet hast** und wie (an der Maschine oder nur die Ausgabe geprüft). Die Regeln stehen in der [CONTRIBUTING.md](https://github.com/KlapSC/ortino-cam/blob/main/CONTRIBUTING.md), eine Kurzfassung auf der Seite [Mitmachen und Tests](Mitmachen-und-Tests). Ein Bericht über einen Test an einer echten Steuerung hilft auch dann, wenn etwas nicht klappt.

## Weiter

* [Maschine einrichten](Maschine-einrichten)
* [Fräsen an der Maschine](Fräsen-an-der-Maschine)
