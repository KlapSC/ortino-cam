# Maschine einrichten

Damit ortino.CAM weiß, wie groß deine Fräse ist und wie schnell sie fahren darf, braucht es ein **Maschinenprofil**. Das ist eine kleine Datei mit den Verfahrwegen, dem Drehzahlbereich der Spindel, den Vorschüben und dem Postprozessor (siehe [Postprozessoren und Steuerungen](Postprozessoren-und-Steuerungen)). Aus dem Profil rechnet das Programm die Zeitschätzung, die Prüfliste und den Start-Check.

![Assistent „Maschine einrichten“: Maschinenkatalog mit Größen und gekennzeichneten Herstellerangaben](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/einrichtung-light.png)

> **Ehrlich zum Stand:** An einer echten Maschine erprobt ist bisher nur die **Ultimate Bee mit CNC xPRO V5** (Version 0.3.3). Die Maße im Katalog stammen aus Herstellerseiten, Händlertabellen und Nutzerberichten (Stand Oktober 2026) und sind **nicht an Hardware geprüft**. Miss deine Maschine einmal nach, auch wenn ein Wert als »Herstellerangabe« gekennzeichnet ist. Teste den ersten Lauf **ohne Werkzeug und Material**, den Not-Aus in Reichweite.

## Die wichtigste Regel: ortino.CAM schreibt nie in die Steuerung

* Das Programm **liest** die Einstellungen deiner Steuerung (die sogenannten `$`-Werte wie `$130` für den Verfahrweg in X). Es **schreibt sie nie**, auch nicht über die Schnittstelle für Claude oder Skripte.
* Weicht etwas ab, zeigt dir das Programm die Zeile (zum Beispiel `$20=1`) **zum Kopieren**. Senden musst du sie selbst, in der Konsole im Schritt »Fräsen«.
* »Übernehmen« kopiert Werte **aus der Steuerung in das Profil von ortino.CAM**, nie umgekehrt.

## Wo startest du den Assistenten?

Der Assistent »Maschine einrichten« führt dich durch alles in fünf Schritten. Du findest ihn:

* im Schritt **Projekt**,
* im Dialog **Maschinen**,
* in der Befehlspalette (`Strg+K`),
* im Dialog **Neues Projekt**,
* auf der Willkommensseite beim ersten Start. Dort lässt sich das Angebot mit »Später« dauerhaft ausblenden.

## Der Katalog

Der Katalog kennt verbreitete Fräsen mit ihren Größen. Jede Maschine ist gekennzeichnet:

| Kennzeichnung | Bedeutung |
|---|---|
| **Herstellerangabe, bitte prüfen** | Die Maße stammen aus Herstellerangaben oder Händlertabellen, mehrere Quellen stimmen überein, und sie sind plausibel. |
| **ungeprüft** | Die Maße sind abgeleitet, nominell oder widersprüchlich. Das Programm sagt dazu, warum. |
| Eigene Maschine | Nie »geprüft«. Du trägst die Maße selbst ein. |

Vorschub, Eilgang und Beschleunigung im Katalog sind **vorsichtige Startwerte** (höchstens 3 000 mm/min und 100 mm/s²), keine Herstellerdaten. Liest der Assistent die echten Werte aus deiner Steuerung, kannst du sie übernehmen.

| Hersteller | Familien im Katalog | Steuerung |
|---|---|---|
| Bulkman3D | Ultimate Bee (500 bis 1500), Queen Bee Pro | CNC xPRO V5 (GRBL-kompatibel) |
| Carbide 3D | Shapeoko 4, Shapeoko 5 Pro, Nomad 3 | GRBL 1.1 |
| Sienci Labs | LongMill MK2 und MK3 | grblHAL |
| SainSmart | Genmitsu PROVerXL, 3018-PROVer | GRBL 1.1 |
| OpenBuilds | LEAD CNC, WorkBee | GRBL (BlackBox, xPro) |
| Inventables | X-Carve | GRBL (X-Controller) |
| Onefinity | Elite Gen 1 und 2, Pro, Original | MASSO, Redline, Buildbotics: **kein GRBL**, nur G-Code-Export |
| Generisch | 3018, 6040, »Eigene GRBL-Maschine« | frei wählbar |

Fehlt deine Maschine, wähle »Eigene GRBL-Maschine« und trage die Maße selbst ein. Bei Steuerungen ohne GRBL-Protokoll (Onefinity) überspringt der Assistent das Verbinden und den Achsentest und erklärt, warum.

## Die fünf Schritte

1. **Maschine:** Hersteller, Familie und Größe wählen, bei der Ultimate Bee auch die Spindel (1,5 oder 2,2 kW).
2. **Steuerung:** per USB oder Netzwerk verbinden und »Einstellungen lesen«. Die Tabelle zeigt Verfahrwege, Vorschub, Beschleunigung, Spindeldrehzahl, Referenzfahrt und Soft-Limits. Abweichungen vom Profil lassen sich ins Profil übernehmen.
3. **Achsen:** Fräser entfernen, Not-Aus in Reichweite, jede Achse 5 mm fahren und die Richtung bestätigen. Richtig ist: **+X nach rechts, +Y nach hinten (vom Bediener weg), +Z nach oben.** Stimmt eine Richtung nicht, rechnet der Assistent die neue Maske für `$3` aus. Du sendest sie selbst.
4. **Nullpunkt:** Referenzecke, Ursprung der Platte, Z-Null (»Plattenoberseite« oder »Tisch (Opferplatte)«), Sicherheitshöhe und Postprozessor.
5. **Fertig:** Namen vergeben, in der Maschinenliste speichern, für das Projekt verwenden und/oder als Standard für neue Projekte setzen.

Ohne Verbindung geht die Einrichtung mit »Überspringen« weiter. Bei jedem Fehler steht im Schritt eine Lösung, und »Zurück« behält alles Eingegebene.

## Beispiel: Ultimate Bee mit xPRO V5

1. **Kabel und Treiber:** Nimm ein USB-A-auf-USB-C-Kabel. USB-C auf USB-C funktioniert laut Herstellerangabe nicht (von uns nicht geprüft). Unter Windows muss der **CP210x-Treiber** (Silicon Labs) installiert sein. Danach erscheint die Steuerung im Gerätemanager als `COMx`.
2. **Baudrate:** 115200.
3. **Neustart beim Verbinden:** Beim Öffnen des Anschlusses startet die Steuerung neu. Die Meldung `Grbl …` in der Konsole ist normal.
4. Weiter wie oben: Assistent starten, »Ultimate Bee«, Rahmengröße, Spindel, Einstellungen lesen, Achsen prüfen, Nullpunkt.

Die Rahmengrößen 500 × 750, 750 × 750 und 750 × 1000 nennt der Händler nicht. Ihre Verfahrwege sind aus den anderen Größen abgeleitet und deshalb als »ungeprüft« gekennzeichnet.

## Typische Stolperfallen

| Problem | Ursache und Lösung |
|---|---|
| Kein COM-Anschluss in der Liste | USB-Treiber fehlt oder falsches Kabel. Treiber installieren, Anschlüsse aktualisieren. |
| Keine Antwort nach dem Verbinden | Falsche Baudrate oder die Steuerung startet noch neu. Erneut lesen. |
| Verfahrwege 300 × 300 × 300 | Werkseinstellung (`$130` bis `$132`). Nachmessen und setzen, sonst lösen die Soft-Limits falsch aus. |
| `$30 = 1000` | Werkseinstellung: Drehzahlen über 1000 werden still gekappt. `$30` auf die Höchstdrehzahl der Spindel setzen, zum Beispiel `$30=24000`. |
| Referenzfahrt in die falsche Ecke | `$23` (Richtung) und `$3` (Achsrichtung) prüfen. |
| Eine Achse fährt verkehrt herum | Maske `$3` ändern oder das Motorkabel der Achse umpolen. |
| Soft-Limits aus | Sie schützen dann nicht vor Fahrten über den Verfahrweg hinaus. Erst `$22=1` (Referenzfahrt, Endschalter nötig), dann `$20=1`. |
| Laser-Modus an (`$32=1`) | Für eine Fräse falsch: `$32=0`. |
| Berichte in Zoll (`$13=1`) | Positionen wären um den Faktor 25,4 falsch: `$13=0`. |

## Verfahrwege nachmessen

Bei Katalogmaschinen sind die Verfahrwege Vorschläge. Der **Verfahrwege-Assistent** (Dialog »Maschinen« → Verfahrwege → »Verfahrwege messen …«) misst sie an deiner Maschine.

> **Laut Rückmeldung des Betreibers an einer echten Maschine ausprobiert, hat funktioniert** (Ultimate Bee mit xPRO V5; welche Achsen gemessen wurden, ist nicht festgehalten). Sonst gegen den Simulator und Tests geprüft; andere Steuerungen sind nicht erprobt. Erste Messung ohne Material, Spindel aus, Hand am Not-Aus.

1. **Vorbereiten:** verbunden, **Referenzfahrt** ausgeführt (die Maschine fährt zu den Endschaltern und kennt danach ihre Position), Einstellungen gelesen, Anzeige in Millimetern. Der Assistent prüft das und erklärt Fehlendes.
2. **Soft-Limits für die Messung aus:** Sonst begrenzt die Steuerung jede Fahrt auf den alten Wert. Der Assistent zeigt die Zeile `$20=0` zum Kopieren. Du gibst sie selbst in der Konsole ein. Ohne Soft-Limits schützen dich nur kleine Schritte, Aufmerksamkeit und der Not-Aus.
3. **Messen:** Je Achse (X und Y) fährst du mit »Weiter« in kleinen Schritten vom Referenzpunkt weg. Die Schritte werden zum Ende hin kleiner. Steht die Achse kurz vor dem Anschlag, übernimmt »Hier ist das Ende« die Position. Z ist vorbelegt übersprungen, weil Tisch oder Opferplatte im Weg sein können.
4. **Ergebnis:** Verfahrweg = gemessener Weg minus Sicherheitsabstand (Standard 2 mm). Du bekommst die Zeilen `$130=…`, `$131=…`, `$132=…` zum Kopieren und kannst die Werte ins Profil eintragen. Das offene Projekt ändert sich erst, wenn du »Für das offene Projekt übernehmen« wählst.
5. **Prüffahrt:** `$20=1` wieder einschalten und prüfen, dass die Steuerung kurz vor dem Ende anhält.

Gemessen wird ab der Position nach der Referenzfahrt. Das Ergebnis liegt dadurch auf der sicheren Seite.

## Einstellungen der Steuerung lesen

Nach dem Verbinden liest ortino.CAM die Einstellungen (`$$`) **von selbst**, sobald die Steuerung bereit ist: im Leerlauf, ohne Alarm, nie während eines Auftrags. Du kannst das im Start-Check mit »Beim Verbinden automatisch lesen« abschalten und jederzeit per Klick neu lesen. Das Ergebnis fließt in den Start-Check ([Fräsen an der Maschine](Fräsen-an-der-Maschine)). Klappt das Lesen nicht, sagt das Programm das und rechnet mit dem Profil weiter. Verhalten echter Firmware ist dabei **nur gegen den Simulator geprüft**.

## Profil sichern, exportieren, wiederherstellen

* Dein Profil liegt in einer Datei im Datenverzeichnis (unter Windows `%APPDATA%\ortino.CAM`, im Dialog »Über ortino.CAM« steht der Pfad), **nicht** im Programmordner. Ein Update ersetzt nur Programmdateien. Das ist **nicht mit einem echten Windows-Update erprobt**.
* Vor dem Löschen, Ersetzen und Zurückspielen sichert das Programm die Liste automatisch (die letzten 10 Sicherungen).
* Im Dialog »Maschinen« kannst du ein Profil **exportieren** und **importieren**. Der Import zeigt vorher eine Vorschau und legt standardmäßig eine Kopie an. Die Datei enthält nur Zahlen, Schalter und Text, keine Pfade und keine Verbindungsdaten.
* Hast du eine Maschine an einer echten Steuerung benutzt, freuen wir uns über dein Profil (ohne persönliche Notizen) als Beitrag. Mehr dazu auf der Seite [Mitmachen und Tests](Mitmachen-und-Tests).

## Projekt, Liste und Standardmaschine

Jedes Projekt trägt eine **Kopie** seiner Maschine, daneben gibt es die **Maschinenliste** mit deinen eigenen Maschinen. Weichen beide voneinander ab, zeigt der Dialog »Maschinen« das und lässt dich wählen, welcher Stand gilt. Mitgelieferte Vorlagen überschreibt das Programm nie. Als **Standardmaschine für neue Projekte** kannst du eine Maschine aus der Liste festlegen. Bestehende Projekte ändern sich dadurch nie.

### Meine Maschine (ab 0.3.12)

Fester Taster, Opferplatte, Kamera-Kalibrierung und Zubehör (Absaugung, Tastplatte, Werkzeugwechsel) beschreiben die **Maschine**, nicht ein Projekt. Steht die Maschine **in deiner Liste** und ist sie die Standardmaschine, bekommt **jedes neue Projekt** diese Einrichtung mit. Bei einer **mitgelieferten Vorlage** oder einer Maschine nur aus der Projektdatei zeigt das Programm den Hinweis »Diese Einrichtung gilt bisher nur für dieses Projekt. In jedem neuen Projekt haben?« mit dem Knopf **»Als meine Maschine speichern«**: Er legt eine Kopie in deiner Liste an (nie über eine vorhandene), macht sie zur Standardmaschine, und **Strg+Z** holt die Vorlage im Projekt zurück. Für ein älteres Projekt gibt es **»Einrichtung der Maschine aus der Liste übernehmen«**; das Programm vergisst dabei den Z-Bezug und sagt es. *Nur gegen Tests, Simulator und Chromium geprüft.*

Deine Maschinenprofile lassen sich außerdem [im Portal sichern](Sicherung-im-Portal) und auf einem anderen Rechner abrufen.

<!-- videos:start -->
## Videos (English)

* [![Choose the machine and the post-processor (video, English captions)](https://klapsc.github.io/ortino-cam/videos/machine-choose-poster.jpg)](https://klapsc.github.io/ortino-cam/videos/#machine-choose)  
**Choose the machine and the post-processor** · 11 s

Alle Videos: [Videos](Videos).
<!-- videos:end -->

## Weiter

* Nächster Schritt: [Zeichnen und Importieren](Zeichnen-und-Importieren)
* Später an der Maschine: [Fräsen an der Maschine](Fräsen-an-der-Maschine)
* Probleme: [Fehlersuche](Fehlersuche)
