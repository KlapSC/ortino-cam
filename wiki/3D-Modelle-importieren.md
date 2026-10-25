# 3D-Modelle importieren (STL und STEP)

Ein 3D-Modell aus einem CAD- oder Netzprogramm lässt sich in ortino.CAM auf die Platte bringen, als **3D-Relief**, als **Umriss** oder als **Schichtmodell**. Davor siehst du es im Dialog in 3D, richtest es aus und bekommst eine Prüfliste mit Lösungsvorschlägen.

> **Ehrlich zum Stand:** Das alles wurde **nur gegen Tests, den Simulator und Chromium** geprüft, mit selbst erzeugten Körpern (Quader, Kugel, Kegel, Pyramide, Pilz) und kleinen selbst gebauten Dateien. **Es wurde nie gefräst** und **nie mit einem Modell aus einem echten CAD-Programm** (Fusion, SolidWorks, Blender, FreeCAD …) erprobt. Der **STEP-Import** ist eigener Code und wurde nur mit selbst geschriebenen Beispieldateien im Stil der Exporter geprüft. Ob dein Modell vollständig und maßhaltig ankommt, zeigen der Bericht und die Prüfliste im Dialog. Schau dir das Ergebnis im Schritt »Prüfen« an, bevor du fräst, und beginne mit einem Reststück.

## Öffnen

*Datei ▸ 3D-Modell importieren …*, *Datei ▸ Importieren* (`Strg+I`) mit einer `.stl`, `.step` oder `.stp`-Datei, die Befehlspalette (»3D-Modell importieren«) oder die Datei einfach **ins Fenster ziehen**.

## Im Dialog

Links die 3D-Ansicht (Drehen, Verschieben, Zoomen mit Maus, Finger oder Stift): das Modell, die Platte als Rechteck mit Dicke und ein Rahmen mit den Maßen. Rechts die Einstellungen:

1. **Ausrichtung:** welche Seite oben liegt (Oben, Unten, Vorn, Hinten, Links, Rechts), Drehen um jede Achse, Spiegeln.
2. **Größe:** Einheit der Datei (mm, cm, Zoll, m), Maßstab in Prozent, *Auf Platte einpassen*, *Auf Materialstärke einpassen*. Eine STL-Datei kennt keine Einheit: das Programm **schlägt eine vor** (mit Hinweis), die Wahl bleibt bei dir. STEP-Dateien liefern ihre Einheit mit.
3. **Platzierung:** Lage auf der Platte und beim Relief die Höhe im Material (Oberseite bündig oder das Modell versenkt).
4. **Umwandlung:** drei Karten, siehe unten.
5. **Prüfung:** Liste mit Hinweisen, Warnungen und Fehlern, jeweils mit **Lösung** und, wo möglich, einem Knopf, der sie anwendet (»Auf 62 % verkleinern«, »Um 90° drehen«, »Einheit cm«).

Im **Einfach-Modus** siehst du Seite oben, Einheit und Maßstab, die Karten und die Prüfung; der Rest liegt hinter »Mehr Einstellungen«. *Importieren* (`Strg+Enter`) ist ein einziger Rückgängig-Schritt, *Abbrechen* oder `Esc` lässt das Projekt unberührt. Ohne WebGL zeigt der Dialog eine Meldung statt der Ansicht, Maße, Prüfung und Import funktionieren trotzdem.

## Drei Wege der Umwandlung

* **3D-Relief:** Das Modell wird **von oben** auf ein Raster abgebildet; an jedem Punkt zählt die oberste Fläche. Das Ergebnis ist ein gewöhnliches Relief, Schruppen und Schlichten laufen wie bei jedem Relief (siehe [Bearbeitungen](Bearbeitungen)), auf Wunsch gleich mit angelegt. Gerechnet wird direkt aus dem Netz, nicht über ein 8-Bit-Bild, das für Modelle zu grob wäre. Ist die Tiefe kleiner als das Modell, wird unten abgeschnitten; die Vorgabe ist die Modellhöhe, höchstens **drei Viertel der Plattendicke**, damit ein Boden bleibt.
* **Umriss als Form:** der **Schatten von oben** als geschlossene Kontur mit Löchern, auf Wunsch gleich mit einer Profil-Bearbeitung (außen um die Kontur, Löcher von innen). Bögen bleiben Bögen, wo das Modell welche hat.
* **Schichtmodell:** das Modell wird in **Lagen der Plattenstärke** geschnitten, jede Lage als Profil auf eine eigene Platte oder alle nebeneinander auf eine Platte. Höchstens 200 Lagen. Die Lagen haben **keine Passlöcher**; du musst sie selbst ausrichten und verleimen.

## Die Prüfliste

Sie meldet unter anderem: Einheit nur vermutet, sehr klein oder sehr groß, zu flach, **breiter oder tiefer als die Platte**, **höher als die Materialstärke**, zu wenig Boden, **Hinterschneidungen** (eine Schätzung: Anteil der Oberfläche, den eine Fräse von oben nicht erreicht), **offene Kanten oder Löcher im Netz**, mehrere getrennte Teile, zu grobe Auflösung für den Fräser und Details, die der Kugelfräser nicht ausformt. Ein Netz, das das Programm nicht schließen kann, wird **nicht repariert**: die Liste nennt das Problem, die Lösung liegt in der Netzsoftware.

## STEP

Das Einlesen ist **eigener Code ohne fremde Bibliothek** und versteht die gängigen Austauschformate (AP203, AP214, AP242): Ebenen, Zylinder, Kegel, Kugel, Torus, B-Spline-, Extrusions- und Rotationsflächen, fertige Netze, einfache Baugruppen und die Einheiten. Der Dialog zeigt einen **STEP-Bericht**: wie viele Flächen umgesetzt sind, was nicht unterstützt ist, erkannte Einheit und Programm, Volumen, ob das Netz geschlossen ist. Eine Fläche, die das Programm nicht kennt, entfällt und wird gezählt; das Netz ist dann offen, der Bericht sagt es, und der Dialog schlägt vor, die Datei zusätzlich als STL zu exportieren. **Nur wenn alle Flächen umgesetzt sind und das Netz geschlossen ist, ist das Modell vollständig angekommen.**

Nicht unterstützt sind unter anderem Hyperbel- und Parabelkurven, Körper aus Rechenvorschriften (CSG), reine Drahtmodelle, komprimierte Dateien (`.stpz`) und Dateien über 200 MB. Farben, Schichten, Bemaßungen und Namen werden nicht gelesen. Mehrere Körper (und die Teile einer Baugruppe) werden zu **einem** Netz zusammengefügt, nicht verschmolzen.

## Grenzen

* Nur die **Draufsicht**: Hinterschneidungen werden gemeldet, nicht gefräst. Zwei Seiten zu fräsen ist ein eigener Weg ([Doppelseitig fräsen](Doppelseitig-fraesen)), hier nicht verbunden.
* Maßstab nur gleichmäßig in allen Achsen.
* Das Netz lässt sich **nicht bearbeiten** (Löcher füllen, vereinfachen, reparieren).
* Kein Export nach STL oder STEP.
* **Nicht gemessen:** der Speicherbedarf bei sehr großen Modellen (Höchstgrenze fünf Millionen Dreiecke), Modelle mit sehr vielen kleinen oder sich schneidenden Teilen und echte CAD-Dateien.

## Siehe auch

* [Zeichnen und Importieren](Zeichnen-und-Importieren)
* [Bearbeitungen](Bearbeitungen) (3D-Relief fräsen)
* [Prüfen und Simulation](Prüfen-und-Simulation)
