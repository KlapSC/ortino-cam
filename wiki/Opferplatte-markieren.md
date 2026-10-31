# Opferplatte markieren

Ein Assistent fräst **Markierungen in die Opferplatte** der Maschine: Nullpunkt-Kreuz und Rahmen, ein Lineal mit Zahlen, Anschlag-Linien und ein Lochraster. Damit legst du Werkstücke nach Augenmaß genau und setzt Spannmittel. Die Markierungen erscheinen danach auch in der Tisch-Ansicht der Karte im Schritt »Fräsen«.

> **Ehrlich zum Stand:** Das alles wurde **nur gegen Tests, den eingebauten Maschinensimulator und Chromium** geprüft. **Nichts davon wurde an einer echten Maschine gefräst.** Wie genau die Rillen sitzen, hängt von der Wiederholgenauigkeit der Referenzschalter, dem Rundlauf des Fräsers und dem Zustand der Opferplatte ab und ist nicht erprobt. Beim ersten Mal **flach gravieren**, vorher »Rahmen fahren« und die Lage am Tisch ansehen. Beispielwerte (zum Beispiel 8 mm für Löcher) sind Beispiele, keine Herstellerangaben.

> **Dieser Auftrag fräst in die Opferplatte deiner Maschine.** Sie darf danach nicht verschoben werden, und nach dem Planfräsen sind die Markierungen weg.

## Öffnen

*Erstellen ▸ Opferplatte markieren …*, die Befehlspalette (`Strg+K`, »Opferplatte markieren«) oder der Abschnitt »Markierungen« in der Karte »Opferplatte« im Schritt »Fräsen«. Vorher möglichst verbinden und die Einstellungen lesen lassen (das passiert beim Verbinden von selbst).

## Die vier Arten

Jede Art ist einzeln wählbar und hat ihre eigenen Werte und Tiefen.

| Art | Was |
|---|---|
| **Nullpunkt-Kreuz und Rahmen** | Kreuz an der Referenzecke (oder Mitte, oder einer anderen Ecke), Rahmen um den nutzbaren Bereich, ganze Linie oder nur Eckmarken |
| **Lineal mit Skala** | Teilstriche an den Kanten der Referenzecke (wahlweise an allen vier), Zahlen in Einzellinienschrift, wahlweise durchgehende Rasterlinien; Teilung 10/50/100 mm einstellbar |
| **Anschlag-Linien** | Eckwinkel (L mit zwei Schenkeln) oder Anschlagkanten an einer Ecke, zum Anlegen eines Werkstücks oder zum Anschrauben einer Leiste |
| **Lochraster** | Bohrungen im Raster für Spannmittel oder Passstifte (Teilung, Randabstand, Durchmesser; Anzahl und Vorschau stehen im Assistenten) |

## Tiefen frei einstellbar

* **Gravurtiefe:** ein Wert für alle Linien und Zahlen (Vorgabe flach, 0,3 mm). Unter »Mehr Einstellungen« hat jede Art ihre eigene Tiefe; die Rasterlinien bleiben flacher.
* **Lochtiefe:** **»Nur anbohren«** (Vorgabe, 2 mm: die Stelle markieren und später von Hand mit dem passenden Bohrer bohren), **»Tief bohren«** (so tief wie erlaubt), **»Wie Passstifte«** (Durchmesser und Tiefe der Passstifte aus dem doppelseitigen Fräsen) oder **»Selbst wählen«**.

## Schutz vor dem Durchfräsen

Das Programm kannte die Dicke deiner Opferplatte bisher nicht. Der Assistent **fragt sie ab** (Vorgabe 18 mm, **bitte nachmessen**) und prüft **jede** Tiefe dagegen: Unter der tiefsten Stelle bleibt mindestens ein **Mindestrest** stehen (Vorgabe 3 mm, einstellbar, nie unter 1 mm). Sonst ist es ein **Fehler mit Lösungsvorschlag**, und »Platte anlegen« bleibt gesperrt. Dieselbe Grenze prüfen danach die Prüfliste und der **Start-Check** (er sperrt den Start).

## Wiederfindbar: bezogen auf die Maschine

Die Markierungen müssen sich später wiederfinden lassen. Deshalb beziehen sie sich auf die **Referenzposition** der Maschine (nach der Referenzfahrt), nicht auf einen frei gesetzten Nullpunkt. Der Assistent legt eine Platte an, deren XY-Nullpunkt in der Referenzecke liegt; der Start-Check **verlangt, dass XY-Null auf der Referenzposition liegt**, und prüft es. Nach der Referenzfahrt genügt »XY hier nullen«. Ohne bekannte Referenzrichtung (`$23`) oder Referenzecke im Maschinenprofil plant der Assistent nicht, er rät nicht.

**Z-Null ist die Oberfläche der Opferplatte:** auf der Opferplatte antasten (Tastplatte) oder von Hand setzen. Mit festem Taster bietet der Start-Check für diesen Auftrag den Werkzeugwechsel »Pause« an; Z für jeden Fräser (erst Gravur, dann Bohrer) auf der Opferplatte neu antasten.

## Ablauf

1. **Markierungen** wählen, Dicke der Opferplatte, Gravurtiefe, Lochtiefe eintragen. Im Einfach-Modus steht nur das vorn, der Rest hinter »Mehr Einstellungen«. Rechts zeigt die Vorschau den Tischplan mit Verfahrweg, nutzbarem Bereich, Referenzecke und den geplanten Markierungen.
2. **Prüfen:** Referenzecke, Fräser (Vorschlag oder eigene Wahl; V-Fräser oder Gravierstichel für Linien, Bohrer oder Schaftfräser für Löcher) und die Prüfliste mit Lösungen.
3. **Platte anlegen:** eine normale Platte »Opferplatte markieren« mit gesperrten Ebenen und Bearbeitungen, Gravur zuerst, Bohrung zuletzt, in **einem Rückgängig-Schritt**.
4. Wie gewohnt **Prüfen ▸ Fräsen**. Der Start-Check verlangt die Bestätigung »Fräst in die Opferplatte der Maschine«.
5. Danach in der Karte »Opferplatte« **»Markierungen sind gefräst«** bestätigen. Das Programm kann nicht wissen, ob wirklich gefräst wurde; bis du bestätigst, stehen die Markierungen als **»geplant«** (gestrichelt, blass) in der Tisch-Ansicht, danach als **»gefräst«** (kräftig). Mit »zurück auf geplant« und »vergessen« nimmst du es zurück.

Hat das Projekt die Platte schon, öffnet der Assistent mit ihren Werten; **»Neu erzeugen«** ersetzt die Markierungs-Bearbeitungen, eigene Formen auf der Platte bleiben.

## Grenzen

* Pro Maschine gibt es **eine** Beschreibung der Markierungen (sie gehört zu »Meine Maschine« und geht nicht ins geteilte Paket).
* Die Zahlen des Lineals zählen ab der Rahmenecke in der Referenzecke, nicht ab XY-Null.
* Über der Markierungs-Platte verdecken die Werkzeugwege des Auftrags die Linien weitgehend, die Löcher bleiben sichtbar.
* Das Raster »Wie Passstifte« ist nur ein Hilfsraster: der Assistent »Doppelseitig fräsen« bohrt seine Passlöcher weiterhin je Werkstück selbst.
* Nicht erprobt: Wiederholgenauigkeit der Referenzschalter, Lage und Lesbarkeit der Rillen in MDF, Windows (WebView2).

## Siehe auch

* [Fester Taster und Opferplatte](Fester-Taster-und-Opferplatte)
* [Fräsen an der Maschine](Fräsen-an-der-Maschine)
* [Doppelseitig fräsen](Doppelseitig-fraesen)

<!-- videos:start -->
## Videos (English)

* [![Plan marks for the spoilboard (video, English captions)](https://klapsc.github.io/ortino-cam/videos/spoilboard-marks-poster.jpg)](https://klapsc.github.io/ortino-cam/videos/#spoilboard-marks)  
**Plan marks for the spoilboard** · 14 s

Alle Videos: [Videos](Videos).
<!-- videos:end -->
