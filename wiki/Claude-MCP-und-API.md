# Claude, MCP und API

ortino.CAM lässt sich von außen steuern: von **Claude** (Claude Desktop, Claude Code oder jedem anderen Programm, das das *Model Context Protocol*, kurz **MCP**, spricht), von eigenen Programmen über eine **lokale Schnittstelle (API)** und von der **Kommandozeile** `ortino`. Zusätzlich gibt es kleine **Skripte** und einen **Assistenten im Programm**.

**Du brauchst das alles nicht.** Alles Wesentliche läuft ohne Claude und ohne Anthropic-Schlüssel. Diese Seite ist für alle, die es ausprobieren wollen.

> **Ehrlich zum Stand:** Das Programm ist eine frühe Version, und die Claude-Anbindung kann wie alles darin Fehler haben. Maschinenbefehle über Claude oder die Schnittstelle sind wie alle Maschinenfunktionen nur gegen den Simulator geprüft (außer dem, was auf [Fräsen an der Maschine](Fräsen-an-der-Maschine) als erprobt steht). Der Assistent im Programm wurde laut Dokumentation (Stand Oktober 2026) nur gegen einen nachgebauten Server getestet, nicht gegen die echte Anthropic-Schnittstelle. Der Not-Aus der Maschine bleibt die letzte Sicherung. Siehe den [Haftungsausschluss](https://github.com/KlapSC/ortino-cam#haftungsausschluss).

## Der MCP-Server `ortino-mcp`

Mit dem MCP-Server können Claude und andere Clients zeichnen, Bearbeitungen anlegen, die Prüfliste abarbeiten und G-Code erzeugen, **live im Programmfenster**. Jede Aktion ist ein Rückgängig-Schritt (»KI: 3 Formen anlegen«, Strg+Z nimmt sie zurück). Das Programm `ortino-mcp.exe` liegt dem Windows-Installer bei, neben `ortino.CAM.exe`.

### Einrichten

1. **Externe Steuerung einschalten (empfohlen):** Datei → *Erweiterungen & KI …* → **Externe Steuerung erlauben**. ortino.CAM startet dann eine Schnittstelle, die **nur auf diesem Rechner** (`127.0.0.1`) mit einem zufälligen Zugangsschlüssel erreichbar ist. In der Statusleiste steht »Externe Steuerung«. Ohne diesen Schritt arbeitet `ortino-mcp` **eigenständig** mit einem eigenen Projekt im Speicher, und das Programmfenster sieht davon nichts.
2. **Claude Desktop:** *Einstellungen → Entwickler → Konfiguration bearbeiten* öffnet die Datei `claude_desktop_config.json`. Ergänze den Eintrag (den richtigen Pfad zeigt ortino.CAM unter *Erweiterungen & KI → Claude verbinden* zum Kopieren an):

   ```json
   {
     "mcpServers": {
       "ortino-cam": {
         "command": "C:\\Users\\<Name>\\AppData\\Local\\ortino.CAM\\ortino-mcp.exe",
         "args": []
       }
     }
   }
   ```

   Backslashes werden in JSON verdoppelt. Gibt es schon andere Server, ergänze nur den Block `"ortino-cam": { … }`. Danach Claude Desktop **neu starten**. ortino.CAM erscheint bei den Werkzeugen.
3. **Claude Code:** `claude mcp add --scope user ortino-cam -- "C:\Users\<Name>\AppData\Local\ortino.CAM\ortino-mcp.exe"`. Mit `/mcp` prüfst du, ob »ortino-cam« verbunden ist.
4. **Ausprobieren:** Bitte Claude zum Beispiel: »Entwirf in ortino.CAM ein Türschild 300 × 150 mm mit dem Text ›Werkstatt‹, vier Befestigungslöchern Ø5 und einer Außenkontur mit Haltestegen. Prüfe das Ergebnis und zeig mir ein Vorschaubild.« Claude benutzt dann Werkzeuge wie `get_project`, `create_shapes`, `add_operation`, `run_checklist` und `render_preview`.

Optionen für `"args"` (Auswahl): `--attach` (nur an das laufende Programm anhängen), `--headless` (immer eigenständig), `--project <Datei>` (eigenständig mit dieser Datei), `--readonly` (nur lesende Werkzeuge), `--allow-machine` und `--allow-danger` (siehe unten), `--lang de` (Werkzeugbeschreibungen auf Deutsch), `--log <Datei>` (alle Nachrichten mitschreiben), `--check` (Verbindung prüfen).

### Was Claude kann

Es gibt bewusst wenige, zugeschnittene Werkzeuge: Projekt lesen und ändern, Formen anlegen und ändern (auch Boolesche Operationen, Verrunden, Knoten bearbeiten, Plattenplaner), Bearbeitungen anlegen und ändern, Werkzeuge verwalten, Prüfliste, Simulation und Vorschaubild, Vorschläge für Schnittwerte, Vorlagen ausfüllen, SVG/DXF importieren und exportieren. Alle Methoden der Schnittstelle listet `list_api_methods`, aufrufen lassen sie sich mit `call_api`. Zahlen sind Millimeter, Längen dürfen Formeln sein (`Breite/2 - 5mm`) und bleiben dann parametrisch.

**Dateien:** Claude hat keinen Zugriff auf deine Festplatte. Lesen darf es nur aus **freigegebenen Leseordnern** (Ordner des gespeicherten Projekts, `Dokumente\ortino.CAM` und Ordner, die du unter *Erweiterungen & KI → Claude verbinden* freigibst). Schreiben darf es nur in **Ausgabeordner**, nur mit passender Endung und nie in Systemordner. Alternativ übergibst du Inhalte als Text oder lädst große Dateien in Teilen hoch.

## Die vier Sicherheitsstufen

Alles, was von außen kommt, ist einer Stufe zugeordnet:

| Stufe | Was erlaubt ist | Standard |
|---|---|---|
| `read` | Projekt, Prüfliste, Vorschau, Simulation lesen | erlaubt |
| `edit` | Projekt im Speicher ändern. Jede Aktion ist genau ein Rückgängig-Schritt, bei einem Fehler bleibt alles unverändert. | erlaubt (außer mit `--readonly`) |
| `machine` | Verfahren, Spindel, Nullpunkt, Referenzfahrt, Antasten, Verbinden | **gesperrt**, jede Aktion mit Bestätigung im Programm |
| `danger` | Nicht rückgängig zu machen: Job starten, Dateien überschreiben oder löschen, Prüfliste übergehen, Nutzerbibliotheken ändern | **gesperrt**, jede Aktion mit Bestätigung im Programm |

* `machine` und `danger` brauchen **mehrere Freigaben**: die Option beim Start (`--allow-machine`, `--allow-danger`), die Freigabe unter *Erweiterungen & KI* und die **Bestätigung jeder einzelnen Aktion** in einem Dialog im Programm. Esc lehnt ab, nach 120 Sekunden lehnt das Programm selbst ab. Gesperrte Werkzeuge erscheinen gar nicht erst in der Liste.
* **Nie:** Einstellungen der Steuerung schreiben (`$…=` und Ähnliches). Das geht auf keiner Stufe, auch nicht über die Schnittstelle. Freie Zeilen an die Steuerung sind auf einfache, druckbare Zeichen und eine Zeile begrenzt, und Befehle, die dauerhaft etwas in der Steuerung speichern, sind ausgeschlossen. Die Prüfliste sperrt Export und Maschinenstart bei Fehlern weiterhin.
* **Skripte** bekommen nie mehr Rechte als der, der sie startet.
* **Die Handy-Fernbedienung** ist für Claude, die Schnittstelle und Skripte nie erreichbar.

### Hochladen ins Community-Portal: nur als Entwurf

Claude kann ein Projekt als **Entwurf** im [Community-Portal](Community-Portal) ablegen. Das ist **standardmäßig aus** und lässt sich nur im Programm einschalten (*Erweiterungen & KI → Claude verbinden → »Hochladen ins Portal erlauben (nur Entwurf)«*). Jeder Upload zeigt dir vorher einen Dialog mit dem genauen Inhalt. Gesendet wird erst nach deiner Bestätigung. Veröffentlichen kannst nur du. Die Datenschutzprüfung (Dateipfade, Benutzernamen) ist Pflicht. Es sind höchstens fünf Anfragen pro Stunde möglich. Anmeldedaten bekommt Claude nie.

## Die lokale Schnittstelle (API)

Bei eingeschalteter externer Steuerung kann jedes Programm auf demselben Rechner die JSON-Schnittstelle benutzen, mit denselben Stufen und Bestätigungen wie Claude. Sie lauscht **nur auf `127.0.0.1`**, verlangt einen zufälligen 256-Bit-Zugangsschlüssel (er steht in der Datei `api.json` im Datenverzeichnis, Windows: `%APPDATA%\ortino.CAM`), lehnt Anfragen aus Webseiten im Browser ab und ist **standardmäßig aus**. Ausschalten oder Beenden des Programms entfernt die Datei sofort.

## Die Kommandozeile `ortino`

Die Kommandozeile erzeugt G-Code und prüft Projekte, ohne dass du das Programmfenster brauchst. Das ist praktisch für Serien oder automatische Abläufe.

| Befehl | Wirkung |
|---|---|
| `ortino gcode <projekt.ocam> [-o datei.nc] [--sheet ID] [--post ID]` | G-Code erzeugen. Bricht bei Fehlern der Prüfliste ab. |
| `ortino check <projekt.ocam>` | Prüfliste ausgeben (Rückgabewert 1 bei Fehlern) |
| `ortino info <projekt.ocam>` | Platten, Bearbeitungen und Zeitschätzung |
| `ortino export <projekt.ocam> --format svg\|dxf [-o datei]` | Vektoren einer Platte exportieren |
| `ortino demo -o beispiel.ocam` | Beispielprojekt »Türschild« schreiben |
| `ortino posts` | Postprozessoren auflisten |
| `ortino ports` | serielle Anschlüsse auflisten |
| `ortino series <vorlage.ocam> <daten.csv> --out <ordner>` | Serienfertigung aus einer Tabelle (siehe [Platten und Möbel](Platten-und-Möbel)) |
| `ortino script list`, `run`, `check` | Skripte auflisten, ausführen, prüfen |
| `ortino rpc <methode> [json]` | JSON-Schnittstelle direkt aufrufen |
| `ortino package pack\|inspect …` | Designpakete für das Portal |
| `ortino --version` | Version |

```text
ortino check  tuerschild.ocam
ortino gcode  tuerschild.ocam -o tuerschild.nc --post grbl
ortino export tuerschild.ocam --format dxf -o tuerschild.dxf
```

Die Kommandozeile ist ein eigenes kleines Programm (`ortino-cli.exe`, im Befehl `ortino`). Sie steckt **nicht** im Installer. Ob sie für deine Version als eigene Datei bereitliegt, steht in den Hinweisen der Version auf der Release-Seite.

## Eigene Werkzeuge als Skripte

Mit kleinen Skripten in der Sprache **Rhai** (ähnlich JavaScript, im Programm eingebaut, nichts zu installieren) baust du eigene Werkzeuge wie Lochraster, Schildrahmen oder Bohrbilder. Eine Skriptdatei (`.rhai`) legst du in den Ordner `scripts` im Datenverzeichnis (*Erweiterungen & KI → Skripte → Ordner öffnen*). Jedes Skript erscheint als Befehl in der Befehlspalette (`Strg+K`, »Skript: …«) mit einem automatisch erzeugten Eingabedialog, auf der Kommandozeile und als Werkzeug für Claude. Das Ergebnis ist **ein** Rückgängig-Schritt, und bei einem Fehler bleibt das Projekt unverändert. Skripte laufen in einer **Sandbox** ohne Datei-, Netzwerk- und Prozesszugriff, mit Zeitlimit (Standard 10 Sekunden). Skripte aus Community-Paketen werden nie ausgeführt.

## Der Assistent im Programm

Der eingebaute **Assistent** ist eine Seitenleiste (Symbol ✦ in der Kopfleiste oder `Strg+L`), in der du Claude Fragen stellst, dir Meldungen der Prüfliste erklären lässt und auf Wunsch Projekte einrichten lässt. Er braucht **deinen eigenen API-Schlüssel von Anthropic**. Ohne Schlüssel funktioniert ortino.CAM vollständig.

* **Datenschutz:** Vor der ersten Nutzung bestätigst du einen Hinweis zur Datenübertragung. **Vorher wird nichts gesendet.** Was du fragst und was Claude zur Antwort braucht, geht an den eingestellten Anbieter (standardmäßig Anthropic). Bilder gehen nur mit, wenn du sie selbst anhängst, mit Vorschau vor dem Senden und einem zusätzlichen Hinweis.
* **Schlüssel:** Unter Windows liegt er im Windows-Anmeldeinformationsspeicher, nicht in Projekten, Einstellungen oder Protokollen.
* **Kosten:** Abgerechnet wird über dein Anthropic-Konto. Der Assistent zeigt die verbrauchten Eingabe- und Ausgabemengen, aber bewusst keine Preise. Das Modell wählst du in den Einstellungen.
* **Rückgängig:** Alle Änderungen einer Antwort sind ein einziger Rückgängig-Schritt. Der Assistent hat höchstens die Stufe `edit`. Maschine und Gefährliches gehören ihm nie.

## Wenn es nicht klappt

| Problem | Lösung |
|---|---|
| Claude Desktop zeigt ortino.CAM nicht | Pfad in der Konfiguration prüfen (doppelte Backslashes), Claude Desktop ganz beenden und neu starten. |
| Änderungen erscheinen nicht im Fenster | `ortino-mcp` arbeitet eigenständig. Externe Steuerung einschalten und Claude Desktop neu starten. Mit `ortino-mcp.exe --attach --check` im Terminal lässt sich das prüfen. |
| »Gesperrt: … braucht die Stufe machine« | Gewollt. Bei Bedarf `--allow-machine` in `"args"` und im Programm die Maschinenbefehle erlauben. Jede Aktion wird bestätigt. |
| »Keine Bestätigung … innerhalb von 120 s« | Der Dialog im Programm wurde nicht beantwortet. |
| »… liest von außen nur Dateien aus freigegebenen Ordnern« | Gewollt. Datei nach `Dokumente\ortino.CAM` legen oder den Ordner freigeben. Alternativ Text übergeben oder in Teilen hochladen. |
| Windows-SmartScreen oder ein Virenscanner blockiert `ortino-mcp.exe` | Die Datei ist nicht einzeln signiert. Wenn du dem Installer vertraust, die Datei einmalig zulassen (siehe [Installation und Updates](Installation-und-Updates)). |
| Installation oder Update meldet, eine Datei könne nicht überschrieben werden | Der Installer beendet `ortino-mcp.exe` selbst (nicht unter Windows erprobt). Hilft das nicht, beende Claude Desktop und starte die Installation neu. |
