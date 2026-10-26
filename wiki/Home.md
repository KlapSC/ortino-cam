# ortino.CAM Wiki

![ortino.CAM – Vom Entwurf zum Werkstück: CAD/CAM für CNC-Fräsen](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/banner.png)

Willkommen. **ortino.CAM** ist eine **CAD/CAM-Software für CNC-Fräsen** unter Windows: zeichnen, Werkzeugwege berechnen (Profil, Tasche, V-Carving, 3D-Relief), in 3D simulieren, prüfen und direkt an eine **GRBL-Steuerung** wie die der Ultimate Bee (CNC xPRO V5) schicken, alles in einer Anwendung. Mit einem MCP-Server und einer lokalen Schnittstelle lässt sie sich auch von **Claude** und eigenen Skripten steuern.

Dieses Wiki ist für Menschen, die ortino.CAM **benutzen**: Hobby-Fräser, Tischler und Werkstätten. Du musst nichts über den Quelltext wissen. Es beschreibt die veröffentlichte **Version 0.4.2**.

## Bitte zuerst lesen

> **Frühe Version (0.x): nicht alles ist an einer echten Maschine erprobt.** An echter Hardware erprobt sind bisher nur **Taschen, V-Carving, Konturen, Referenzfahrt und Werkzeugwechsel mit der Tastplatte** (Version 0.3.3, Ultimate Bee mit xPRO V5); dazu laut Rückmeldung des Betreibers das **Einrichten des festen Tasters und das Einmessen eines Werkzeugs an ihm** (Version 0.3.10, dieselbe Maschine) und an der **Handy-Fernbedienung** das **Stoppen, Verfahren und Setzen der Nullpunkte** (dieselbe Maschine); ebenso lief laut Betreiber ein Projekt von der **Modellierung mit Claude (MCP)** über **»Reihenfolge optimieren«** bis zum Fräsen (Einzelheiten nicht festgehalten). **Nur gegen Simulator und Tests geprüft** sind der Werkzeugwechsel am festen Taster mitten im Programm, die Messung der Opferplatte, die Höhenkarte, die übrigen Teile der Handy-Fernbedienung (Pause, Anzeige), »An Position fahren«, der Längensensor, **Gewindefräsen, der Wartungsplan, die Kamera auf der Arbeitsplatte** und **alle Postprozessoren außer GRBL** (grblHAL, FluidNC, Mach3/4, LinuxCNC, UCCNC, Centroid, ShopBot, MASSO, PlanetCNC). Die **Beispiele** der Galerie und die **Lektionen** sind **nicht gefräst**, und **Béziers aus SVG und PDF** sind nur mit selbst erzeugten Dateien geprüft. Die Neuerungen aus 0.3.9, 0.3.11, 0.3.12, 0.3.14, 0.4.0 und 0.4.1 (das **Markieren der Opferplatte**, die neue **Tisch-Ansicht**, **Gerätenischen und Raum** im Küchenplaner und die neuen **Möbelarten**; ebenso auch der **Import von STL- und STEP-Modellen**, der **Möbel-Designer**, das Speichern und die Varianten der Küche und die Beschlagbibliothek; ebenso das **doppelseitige Fräsen mit Passstiften** sowie **Farben, Griffe, 3D-Reliefs, Rendering-Export und Touch-Bedienung** des Küchenplaners) liefen nur gegen Tests, Simulator und im Browser (Chromium) und sind nicht systematisch unter Windows (WebView2) geprüft; gefräste Reliefs, importierte Modelle, Möbelstücke und Griffbohrungen sind nie gefräst oder gebaut, der STEP-Import hat nie eine echte CAD-Datei gelesen, das Rendering lief nie auf einer echten Grafikkarte.
>
> **Teste immer zuerst ohne Werkzeug und ohne Material**, mit dem Not-Aus in Reichweite, und lass die Maschine nie unbeaufsichtigt laufen. CNC-Maschinen sind gefährlich. Simulation, Prüfliste und Start-Check sind Hilfen und keine Sicherheitsfunktion. Schnittwerte und Zeiten sind Richtwerte. Lies den **[Haftungsausschluss](https://github.com/KlapSC/ortino-cam#haftungsausschluss)**: ortino.CAM wird ohne Gewährleistung bereitgestellt, die Nutzung erfolgt auf eigene Gefahr.

Die Software entsteht **zum größten Teil mit Claude Code (Anthropic) als Co-Autor**. Anforderungen, Entscheidungen, Abnahme und Veröffentlichung liegen beim Betreiber. Mit Fehlern ist zu rechnen. Deshalb sind Berichte von echten Maschinen so wichtig (siehe [Mitmachen und Tests](Mitmachen-und-Tests)).

**So liest du dieses Wiki:** Wo etwas nur im Simulator, in Tests oder mit erzeugten Bildern geprüft ist, steht das dabei, ebenso wo etwas nicht erprobt ist. Wo nichts steht, ist es dennoch eine frühe Version.

## Wo fange ich an?

| Ich möchte … | Seite |
|---|---|
| das Programm installieren und aktuell halten | [Installation und Updates](Installation-und-Updates) |
| vom leeren Projekt zum ersten Werkstück kommen, mit Beispielgalerie, Einführung und Lektionen | [Erste Schritte](Erste-Schritte) |
| meine Fräse eintragen und die Verfahrwege messen | [Maschine einrichten](Maschine-einrichten) |
| zeichnen, Text setzen, SVG/DXF/PDF oder ein Bild importieren | [Zeichnen und Importieren](Zeichnen-und-Importieren) |
| wissen, was Profil, Tasche, V-Carving und Gewinde tun, und was Gleichlauf und Gegenlauf heißt | [Bearbeitungen](Bearbeitungen) |
| Fräser und Schnittwerte wählen | [Werkzeuge und Schnittdaten](Werkzeuge-und-Schnittdaten) |
| prüfen, bevor ich fräse | [Prüfen und Simulation](Prüfen-und-Simulation) |
| an der Maschine fräsen | [Fräsen an der Maschine](Fräsen-an-der-Maschine) |
| ein Werkstück von beiden Seiten fräsen, mit Passstiften (nur Simulator) | [Doppelseitig fräsen](Doppelseitig-fraesen) |
| den festen Taster oder die Höhenkarte der Opferplatte nutzen | [Fester Taster und Opferplatte](Fester-Taster-und-Opferplatte) |
| Markierungen (Kreuz, Rahmen, Lineal, Anschlag, Lochraster) in die Opferplatte fräsen | [Opferplatte markieren](Opferplatte-markieren) |
| die Maschine vom Handy aus steuern | [Handy-Fernbedienung](Handy-Fernbedienung) |
| mit einer Kamera Material auf der Arbeitsplatte ausrichten | [Kamera auf der Arbeitsplatte](Kamera-auf-der-Arbeitsplatte) |
| Platten aufteilen, Zinken fräsen, Schränke und Küchen entwerfen | [Platten und Möbel](Platten-und-Möbel) |
| Tische, Sideboards, Regale und Stühle entwerfen (leimlos steckbar) | [Möbel-Designer](Moebel-Designer) |
| ein 3D-Modell (STL, STEP) als Relief, Umriss oder Schichtmodell fräsen | [3D-Modelle importieren](3D-Modelle-importieren) |
| ein Bild der Küche für den Kunden rendern (Licht, Schatten, Glanz, Spüle) | [Küchen-Rendering](Kuechen-Rendering) |
| mit Finger oder Stift bedienen (Tablet, Touch-Laptop) | [Touch und Stift](Touch-und-Stift) |
| ein Rüstblatt und ein Angebot erzeugen, auch mit Stückzahl und Staffel | [Rüstblatt und Angebot](Rüstblatt-und-Angebot) |
| einen anderen G-Code-Dialekt oder eigene Postprozessoren | [Postprozessoren und Steuerungen](Postprozessoren-und-Steuerungen) |
| Claude, MCP, die lokale Schnittstelle oder die Kommandozeile nutzen | [Claude, MCP und API](Claude-MCP-und-API) |
| Designs entdecken, laden und teilen | [Community-Portal](Community-Portal) |
| ein Problem lösen | [Fehlersuche](Fehlersuche) |
| ein Tastenkürzel nachschlagen | [Tastenkürzel](Tastenkürzel) |
| einen Begriff nachschlagen | [Glossar](Glossar) |
| helfen oder einen Test melden | [Mitmachen und Tests](Mitmachen-und-Tests) |

## Das Wichtigste in Kürze

* **Alles in einer Anwendung:** Projekt, Design, Bearbeitung, Prüfen, Fräsen. Fünf Schritte führen vom Entwurf zum Werkstück.
* **Prüft, bevor es fräst:** Prüfliste mit Lösungsvorschlägen und ein Start-Check vor jedem Lauf. Bei Fehlern sind Export und Maschinenstart gesperrt.
* **Für Einsteiger und Erfahrene:** Der Einfach-Modus schlägt Werkzeug, Tiefen und Schnittwerte vor und begründet sie. Der Experten-Modus zeigt alle Einstellungen.
* **Direkt an die Maschine:** GRBL-kompatible Steuerungen (GRBL 1.1, grblHAL, FluidNC) über USB oder Netzwerk. Das Programm **schreibt nie Einstellungen in deine Steuerung**, es liest sie nur.
* **Kostenlos** für private und gewerbliche Nutzung, **Windows 10 und 11 (64 Bit)**. Der Quelltext ist nicht öffentlich.

## Links

* **Download:** [Releases](https://github.com/KlapSC/ortino-cam/releases/latest)
* **Fragen, Fehler, Wünsche, Maschinenberichte:** [GitHub Issues](https://github.com/KlapSC/ortino-cam/issues/new/choose). Issues sind öffentlich, bitte keine persönlichen Daten hineinschreiben. **Datenschutzanfragen und rechtliche Anliegen zum Community-Portal** gehen an die E-Mail-Adresse im [Impressum des Portals](https://benini.access.ly:8088/imprint).
* **Überblick, Vergleich und Fragen:** die [README](https://github.com/KlapSC/ortino-cam#readme) und die [Projektseite](https://klapsc.github.io/ortino-cam/)
* **Community-Portal:** [https://benini.access.ly:8088](https://benini.access.ly:8088)
* **Mitmachen:** [CONTRIBUTING.md](https://github.com/KlapSC/ortino-cam/blob/main/CONTRIBUTING.md)

## English

This wiki is the user guide for **ortino.CAM**, CAD/CAM software for CNC routers on Windows with direct GRBL machine control (version 0.4.2). It is an early version: proven on a real machine so far only for pockets, V-carving, profiles, homing and touch-plate tool changes, while newer features are tested against a simulator only. Always test without tool and material first and keep the emergency stop within reach. The software is provided "as is", without warranty, and you use it at your own risk (see the [disclaimer](https://github.com/KlapSC/ortino-cam#haftungsausschluss)). The pages are in German, and the main project page and the README have English summaries. Questions and bugs go through [GitHub issues](https://github.com/KlapSC/ortino-cam/issues/new/choose) (public, so no personal data); data protection requests and legal matters about the community portal go to the e-mail address in the [portal's imprint](https://benini.access.ly:8088/imprint).
