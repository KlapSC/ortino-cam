# Erste Schritte

Diese Seite führt dich vom ersten Start bis zum ersten Werkstück. Du lernst zuerst an einem fertigen **Beispielprojekt** (einem Türschild), danach legst du ein eigenes Projekt an. Alles, was die Maschine betrifft, übst du zuerst mit der **simulierten Demo-Maschine**. Dafür brauchst du keine Fräse.

![ortino.CAM: Entwurf eines Türschilds mit Text, Bohrungen und Außenkontur im Zeichenbereich](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/entwurf-light.png)

> **Sicherheit zuerst:** Wenn du später an einer echten Maschine fräst, teste **zuerst ohne Werkzeug und ohne Material**, halte den **Not-Aus** in Reichweite und lass die Maschine nie unbeaufsichtigt. Die Software ist eine frühe Version, und nicht alles ist an einer echten Maschine erprobt (siehe [Home](Home)). Siehe den [Haftungsausschluss](https://github.com/KlapSC/ortino-cam#haftungsausschluss).

## 1. Installieren und starten

Wie du ortino.CAM installierst, steht unter [Installation und Updates](Installation-und-Updates). Beim ersten Start siehst du die **Willkommensseite**. Sie bietet vier Karten an:

* **Neues Projekt:** Platte, Material und Maschine festlegen.
* **Beispielprojekt Türschild:** ein fertiges Projekt ansehen.
* **Projekt öffnen:** eine gespeicherte `.ocam`-Datei weiterbearbeiten.
* **Datei importieren:** SVG, DXF, PDF/AI oder ein Bild übernehmen.

Neue Nutzer starten im **Einfach-Modus**. Er zeigt je Bearbeitung nur die wichtigsten Einstellungen und begründet Vorschläge. Mit dem Umschalter **Einfach | Experte** in der Kopfleiste siehst du jederzeit alles. Umschalten ändert nie das Projekt.

## 2. Das Beispielprojekt öffnen

Auf der Willkommensseite klickst du auf **Beispielprojekt Türschild**. Alternativ lädst du die Datei `tuerschild.ocam` von der [Release-Seite](https://github.com/KlapSC/ortino-cam/releases/latest) herunter und öffnest sie per Doppelklick oder mit `Strg+O`. Auch die Befehlspalette (`Strg+K`) kennt »Beispielprojekt „Türschild“ laden«.

Das Projekt ist ein Namensschild: 400 × 200 mm groß, 12 mm Sperrholz, mit der Aufschrift »Büro 12«, zwei Befestigungslöchern und einer abgerundeten Außenkontur. Die Maschine im Projekt ist eine **generische GRBL-Fräse 600 × 400**. Das ist nur eine Vorlage, deine Maße trägst du später ein (siehe [Maschine einrichten](Maschine-einrichten)).

Oben siehst du die fünf Schritte der Arbeit. Du wechselst zwischen ihnen mit der Maus oder mit `Alt+1` bis `Alt+5`.

| Schritt | Was du dort tust |
|---|---|
| **Projekt** | Platte (Größe, Dicke, Material, Nullpunkt), Maschine, Variablen |
| **Design** | Formen zeichnen und importieren |
| **Bearbeitung** | festlegen, was mit den Formen passieren soll |
| **Prüfen** | Prüfliste und 3D-Simulation |
| **Fräsen** | verbinden, Nullpunkt setzen, Start-Check, fräsen |

Gehe die Schritte am Beispiel durch:

1. **Projekt:** Die Platte ist 400 × 200 × 12 mm. Das Projekt hat eine **Variable** `Rand` mit dem Wert 20 mm. Die Außenkontur ist als Formel `400 - 2*Rand` angelegt.
2. **Design:** Das Schild ist ein Rechteck mit Eckenradius 15 mm, dazu zwei kleine Kreise (3 mm) und der Text. Klicke das Rechteck an und sieh dir im Eigenschaften-Panel die Formeln an. Probiere aus: Ändere im Schritt »Projekt« die Variable `Rand` auf 30 mm. Das Schild wird schmaler, die Werkzeugwege rechnen sich neu. `Strg+Z` nimmt es zurück.
3. **Bearbeitung:** Es gibt drei Bearbeitungen: **Bohrungen** (die beiden Kreise, 3-mm-Bohrer), **Beschriftung ausräumen** (eine Tasche, 2 mm tief, mit einem 3,175-mm-Fräser) und **Außenkontur** (ein Profil außen mit einem 6-mm-Fräser, mit Haltestegen, ganz durch die Platte). Klicke eine Bearbeitung an und sieh dir an, was im Eigenschaften-Panel steht. Mehr zu den Arten: [Bearbeitungen](Bearbeitungen).
4. **Prüfen:** Lies die Prüfliste (Fehler sperren das Fräsen) und spiele die 3D-Simulation ab. Siehe [Prüfen und Simulation](Prüfen-und-Simulation).
5. **Fräsen:** Verbinde dich mit der **Demo** (Karte »Verbindung«, Art »Demo«). Setze den Nullpunkt, lies den Start-Check, fahre den **Rahmen** und starte das Programm. Die simulierte Maschine fährt den ganzen Ablauf. Siehe [Fräsen an der Maschine](Fräsen-an-der-Maschine).

## 3. Dein erstes eigenes Projekt

1. **Neues Projekt** (`Strg+N`). Wähle eine Vorlage (Schild, Plattenzuschnitt, Möbelplatte, Relief/Quadrat oder Eigene Größe), gib die Maße deines Materials ein und wähle deine Maschine. Der Dialog zeigt dir, ob die Platte in den Fräsbereich der Maschine passt. Die **Einheit** (Millimeter oder Zoll) kannst du danach nicht mehr ändern, alles andere schon.
2. **Maschine einrichten:** Hast du noch keine Maschine eingerichtet, tu das jetzt (oder später, aber vor dem ersten Lauf an der echten Maschine): [Maschine einrichten](Maschine-einrichten).
3. **Etwas zum Fräsen wählen.** Zwei Wege:
   * **Schnellstart** »Was möchtest du fräsen?«: Du wählst eine Absicht (zum Beispiel Schild mit V-Carving, Ausschneiden, Bohrbild, Tasche, Gravur, Inlay) und beantwortest zwei bis vier Fragen. Das Programm zeigt einen **Plan** mit Werkzeug, Tiefen und Zeit, erklärt jede Entscheidung (»Warum so?«) und bietet drei Qualitätsstufen. Mit »Übernehmen« legt es alles in einem Rückgängig-Schritt an. Du findest den Schnellstart auf der Karte im Schritt »Projekt« und in der Befehlspalette.
   * **Selbst zeichnen:** Im Schritt **Design** zeichnest du Formen (`R` Rechteck, `E` Ellipse, `T` Text …) oder importierst eine Zeichnung. Mehr dazu unter [Zeichnen und Importieren](Zeichnen-und-Importieren). Danach legst du im Schritt **Bearbeitung** mit **Neue Bearbeitung** die passende Bearbeitung an.
4. **Prüfen:** Prüfliste lesen, Simulation ansehen, Hinweise der Glühbirne in der Kopfleiste beachten.
5. **G-Code speichern oder fräsen.** Im Schritt »Fräsen« kannst du den G-Code als Datei speichern oder direkt an eine GRBL-Maschine schicken.

**Wichtig bei Schnittwerten:** Alle Vorschläge für Vorschub und Drehzahl sind **Richtwerte**, keine Gewähr. Sie hängen von deiner Maschine, deinem Fräser und deinem Material ab. Prüfe sie, fange vorsichtig an und probiere mit einem Reststück. Mehr unter [Werkzeuge und Schnittdaten](Werkzeuge-und-Schnittdaten).

## 4. Speichern und Rückgängig

* `Strg+S` speichert das Projekt als `.ocam`-Datei, `Strg+Umschalt+S` speichert unter einem neuen Namen.
* `Strg+Z` macht Schritte rückgängig (bis zu 200), `Strg+Y` oder `Strg+Umschalt+Z` stellt sie wieder her. Auch Aktionen von Assistenten, Schnellstart und Claude sind je ein Schritt.
* Alle 30 Sekunden sichert das Programm automatisch. Nach einem Absturz bietet es auf der Willkommensseite an, den Stand wiederherzustellen.

## Was als Nächstes?

* [Maschine einrichten](Maschine-einrichten): Katalog, Verfahrwege, Steuerung
* [Fräsen an der Maschine](Fräsen-an-der-Maschine): verbinden, Nullpunkt, Start-Check
* [Tastenkürzel](Tastenkürzel) und [Glossar](Glossar)
* Wenn etwas hakt: [Fehlersuche](Fehlersuche)
