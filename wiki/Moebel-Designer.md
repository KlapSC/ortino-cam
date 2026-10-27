# Möbel-Designer (Tische, Sideboards, Regale, Sitzmöbel)

Neben der Küche entwirfst du im selben Dialog **Möbel**: Tische, Sideboards, Regale und Sitzmöbel. Werkstoffe, Kantenband, Farben, Griffe, Reliefs, Stückliste, Zuschnitt, Rüstblatt und Angebot, »Teile erzeugen & fräsen vorbereiten« und Rückgängig gelten wie bei der Küche (siehe [Platten und Möbel](Platten-und-Möbel)).

> **Ehrlich zum Stand:** Alles hier sind **Rechnungen und übliche Werkstattmaße**, geprüft nur gegen Tests, Simulator und Chromium. **Nichts davon wurde gefräst, gebaut oder belastet.** Die Prüfungen (Kippen, Durchbiegung, Stege, Innenradien) sind **Hinweise aus einfachen Formeln, kein Festigkeitsnachweis**; Werkstoffkennwerte, Lasten, Prüflasten, Steckspiel und Gewichte sind **Annahmen**, die in jeder Meldung stehen. **Vor jeder Serie ein Probeteil aus dem echten Material bauen und mit der vorgesehenen Last prüfen.** Bei Stuhl, Hocker und Bank ist das Voraussetzung.

> **Auch im Browser:** Seit 0.5.0 gibt es diesen Designer auch im Community-Portal (ohne Programm, ohne Fräsen): [Web-Designer im Portal](Web-Designer-im-Portal).

## Öffnen

Im Möbel-Designer (`Strg+Umschalt+M`) oben den Umschalter **Küche | Möbel**, oder in der Befehlspalette (`Strg+K`) »Möbel-Designer: Bereich Möbel öffnen«, »Möbel: Essgruppe anlegen« oder »Möbel hinzufügen: …«. Küchenschränke und Möbelstücke können im selben Projekt stehen; jeder Bereich zeigt nur seine Stücke, Stückliste, Zuschnitt und »Teile erzeugen« enthalten beide.

Links die Liste, nach Tischen, Sideboards, Regalen und Sitzmöbeln gruppiert, mit *Hinzufügen*; ein Punkt am Eintrag zeigt eine Warnung oder einen Fehler. In der Mitte die 3D-Vorschau und darunter der **Grundriss**, rechts die Felder des gewählten Stücks. Alle Längen nehmen Zahl oder Formel mit Projektvariablen. Im **Einfach-Modus** liegen die Feinheiten der Konstruktion hinter *Weitere Maße*.

## Möbelarten

Standardmaß Breite × Höhe × Tiefe in mm.

| Art | Standard | Wahlen |
|---|---|---|
| **Esstisch** | 1800 × 740 × 900 | Platte rechteckig, Soft-Rechteck, Stadion, oval, rund; Kante gerade, Fase (90°-Fräser) oder Radius (nur Handarbeit); Fuß Zarge mit vier Beinen, Plattenfüße, Kreuzfuß, A-Gestell; Platte in 2–3 Teile geteilt |
| **Couchtisch** | 900 × 380 × 600 | wie der Esstisch |
| **Beistelltisch** | 450 × 550 × 450 | wie der Esstisch |
| **Satztische** | 700 × 500 × 460 | 2–3 Tische, die ineinander passen, mit Abstandsprüfung |
| **Sideboard / Lowboard / TV-Board** | 1800 × 650 × 420 | Sockel, Beine oder Schlittenfuß; Türen, Schubladen, Klappen, offene Fächer; gemeinsame Mittelwände, genutete Rückwand, Kabeldurchlass |
| **Bücherregal** | 800 × 1800 × 320 | Böden im System 32, fest in Nuten oder gesteckt; Lastannahme je Meter Brett |
| **Leiterregal** | 700 × 1800 × 450 | zwei schräge Holme, gesteckte Böden, lehnt an der Wand |
| **Modulregal** | 1200 × 1200 × 340 | Raster aus Spalten und Reihen |
| **Wandregal** | 800 × 240 × 230 | Kasten oder Brett; Wandbefestigung als Zukaufteil mit Hinweis |
| **Hocker**, **Plattenhocker** | 360 × 450 × 360, 380 × 450 × 320 | Sitz auf Zarge, Plattenfüßen oder Kreuzfuß bzw. auf zwei Seitenplatten |
| **Sitzbank** | 1400 × 450 × 380 | Platte auf Plattenfüßen, Zarge, Kreuzfuß oder A-Gestell |
| **Sperrholzstuhl** | 440 × 840 × 520 | zwei profilierte Seitenplatten, schräger Sitz und Lehne, Querstrebe |
| **Kommode**, **Highboard** | (seit 0.4.1) | Schubladenkorpus mit Schubkästen auf Vollauszug (13 mm Seitenluft), Sockel, Beinen oder Kufe, Rückwand; Fächer nach der Breite vorgeschlagen |
| **Nachttisch** | (seit 0.4.1) | Fach mit Schublade, auch Schublade über offenem Fach; Höhe zur Matratze als Richtwert |
| **Schreibtisch** | (seit 0.4.1) | Wangen mit Knieblende, Zarge, Plattenfüße oder Kufe; optional Schubladencontainer links oder rechts und Kabeldurchlass (rund oder Schlitz) |
| **Garderobe** | (seit 0.4.1) | Wandpaneel mit Hakenleiste und Ablage auf gesteckten Konsolen; Haken und Wandbefestigung stehen in der Stückliste |
| **Schuhbank / Schuhschrank** | (seit 0.4.1) | bis 480 mm Höhe eine Bank mit offenen Fächern, darüber ein Schrank |

Einen **Loungesessel** gibt es bewusst nicht, ebenso keine Polster, Armlehnen, Drehstühle oder Betten.

## Verbindungen

* **Leimlos steckbar:** Zapfen durch Schlitze. Das Spiel kommt aus dem Passungs-Assistenten (Projektvariable `Spiel`), sonst nimmt das Programm 0,15 mm an. Die Schlitzecken bekommen **Hundeknochen** passend zum Fräser. **Zapfen und Schlitz entstehen aus einer Beschreibung** und passen daher rechnerisch immer zusammen.
* **Klassisch:** Zapfen in Sacktaschen (verleimt), Dübel oder Konfirmatschrauben (als Zukaufteil in der Stückliste).
* Beim **Sideboard** ist nur der Fuß leimlos steckbar; der Korpus bleibt bei den Verbindern des Küchen-Baukastens.
* **Fingerzinken** (seit 0.4.1) sitzen an den Außenecken des Korpus und an den Schubkastenecken, nur in Multiplex und Massivholz; bei beschichteter Platte, Span oder OSB bleibt die klassische Verbindung mit Warnung. Nicht angeschlossen sind Schwalbenschwanz und Gehrung, und Zinken nur an den Außenecken, nicht an inneren Verbindungen.

## Stilvorlagen

Sechs Vorlagen setzen Werkstoff, Stärken, Farbe, Glanz, Griff, Formen und Verbindung in einem Schritt, danach ist alles frei änderbar: **Soft Modern**, **Japandi**, **Lamelle**, **Skulptural**, **Warm Minimal** und **Dunkel**. Es sind allgemeine Namen ohne Hersteller und ohne Nachbau geschützter Möbel, und es sind **Einschätzungen aktueller Richtungen, keine Marktdaten**. In den lackierten Vorlagen nehmen Tische, Sitze und Regale Multiplex statt MDF, weil MDF unter Dauerlast nachgibt.

## Essgruppe und Aufstellung

*Essgruppe anlegen* fragt Personenzahl (2–10), Tischform, Stil und auf Wunsch Stühle an den Kopfenden und ein Sideboard; Tischgröße und Stuhlplätze (60 cm je Platz) rechnet das Programm, und alles entsteht in **einem** Rückgängig-Schritt.

Im Grundriss lassen sich Stücke **ziehen** (Raster 10 mm, mit `Umschalt` 100 mm) oder über die Felder *x*, *z* und *Drehung* setzen. Das ist **kein Raumplaner**: keine Wände, Türen, Fenster oder Steckdosen. Es gibt nur eine Warnung, wenn sich Stücke im Grundriss überschneiden (ein Stuhl, der unter die Tischplatte passt, ist nur ein Hinweis).

## Prüfungen

Jede Meldung nennt Annahme, Rechnung und einen **Lösungsvorschlag**:

* **Ergonomie:** übliche Bereiche für Tischhöhe, Sitzhöhe und -tiefe, Beinfreiheit, Plätze je Person.
* **Kippen:** Last am Plattenrand (Tische mit 15 oder 40 kg, Sitze mit 80 kg angenommen), Stuhl nach hinten, Regale und Wand (mit Hinweis auf die Wandbefestigung).
* **Durchbiegung:** Balkenformel, Hinweis ab L/300, Warnung ab L/200, mit Lastannahmen für Regalbretter (Standard 40 kg je Meter), Tischplatte und Sitz.
* **Stege und Fräser:** Stegbreite, Schlitzbreite und Innenradien gegen den Fräser der Maschine.
* **Verfahrweg:** passt ein Teil nicht in den Verfahrweg, nennt die Liste Lösungen (teilen, Maßstab, andere Platte oder Maschine, mehrere Aufspannungen).
* **Probeteil:** bei Stuhl, Hocker, Plattenhocker und Bank immer.
* **Neu in 0.4.1:** **Kippsicherung** bei Kommode und Highboard (Wandbefestigung als Pflicht-Hinweis) und **Kippen mit ausgezogener Schublade**; Schubladen (Auszug, Last, Breite, Anschlag, Boden); Schreibtisch (Höhe, Tiefe, Beinfreiheit, Kabeldurchlass); Nachttisch gegen die Matratzenhöhe; Garderobe (Last je Wandschraube, Hakenabstand); Schuhbank als Sitz; **Verwindung** bei fehlender Rückwand; Zinken (Fräser, Breite, Werkstoff). Die Lasten (zum Beispiel 30 kg je Auszugspaar, 20 kg Zusatzlast beim Kippen) sind **Annahmen**, die Verwindung ist eine Erfahrungsregel.

Die Rechnungen nehmen einen frei aufliegenden Balken und starre Verbindungen an; Verbindungen, Beschläge, Leimfugen und die Lastabtragung in den Beinen werden **nicht nachgewiesen**. Gewichte sind grob (Volumen mal Rohdichte, ohne Beschläge und Leim).

## Rendering

*Rendering* im Bereich Möbel zeigt eine **Möbelszene** mit Boden (Parkett), Wand hinter dem hintersten Wandmöbel, Seitenwänden, wählbarem Teppich und Holzmaserung entlang der Faser. Wie beim [Küchen-Rendering](Kuechen-Rendering): ein schnelles WebGL-Bild, **kein fotorealistischer Render**, nur in Chromium mit Software-Grafik geprüft, Bildschirmfarben sind keine Farbmuster.

## Tastatur

`↑`/`↓` wählt das nächste Stück, `N` legt ein neues Stück der gewählten Art an, `Entf` löscht, `K` zeigt den Überblick, `R` öffnet das Rendering, `Strg+Z`/`Strg+Y` nehmen zurück bzw. wiederholen. Verschoben wird per Ziehen (Maus, Finger, Stift) oder über die Felder, nicht mit Pfeiltasten.

## Grenzen

* Radius- und Fasenkante sind in 3D nicht zu sehen; der Radius ist Handarbeit.
* Kein Raumplaner, keine Prüfung gegen die Küche, kein automatisches Anordnen.
* Das Rendering lief nie unter Windows (WebView2) oder auf einer echten Grafikkarte.

## Siehe auch

* [Platten und Möbel](Platten-und-Möbel) (Küche, Plattenplaner, Passungen)
* [Küchen-Rendering](Kuechen-Rendering)
* [Rüstblatt und Angebot](Rüstblatt-und-Angebot)
