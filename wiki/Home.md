[English](Home-en) | **Deutsch**

# ortino.CAM Wiki

![ortino.CAM – Vom Entwurf zum Werkstück: CAD/CAM für CNC-Fräsen](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/banner.png)

Willkommen. **ortino.CAM** ist eine **CAD/CAM-Software für CNC-Fräsen** unter Windows: zeichnen, Werkzeugwege berechnen (Profil, Tasche, V-Carving, 3D-Relief), in 3D simulieren, prüfen und direkt an eine **GRBL-Steuerung** wie die der Ultimate Bee (CNC xPRO V5) schicken, alles in einer Anwendung. Mit einem MCP-Server und einer lokalen Schnittstelle lässt sie sich auch von **Claude** und eigenen Skripten steuern.

Dieses Wiki ist für Menschen, die ortino.CAM **benutzen**: Hobby-Fräser, Tischler und Werkstätten. Du musst nichts über den Quelltext wissen. Es beschreibt die veröffentlichte **Version 0.16.0**. Neu seit 0.16.0 sind die Wort- und Logo-Collage im Muster-Studio und im Generator im Browser (damit 40 Arten und 80 Vorlagen im Muster-Studio) und die schlanke Schrift Montserrat. Neu seit 0.15.0 sind die eigenen Vorlagen (Sparte »Eigene« im Muster-Studio und im Relief-Studio, Dialog »Formen«), das Zuschnittverfahren »Optimiert« im Möbel- und Küchen-Designer und der Formen- und Muster-Generator im Browser. Neu seit 0.14.0 sind mehr Muster im Muster-Studio (Stand 0.14.0: 39 Arten, 76 Vorlagen), mehr Relief-Vorlagen (62), 14 Motive im Art Designer, die Dekoration nach Jahreszeit mit 35 Motiven und vier neue Creator (22 in sechs Gruppen). Neu seit 0.13.0 sind der Creator, die Reihenfolge der Zustellungen, der Dialog KI-Modelle und die Startseite mit Schnellzugriffen. Die Seiten und Abschnitte dazu tragen die Hinweise **»seit 0.16.0«**, **»seit 0.15.0«**, **»seit 0.14.0«** bzw. **»seit 0.13.0«**.

## Bitte zuerst lesen

> **Frühe Version (0.x): nicht alles ist an einer echten Maschine erprobt.** Gefräst wurde bisher auf einer Maschine (Ultimate Bee mit xPRO V5, GRBL), alles Übrige lief nur gegen Tests und Simulator. **Teste immer zuerst ohne Werkzeug und Material**, mit dem Not-Aus in Reichweite. Was genau erprobt ist: [Stand der Erprobung](Stand-der-Erprobung).

Die Software entsteht **zum größten Teil mit Claude Code (Anthropic) als Co-Autor**. Anforderungen, Entscheidungen, Abnahme und Veröffentlichung liegen beim Betreiber. Mit Fehlern ist zu rechnen. Deshalb sind Berichte von echten Maschinen so wichtig (siehe [Mitmachen und Tests](Mitmachen-und-Tests)).

**So liest du dieses Wiki:** Wo etwas nur im Simulator, in Tests oder mit erzeugten Bildern geprüft ist, steht das dabei, ebenso wo etwas nicht erprobt ist. Wo nichts steht, ist es dennoch eine frühe Version.

## Wo fange ich an?

| Ich möchte … | Seite |
|---|---|
| das Programm installieren und aktuell halten | [Installation und Updates](Installation-und-Updates) |
| vom leeren Projekt zum ersten Werkstück kommen, mit Beispielgalerie, Einführung und Lektionen | [Erste Schritte](Erste-Schritte) |
| meine Fräse eintragen und die Verfahrwege messen | [Maschine einrichten](Maschine-einrichten) |
| zeichnen (auch mit parametrischen Skizzen), Text setzen (auch als Schablone mit Stegen), SVG/DXF/PDF/EPS oder ein Bild importieren | [Zeichnen und Importieren](Zeichnen-und-Importieren) |
| wissen, was Profil, Tasche, V-Carving und Gewinde tun, was Gleichlauf und Gegenlauf heißt und in welcher Reihenfolge die Zustellungen gefahren werden (seit 0.13.0) | [Bearbeitungen](Bearbeitungen) |
| Fräser und Schnittwerte wählen | [Werkzeuge und Schnittdaten](Werkzeuge-und-Schnittdaten) |
| prüfen, bevor ich fräse | [Prüfen und Simulation](Prüfen-und-Simulation) |
| an der Maschine fräsen | [Fräsen an der Maschine](Fräsen-an-der-Maschine) |
| ein Werkstück von beiden Seiten fräsen, mit Passstiften (nur Simulator) | [Doppelseitig fräsen](Doppelseitig-fraesen) |
| den festen Taster oder die Höhenkarte der Opferplatte nutzen | [Fester Taster und Opferplatte](Fester-Taster-und-Opferplatte) |
| Markierungen (Kreuz, Rahmen, Lineal, Anschlag, Lochraster) in die Opferplatte fräsen | [Opferplatte markieren](Opferplatte-markieren) |
| die Maschine vom Handy aus steuern | [Handy-Fernbedienung](Handy-Fernbedienung) |
| mit einer Kamera Material auf der Arbeitsplatte ausrichten | [Kamera auf der Arbeitsplatte](Kamera-auf-der-Arbeitsplatte) |
| Platten aufteilen (auch als Sägeplan für die Plattensäge), Zinken fräsen, Schränke und Küchen entwerfen | [Platten und Möbel](Platten-und-Möbel) |
| einen Sägeplan für die Plattensäge mit Optimierer rechnen | [Plattenzuschnitt](Plattenzuschnitt) |
| Tische, Sideboards, Regale und Stühle entwerfen (leimlos steckbar); den Zuschnitt »Optimiert« rechnen lassen (seit 0.15.0) | [Möbel-Designer](Moebel-Designer) |
| Küche und Möbel im Browser entwerfen, teilen und abwechselnd bearbeiten (Portal) | [Web-Designer im Portal](Web-Designer-im-Portal) |
| aus einem Foto ein Relief machen (KI-Tiefenschätzung auf deinem Rechner) | [Foto → Relief](Foto-zu-Relief) |
| das KI-Tiefenmodell laden, prüfen oder entfernen; die Startseite mit Schnellzugriffen nutzen (seit 0.13.0) | [KI-Modelle und Startseite](KI-Modelle-und-Startseite) |
| ein Wandbild aus Holz entwerfen (geschnitzt oder Schichtholz; 14 Motive, sechs davon seit 0.14.0) | [Art Designer](Art-Designer) |
| ein gelochtes Paneel aus Mustern entwerfen (40 Arten, 80 Vorlagen, mit Suchfeld; erweitert in 0.14.0, Wort- und Logo-Collage seit 0.16.0) | [Zeichnen und Importieren](Zeichnen-und-Importieren) |
| ein 3D-Relief aus Vorlagen erzeugen (62 Vorlagen in 9 Kategorien; erweitert in 0.14.0) und daraus Werkzeugwege machen | [Bearbeitungen](Bearbeitungen) |
| eigene Muster, Reliefs und Formen speichern, als Datei sichern und importieren; zehn Grundformen auf die Platte setzen (seit 0.15.0) | [Eigene Vorlagen](Eigene-Vorlagen) |
| Muster und Formen im Browser erzeugen und als SVG oder DXF herunterladen, ohne Konto (seit 0.15.0, Wort- und Logo-Collage seit 0.16.0; kein G-Code) | [Formen- und Muster-Generator](Formen-und-Muster-Generator) |
| ein Werkstück aus wenigen Eingaben erzeugen: Schachtel, Vogelhaus, Zahnräder, Puzzle, Türschild, Adventskalender, Windlicht und mehr (22 Creator; seit 0.13.0, erweitert in 0.14.0) | [Creator](Creator) |
| ein 3D-Modell (STL, STEP) als Relief, Umriss oder Schichtmodell fräsen; Teile als STL oder 3MF exportieren | [3D-Modelle importieren](3D-Modelle-importieren) |
| 3D-Körper als STL oder 3MF exportieren (Modelle, Möbelteile, Reliefplatten) | [3D-Körper exportieren](Export-STL-3MF) |
| ein Relief aus Komponenten zusammensetzen oder mit dem Pinsel nachmodellieren | [Modellieren von Reliefs](Modellieren-von-Reliefs) |
| ein Teil fräsen, das größer ist als der Verfahrweg (Kachelung) | [Große Teile kacheln](Grosse-Teile-kacheln) |
| ein Bild der Küche für den Kunden rendern (Licht, Schatten, Glanz, Spüle) | [Küchen-Rendering](Kuechen-Rendering) |
| mit Finger oder Stift bedienen (Tablet, Touch-Laptop) | [Touch und Stift](Touch-und-Stift) |
| mit mehreren Leuten arbeiten: Werkstatt-Ordner, Rollen, gemeinsame Bibliothek, Dashboard (lokal) | [Werkstatt und Team](Werkstatt-und-Team) |
| ein Rüstblatt und ein Angebot erzeugen, auch mit Stückzahl und Staffel, Kundenstamm, Angebotsnummer und Zahlungsbedingungen | [Rüstblatt und Angebot](Rüstblatt-und-Angebot) |
| Kunden verwalten, Angebotsnummern vergeben, Zahlungsbedingungen einsetzen | [Kunden und Angebote](Kunden-und-Angebote) |
| einen anderen G-Code-Dialekt oder eigene Postprozessoren | [Postprozessoren und Steuerungen](Postprozessoren-und-Steuerungen) |
| Claude, MCP, die lokale Schnittstelle oder die Kommandozeile nutzen | [Claude, MCP und API](Claude-MCP-und-API) |
| Designs entdecken, laden und teilen | [Community-Portal](Community-Portal) |
| Maschinenprofile, Fräser und Einstellungen privat im Portal sichern | [Sicherung im Portal](Sicherung-im-Portal) |
| kurze Anleitungsvideos ansehen (5–20 Sekunden, englisch beschriftet) | [Videos](Videos) |
| ein Problem lösen | [Fehlersuche](Fehlersuche) |
| ein Tastenkürzel nachschlagen | [Tastenkürzel](Tastenkürzel) |
| einen Begriff nachschlagen | [Glossar](Glossar) |
| wissen, was an einer echten Maschine erprobt ist und was nicht | [Stand der Erprobung](Stand-der-Erprobung) |
| helfen oder einen Test melden | [Mitmachen und Tests](Mitmachen-und-Tests) |

## Das Wichtigste in Kürze

* **Alles in einer Anwendung:** Projekt, Design, Bearbeitung, Prüfen, Fräsen. Fünf Schritte führen vom Entwurf zum Werkstück.
* **Prüft, bevor es fräst:** Prüfliste mit Lösungsvorschlägen und ein Start-Check vor jedem Lauf. Bei Fehlern sind Export und Maschinenstart gesperrt.
* **Für Einsteiger und Erfahrene:** Der Einfach-Modus schlägt Werkzeug, Tiefen und Schnittwerte vor und begründet sie. Der Experten-Modus zeigt alle Einstellungen.
* **Direkt an die Maschine:** GRBL-kompatible Steuerungen (GRBL 1.1, grblHAL, FluidNC) über USB oder Netzwerk. Das Programm **schreibt nie Einstellungen in deine Steuerung**, es liest sie nur.
* **Neu in 0.16.0:** die **Wort- und Logo-Collage** (bis zu vier Wörter oder Logos, dicht gemischt) im Muster-Studio und im [Formen- und Muster-Generator](Formen-und-Muster-Generator) im Browser, dazu die schlanke Schrift Montserrat (siehe [Zeichnen und Importieren](Zeichnen-und-Importieren#wort--und-logo-collage-seit-0160)). Das Muster-Studio hat damit 40 Arten und 80 Vorlagen. Wie weit das alles erprobt ist, steht unter [Stand der Erprobung](Stand-der-Erprobung).
* **Neu in 0.15.0:** [eigene Vorlagen](Eigene-Vorlagen) (Sparte »Eigene« im Muster-Studio und im Relief-Studio, Dialog »Formen« mit zehn Grundformen), das Zuschnittverfahren »Optimiert« im [Möbel-Designer](Moebel-Designer#zuschnitt-optimiert-und-sägeplan-seit-0150) und der [Formen- und Muster-Generator](Formen-und-Muster-Generator) im Browser (SVG und DXF, kein G-Code). Nichts davon wurde gefräst oder gesägt; die eigenen Vorlagen sind nicht unter Windows (WebView2) geprüft.
* **Neu in 0.14.0:** mehr Muster (Stand 0.14.0: 39 Arten und 76 Vorlagen im Muster-Studio, siehe [Zeichnen und Importieren](Zeichnen-und-Importieren)), 62 Relief-Vorlagen (siehe [Bearbeitungen](Bearbeitungen)), 14 Motive im [Art Designer](Art-Designer) und im [Creator](Creator) die Dekoration nach Jahreszeit mit 35 Motiven und vier neue Creator (Adventskalender, Kranz und Bordüre, Windlicht / Laterne, Girlande). Nichts davon wurde gefräst oder verleimt.
* **Neu in 0.13.0:** ein [Creator](Creator) mit 18 Werkstück-Generatoren (Stand 0.13.0), die Wahl der [Reihenfolge der Zustellungen](Bearbeitungen), der Dialog [KI-Modelle](KI-Modelle-und-Startseite) und eine Startseite mit Schnellzugriffen. Nichts davon wurde gefräst.
* **Kostenlos** für private und gewerbliche Nutzung, **Windows 10 und 11 (64 Bit)**. Der Quelltext ist nicht öffentlich.

## Links

* **Download:** [Releases](https://github.com/KlapSC/ortino-cam/releases/latest)
* **Fragen, Fehler, Wünsche, Maschinenberichte:** [GitHub Issues](https://github.com/KlapSC/ortino-cam/issues/new/choose). Issues sind öffentlich, bitte keine persönlichen Daten hineinschreiben. **Datenschutzanfragen und rechtliche Anliegen zum Community-Portal** gehen an die E-Mail-Adresse im [Impressum des Portals](https://ortino-cam.com/imprint).
* **Überblick, Vergleich und Fragen:** die [README](https://github.com/KlapSC/ortino-cam#readme) und die [Projektseite](https://klapsc.github.io/ortino-cam/)
* **Community-Portal:** [https://ortino-cam.com](https://ortino-cam.com)
* **Mitmachen:** [CONTRIBUTING.md](https://github.com/KlapSC/ortino-cam/blob/main/CONTRIBUTING.md)
