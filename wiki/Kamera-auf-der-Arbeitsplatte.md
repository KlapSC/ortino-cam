# Kamera auf der Arbeitsplatte

Eine USB-Kamera über der Maschine liefert ein Bild der Arbeitsfläche. **Vier QR-Marken** in den Ecken verankern es in Millimetern. Das Programm berechnet Perspektive und Maßstab, **entzerrt** das Bild und legt es **unter deinen Entwurf**. So positionierst du Teile auf dem echten Material (Reststück, krummes Brett, bedruckte Platte). Außerdem kann das Programm den **Umriss eines Werkstücks** erkennen und als Form oder Reststück übernehmen.

> **Ehrlich zum Stand:** Die Kamera-Funktion ist **nie mit einer echten Kamera erprobt**. Geprüft wurde mit gerechneten Bildern (eine erzeugte Szene mit bekannter Perspektive) und einer Testkamera, die ein Browser vortäuscht (keine echte Hardware). Verhalten echter Kameras und Treiber, Objektivverzerrung, Autofokus, Belichtungsregelung, Spiegelungen im Werkstück und die **Windows-Kameraberechtigung** sind **unerprobt**. Der Dialog sagt das auch. Prüfe die Genauigkeit vor dem Fräsen an einem Probestück.

## Wie genau ist das?

An erzeugten Bildern liegt der Fehler unter idealen Bedingungen unter 0,02 mm. Das ist die **obere Schranke des Verfahrens, nicht die Genauigkeit einer echten Kamera**: Die Testbilder entstehen mit demselben Modell, das die Rechnung anpasst. Bei einer echten Kamera bestimmen Objektivverzerrung, Fokus, Belichtung, Druckgenauigkeit und Ebenheit der Marken das Ergebnis. **Rechne mit 0,5 bis 1,5 mm**, bis du es an deiner Kamera nachgemessen hast (Kontrollwert, Kontrollraster, Probestück).

## Einrichten in fünf Schritten

Den Dialog öffnest du über den Knopf in der Werkzeugpalette links im Zeichenbereich (Schritt »Design«), über das Symbol in der Kopfleiste oder die Befehlspalette (`Strg+K`, »Kamera über der Arbeitsfläche«). Er hat vier Register: **Kamera**, **Kalibrieren**, **Hintergrund**, **Umriss**.

1. **Kamera starten.** Register »Kamera«: Kamera wählen und »Kamera starten«. Die Kamera startet nur auf Knopfdruck und wird beim Schließen des Dialogs freigegeben. Ohne Kamera nimmst du **»Bild aus Datei …«** (PNG, JPEG oder WebP), zum Beispiel ein Foto vom Handy.
2. **Blatt mit Marken drucken.** Register »Kalibrieren«: Das Programm erzeugt ein Blatt (A4, als PDF oder SVG) mit den vier Marken. Seitenlänge 30 bis 100 mm, Standard 50 mm. Drucke mit **100 %**, nicht mit »An Seite anpassen«. Unten steht ein 100-mm-Maßstab zum Nachmessen.
3. **Marken in die Ecken legen.** Schneide die Marken aus und lege die **Außenkante des Codes** an die Ecke der Arbeitsfläche. Sie müssen flach und matt liegen, auf **Höhe der Materialoberfläche** (siehe Parallaxe unten). Eine Marke darf gedreht liegen. Liegen sie woanders, trägst du unter »Mehr Einstellungen« die Mittelpunkte ein.
4. **Aufnehmen und prüfen.** Das Ergebnis zeigt die Güte, den **mittleren und größten Fehler in Millimetern**, einen **Kontrollwert** und Hinweise (Druckgröße falsch, Marken zu klein, Marke am Rand …). Die erkannten Marken (grün) und ihre Sollposition (orange) liegen über dem Bild.
5. **Kalibrierung speichern.** Gespeichert wird nur die Abbildung (neun Zahlen) im Maschinenprofil, **nie ein Bild**.

Die Marken sind nummeriert: **1 vorne links, 2 vorne rechts, 3 hinten rechts, 4 hinten links** (Blick von oben, X nach rechts, Y nach hinten). Mit drei brauchbaren Marken geht es mit Warnung, vier sind besser. Das Programm **rät nicht**: Ist die Zuordnung nicht eindeutig, bekommst du eine Fehlermeldung statt eines geratenen Ergebnisses.

## Hintergrund und Umriss

* **Hintergrund:** »Kamerabild anzeigen« legt das entzerrte Bild mit einstellbarer Deckkraft unter den Entwurf. Es ist ein **Einzelbild**, kein Livebild: Mit »Bild aktualisieren« nimmst du ein neues auf. Das Bild erscheint nur auf dem Bildschirm, **weder in der Projektdatei noch im G-Code**. Nach einem Neustart ist der Hintergrund leer, bis du es neu aufnimmst. Die **Lage der Platte** auf der Arbeitsfläche stellst du hier ein. Das Programm rechnet dir aus, wo an der Maschine der Nullpunkt liegen muss.
* **Umriss:** »Umriss erkennen« findet das Werkstück anhand des Farbunterschieds zur Unterlage. Du übernimmst ihn mit »Als Form einfügen« (ein Rückgängig-Schritt) oder »Als Reststück anlegen« (für den Plattenplaner, siehe [Platten und Möbel](Platten-und-Möbel)). Es wird nur das größte Werkstück erkannt, Löcher werden gefüllt. Ein Bild des leeren Betts als Vergleich hilft bei ähnlichen Farben.

Im Einfach-Modus sind nur die wichtigsten Schritte sichtbar. Der Rest liegt hinter »Mehr Einstellungen«.

## Grenzen, die du kennen solltest

* **Parallaxe:** Die Kalibrierung gilt für die **Ebene der Marken**. Liegt die Oberfläche des Materials höher, erscheint sie von der Kamera aus nach außen verschoben. Bei 1 m Kamerahöhe und 360 mm Abstand von der Mitte sind das für eine 3 mm dicke Platte rund 1,1 mm, für eine 18-mm-Platte rund **6,5 mm** und für einen 40-mm-Block rund 14 mm. **Lösung:** Marken auf Höhe der Materialoberfläche legen (zum Beispiel auf Unterlagen gleicher Dicke) oder die Kamera höher montieren. Eine rechnerische Korrektur gibt es nicht.
* **Objektivverzerrung** wird nicht korrigiert. Weitwinkel- und Actionkameras verzerren am Bildrand oft mehrere Millimeter. Montiere die Kamera hoch, nutze das »Kontrollraster« (gekrümmte Linien zeigen Verzerrung) und beachte den Kontrollwert.
* **Beleuchtung:** gleichmäßiges, weiches Licht ohne Glanz, matt gedruckte Marken. Spiegelnde Platten, harte Schatten und Gegenlicht stören die Erkennung. Die Kamera sollte nicht mit Auto-Belichtung »pumpen«.
* **Auflösung:** Je Modul des QR-Codes braucht das Programm etwa 2,5 bis 3 Bildpunkte. Bei 50-mm-Marken sind das mindestens etwa 1,25 bis 1,5 Bildpunkte je Millimeter, bei 1280 Bildpunkten Breite höchstens etwa 850 bis 1000 mm Arbeitsfläche. Darunter warnt der Dialog. Dann hilft: näher heran, höhere Auflösung, größere Marken. Kleine, verrauschte Marken werden im Test zunehmend **nicht mehr gelesen**.
* **Kamera bewegt:** Die Kalibrierung gilt für eine Kameralage und eine Bildgröße. Wird die Kamera angestoßen, musst du neu kalibrieren. Das Programm erkennt eine bewegte Kamera **nicht**.
* **Nicht vorhanden:** Livebild im Zeichenbereich, Maschinen-Livebild mit Werkzeugposition, Streaming vom Handy, automatische Reaktion auf das Bild, mehrere Kameras.

## Windows-Kameraberechtigung und Datenschutz

Desktop-Programme sehen die Kamera nur, wenn unter **Einstellungen → Datenschutz & Sicherheit → Kamera** der **Kamerazugriff**, »Apps den Zugriff auf Ihre Kamera erlauben« und darunter »Desktop-Apps den Zugriff auf Ihre Kamera erlauben« eingeschaltet sind. Verweigert Windows den Zugriff, erklärt der Dialog genau diesen Weg. Das alles ist **unter Windows nicht geprüft**.

Es wird **nichts gespeichert oder übertragen**: Einzelbilder gehen nur an das Programm auf deinem Rechner und bleiben im Arbeitsspeicher. Kein Verlauf, keine Standbilder auf der Platte, keine Cloud, kein Portal. Die Kamera kann Personen erfassen. Richte sie nicht auf fremde Räume.

## Wenn Marken nicht gefunden werden

Siehe [Fehlersuche](Fehlersuche), Abschnitt »Die Kamera findet die Marken nicht«.

## Mehr

* Der Zeichenbereich und der Umgang mit Formen: [Zeichnen und Importieren](Zeichnen-und-Importieren)
* Bericht über deinen Test mit einer echten Kamera: [Mitmachen und Tests](Mitmachen-und-Tests). Das hilft besonders.
