# Große Teile kacheln (seit 0.7.0)

> **Ehrlich zum Stand:** Die Kachelung ist nur gegen Geometrie- und Eigenschaftstests, die Simulation, den eingebauten Maschinensimulator und Chromium geprüft. **Nie an einer echten Maschine** und nicht unter Windows (WebView2). Wie genau die Kacheln an der Naht zusammenpassen, hängt davon ab, wie genau der Fräser über einer Passmarke steht, wie gerade das Material nach dem Verschieben liegt und wie eben Platte und Opferplatte sind; das ist **nicht erprobt**.

Ist ein Werkstück größer als der **Verfahrweg** deiner Maschine (zum Beispiel 2400 × 1200 mm auf einer 600 × 400 mm Fräse), zerlegt ortino.CAM es in **Kacheln mit Überlappung** und erzeugt ein Programm je Kachel. Zwischen zwei Kacheln verschiebst du das Material um das **Vorschubmaß** und spannst neu; zwei **Passmarken**, die die vorige Kachel gebohrt hat, legen den XY-Nullpunkt der neuen Kachel fest.

## Ablauf am Tisch

1. **Kachel 1:** Material so spannen, dass Kachel 1 im Verfahrweg liegt, XY-Nullpunkt an der Ecke der Platte setzen, Z antasten, fräsen. Danach bohrt das Programm zwei kleine **Passmarken** in die Überlappung zu Kachel 2.
2. **Verschieben:** Material lösen, um das angezeigte Vorschubmaß verschieben (am besten an einer geraden Anschlagleiste, damit es nicht verdreht), spannen. Das Maß muss nicht genau stimmen; es muss nur Kachel 2 in den Verfahrweg bringen.
3. **Kachel 2:** Fräser (Spindel aus) über **Passmarke 1** fahren, mittig stellen und dort den XY-Nullpunkt setzen; dann an **Passmarke 2** die Lage bestätigen. Weicht sie mehr als die Toleranz ab (Standard 0,3 mm), sperrt der Start-Check die Kachel: Dann ist das Material verdreht oder der Fräser stand nicht mittig über Marke 1. Fräsen, und so weiter bis zur letzten Kachel.

## Gut zu wissen

* **3D-Relief, adaptives Räumen, Rest und Inlay** gehen nur, wenn sie **ganz in einer Kachel** liegen.
* Rüstblatt und Anleitung kennen die Kacheln; die Simulation läuft über alle Kacheln.
* Die Prüfung an Marke 2 nie überspringen. **Das erste Mal an einem Reststück mit zwei Kacheln**, die Naht durch Verschnitt legen.

Verwandt: [Doppelseitig fräsen](Doppelseitig-fraesen) (mehrere Aufspannungen mit gemeinsamen Bezugspunkten), [Fräsen an der Maschine](Fräsen-an-der-Maschine), [Rüstblatt und Angebot](Rüstblatt-und-Angebot).
