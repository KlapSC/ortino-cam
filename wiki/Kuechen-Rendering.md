# Küchen-Rendering

Der Möbel- und Küchen-Designer ([Platten und Möbel](Platten-und-Möbel)) kann ein **Bild der Küche** speichern, mit Licht, weichen Schatten, Glanz lackierter Fronten, eingebauter Spüle samt Armatur, Boden, Wänden und Spritzschutz. Gedacht ist es für das Gespräch mit dem Kunden: »So könnte Ihre Küche aussehen.«

> **Ehrlich zum Stand:** Das ist ein **schnelles WebGL-Bild**, **kein fotorealistischer Render**: keine echte globale Beleuchtung (kein Streulicht von Wand zu Wand), keine Lichtbrechung, keine Spiegelung der Küche im Boden. **Farben auf dem Bildschirm sind keine Farbmuster.** Kunden sollten ein Muster des echten Lacks sehen. Das Rendering wurde **nur in Chromium mit Software-Grafik geprüft**, nie unter Windows (WebView2) und nie auf einer echten Grafikkarte; wie lange »Standard« und »Hoch« bei 4K dauern, ist nicht gemessen.

## Öffnen

Im Möbel-Designer: der **Kamera-Knopf** in der Kopfleiste, die Taste `R` oder die Befehlspalette (`Strg+K`, »Rendering exportieren …«). Ohne Schränke gibt es nichts zu rendern. Der Dialog zeigt links eine grobe, drehbare Vorschau (Ziehen dreht, Mausrad zoomt) und rechts die Einstellungen; **Rendern und speichern** rechnet das Bild in Endqualität.

## Einstellungen

* **Größe:** Full HD, 4K, Quadrat oder frei. Große Bilder werden in Kacheln gerechnet; ab etwa 20 Megapixeln warnt der Dialog vor Dauer und Speicher.
* **Ansicht:** Frontal, Schräg, Raumecke, die aktuelle 3D-Ansicht oder eine eigene Ansicht; Brennweite 14 bis 135 mm; Türen auf Wunsch geöffnet.
* **Qualität:** Entwurf, Standard oder Hoch (mehr Durchgänge: weichere Schatten, mehr Glanz, längere Rechenzeit).
* **Licht:** Tageslicht, Abend (warm) oder Studio (neutral); dazu schaltbare **LED-Streifen** unter den Hängeschränken.
* **Raum:** Boden (vier Varianten), Wandfarbe, Wände hinten/links/beide, optional Spritzschutz (Fliese, Glas dunkel, Glas hell, Edelstahl).
* **Spüle:** Sie kommt aus dem **Ausschnitt der Arbeitsplatte** (Küche → Arbeitsplatte): Edelstahl mit ein oder zwei Becken, Abtropffläche und Armatur. Ohne Ausschnitt gibt es keine Spüle; ein Kochfeld-Ausschnitt ergibt ein Kochfeld.
* **Farben und Glanz:** Die Oberflächen der Fronten, des Korpus und der Arbeitsplatte (siehe [Platten und Möbel](Platten-und-Möbel)) werden übernommen: Klarlack-Glanz je nach Glanzgrad, Metall bei Griffen, dunkle Fronten mit sichtbaren Reflexen.
* **Ausgabe:** PNG oder JPEG, Dateiname, auf Wunsch die Zeile »Darstellung · Maße und Farben unverbindlich« unten im Bild.

## Hinweise

* Während des Renderns zeigt der Dialog das entstehende Bild und einen Fortschrittsbalken. **Esc** bricht ab (dann wird nichts gespeichert).
* Gespeichert wird als **Download**; den Zielordner bestimmt Windows bzw. der Browser (meist »Downloads«).
* Die Probebilder in den Tests wirken noch schlicht: Die Spüle überzeugt vor allem in der Nahaufnahme, die LED-Streifen geben einen weichen warmen Schleier statt eines Lichtkegels, und bei Hochglanz erscheint eine Lampe als runder heller Fleck auf einer Front.
* Reliefs auf Fronten erscheinen im Bild als sanfte Schattierung (die Front bleibt eben).

## Weiter

* [Platten und Möbel](Platten-und-Möbel)
* [Tastenkürzel](Tastenkürzel)
* [Fehlersuche](Fehlersuche)
