# Foto → Relief (KI-Tiefenschätzung auf deinem Rechner)

Seit Version 0.6.0 kann ortino.CAM aus einem **Foto** ein **Relief** machen: Ein kleines KI-Modell (Depth Anything V2 Small) schätzt, wie weit jede Stelle des Bildes entfernt ist. Daraus entsteht ein Höhenbild, das als gewöhnliches Relief ins Projekt kommt und im Relief-Studio weiterbearbeitet und gefräst werden kann.

> **Ehrlich zum Stand:** Das Ergebnis ist eine **Schätzung, keine echte Geometrie.** Bei Szenen mit räumlicher Tiefe (Gegenstände, Landschaften, Köpfe von der Seite) ist es brauchbar, bei **frontal fotografierten flachen Motiven** schwach. Geprüft wurde nur mit selbst gebauten Szenen und Tests, **nicht mit echten Fotos**, **nicht unter Windows** und **nichts davon wurde gefräst**. Fräse zuerst ein Probeteil.

## So geht es

1. Im **Relief-Studio** in der Galerie die Karte **»Foto → Relief«** wählen (oder `Strg+K` → »Foto → Relief (Tiefe schätzen) …«). Im Web-Designer des Portals gibt es sie nicht.
2. **Beim ersten Mal** fragt das Programm bei deinem Portal an, ob das **Tiefenmodell** dort liegt (eine kleine Anfrage ohne Foto), und bietet es zum **Herunterladen** an (47,3 MB, mit Fortschritt, Abbrechen und Fortsetzen; die Datei wird mit einer festen Prüfsumme geprüft). Ohne Netz: **»Modelldatei einspielen …«** (Datei vom USB-Stick). Liegt das Modell noch nicht auf deinem Portal, steht der Grund mit Lösung im Dialog; dann muss der Betreiber es bereitstellen.
3. **Foto wählen oder hineinziehen** (JPEG, PNG, WebP; die Drehung von Handyfotos wird beachtet; durchsichtige Teile werden Grund). Eine Schätzung dauert auf einem Rechner mit vier Kernen grob zwei bis sechs Sekunden, mit der Stufe »Fein« drei- bis viermal so lange; du kannst abbrechen.
4. Du siehst **drei Ansichten**: Foto, Tiefenkarte (hell = hoch) und eine schattierte Vorschau des Reliefs.
5. **Regler** rechts: Tiefe in mm, Invertieren, Hintergrund abflachen, Glätten, Kontrast, Tiefenkompression, »Grundwölbung entfernen« (für flache Motive von vorn) und die Auflösung.
6. **Einfügen** (`Strg+Enter`): Es entsteht ein Relief mit einer Bildebene (ein Rückgängig-Schritt). »Einfügen und im Studio öffnen« öffnet danach das Relief-Studio zum Weiterbearbeiten (mit Mustern mischen, Maske, Randauslauf, »Fräsen einrichten …«).

## Gut zu wissen

* **Das Foto verlässt deinen Rechner nie.** Die Rechnung läuft im Programm. Zum Portal geht nur die Anfrage, ob das Modell dort liegt, und der Download des Modells. Das **Originalfoto wird nicht im Projekt gespeichert**, nur das berechnete Höhenbild.
* **Rechte am Bild:** Bei Personenfotos brauchst du das Einverständnis der Abgebildeten, bei fremden Fotos die Erlaubnis des Urhebers.
* **Glas, Spiegel, Wasser, Himmel** schätzt das Modell schlecht.
* **Lizenz des Modells:** Die Gewichte stehen unter Apache-2.0. Die Trainingsdaten enthalten auch Sammlungen mit Forschungs- bzw. Nicht-kommerziell-Bedingungen; ob diese auf die Gewichte durchschlagen, ist rechtlich ungeklärt (Hinweis auch im Dialog).
* **Modell entfernen:** unten rechts im Dialog; vorhandene Reliefs bleiben unverändert.

## Für Betreiber eines eigenen Portals

Das Modell muss einmal auf das Portal: Workflow **»Modell bereitstellen«** (mit »hochladen«) oder `node scripts/modell-hochladen.mjs` mit dem Deploy-Token. Danach muss `https://<portal>/api/v1/models/depth-anything-v2-small-fp16-v1.onnx` mit 200 und einer Größe von 49 619 602 Byte antworten. Einzelheiten stehen in der Betriebsanleitung des Portals im Quelltext-Repository.

## Fehlersuche

| Symptom | Lösung |
|---|---|
| »Das Modell liegt noch nicht auf deinem Portal« | Den Betreiber bitten, es bereitzustellen, oder die Modelldatei von Hand einspielen. |
| »Andere Fassung« (Größe stimmt nicht) | Portal und Programm gehören nicht zusammen; Programm und Portal aktualisieren. |
| »Portal nicht erreichbar« | Verbindung prüfen, dann »Erneut prüfen«; oder von Hand einspielen. |
| Das Relief ist nur eine Wölbung | Motiv ist zu flach fotografiert: »Grundwölbung entfernen« probieren, anders fotografieren (schräg, mit Licht von der Seite). |
