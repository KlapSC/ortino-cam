# Erste Schritte

Diese Seite führt dich vom ersten Start bis zum ersten Werkstück. Du lernst zuerst an einem fertigen **Beispielprojekt** (einem Türschild), danach legst du ein eigenes Projekt an. Alles, was die Maschine betrifft, übst du zuerst mit der **simulierten Demo-Maschine**. Dafür brauchst du keine Fräse.

![ortino.CAM: Entwurf eines Türschilds mit Text, Bohrungen und Außenkontur im Zeichenbereich](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/entwurf-light.png)

> **Sicherheit zuerst:** Wenn du später an einer echten Maschine fräst, teste **zuerst ohne Werkzeug und ohne Material**, halte den **Not-Aus** in Reichweite und lass die Maschine nie unbeaufsichtigt. Die Software ist eine frühe Version, und nicht alles ist an einer echten Maschine erprobt (siehe [Home](Home)). Siehe den [Haftungsausschluss](https://github.com/KlapSC/ortino-cam#haftungsausschluss).

## 1. Installieren und starten

Wie du ortino.CAM installierst, steht unter [Installation und Updates](Installation-und-Updates). Beim ersten Start siehst du die **Willkommensseite**. Sie bietet vier Karten an (und, einmal nach dem Angebot »Maschine einrichten«, eine geführte Einführung, siehe Abschnitt 4):

* **Neues Projekt:** Platte, Material und Maschine festlegen.
* **Beispiele ansehen:** die Beispielgalerie mit 13 fertigen Projekten, darunter das Türschild (siehe Abschnitt 4).
* **Projekt öffnen:** eine gespeicherte `.ocam`-Datei weiterbearbeiten.
* **Datei importieren:** SVG, DXF, PDF/AI oder ein Bild übernehmen.

Neue Nutzer starten im **Einfach-Modus**. Er zeigt je Bearbeitung nur die wichtigsten Einstellungen und begründet Vorschläge. Mit dem Umschalter **Einfach | Experte** in der Kopfleiste siehst du jederzeit alles. Umschalten ändert nie das Projekt.

## 2. Das Beispielprojekt öffnen

Auf der Willkommensseite klickst du auf **Beispiele ansehen** und wählst das **Türschild**. Alternativ lädst du die Datei `tuerschild.ocam` von der [Release-Seite](https://github.com/KlapSC/ortino-cam/releases/latest) herunter und öffnest sie per Doppelklick oder mit `Strg+O`. Auch die Befehlspalette (`Strg+K`) kennt »Beispielprojekt „Türschild“ laden«.

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

## 4. Beispiele, Einführung und Lektionen

Drei Hilfen für den Anfang. Du findest sie im Menü **Hilfe** der Kopfleiste und in der Befehlspalette (`Strg+K`).

> **Ehrlich zum Stand:** Alle Beispiele und Lektionen sind **nicht gefräst**. Sie sind mit Tests, der Simulation und einem Browser (Chromium) geprüft, nie an einer echten Maschine und nicht unter Windows (WebView2). Fahre ein Beispiel zuerst ohne Werkzeug und ohne Material, und fange danach mit einem Reststück an.

### Beispielgalerie

![Beispielgalerie mit Türschild, Namensschild, Untersetzer-Set und weiteren Projekten](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/galerie-light.png)

Der Dialog **»Beispiele«** zeigt 13 fertige kleine Projekte als Kacheln. Jede Kachel nennt Vorschau, Material und Dicke, geschätzte Fräszeit, Plattengröße, die Arten der Bearbeitungen und die Stufe (**Einsteiger** oder **Fortgeschritten**). Filter und Suche (auch auf Englisch) helfen beim Finden. Du öffnest die Galerie im Datei-Menü (»Beispiele ansehen …«), auf der Willkommensseite, im leeren Zeichenbereich, im Hilfe-Menü oder mit `Strg+K`.

* Ein Klick öffnet das Beispiel **als neues Projekt** im Schritt »Design«. Hat das offene Projekt ungespeicherte Änderungen, fragt das Programm vorher nach. Beim Speichern fragt es nach einem Namen, das Original bleibt unverändert.
* **Einsteiger:** Türschild, Namensschild (mit Eingabeformular), Untersetzer-Set, Schneidebrett mit Griff, Regalseiten mit Dübellöchern, Regalboden mit Lochraster, Lochblech-Panel.
* **Fortgeschritten:** Gravurkarte, rundes Schild mit Bogentext, Fingerzinken-Ecke, Wandpaneel mit Wabenmuster, Intarsie Stern, Relief-Rosette.
* Die Zeiten sind Schätzungen der reinen Bahnzeit, ohne Aufspannen, Nullpunkt und Werkzeugwechsel. Das Relief rechnet in Entwurfsqualität und ist mit rund 45 Minuten das längste Beispiel.
* Beim ersten Öffnen der Galerie rechnet das Programm die Vorschauen. Das dauert einige Sekunden.
* Nimmt das Beispiel die Maschine aus deiner Einrichtung, übernimmt es auch deren Voreinstellungen. Ist ein Beispiel größer als der Arbeitsbereich deiner Maschine, steht das auf der Kachel.

### Geführte Einführung

![Geführte Einführung: Karte »Fünf Schritte, ein Weg« mit hervorgehobener Schrittleiste](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/einfuehrung-light.png)

Ein Rundgang durch die fünf Schritte und die wichtigsten Stellen: 11 Karten im Experten-Modus, 12 im Einfach-Modus. Das hervorgehobene Element bleibt **bedienbar**, die Überlagerung fängt keine Klicks ab. Die Karte hat Zurück, Weiter und Beenden. `Esc` beendet jederzeit, mit `←` und `→` blätterst du, wenn der Fokus in der Karte liegt.

* Er startet **einmal von selbst**, nachdem das Angebot »Maschine einrichten« erledigt ist, und nur auf der Willkommensseite eines leeren Projekts, nie über einem Dialog.
* Erneut starten: **Hilfe → Einführung starten** oder `Strg+K` → »Einführung starten«.
* Die Einführung wechselt nur die Arbeitsschritte und **ändert nie dein Projekt**. Findet sie ein Element nicht (zum Beispiel weil es in diesem Modus fehlt), erklärt sie den Schritt an der Schrittleiste oder überspringt ihn.
* **Ungeprüft:** Position und Fokus der Karte sind nur im Browser getestet, nicht unter Windows (WebView2) und nicht bei 125 oder 150 % Skalierung.

### Lektionen

![Dialog »Lernen« mit sechs Lektionen und den Aufgaben der ersten Lektion](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/lektionen-light.png)

Der Dialog **»Lernen«** (Hilfe → Lektionen) bietet sechs Lektionen mit Fortschrittsring, Richtzeit und Stufe. Läuft eine Lektion, zeigt eine Karte in einer Ecke die Aufgaben. **Jede Aufgabe hakt sich selbst ab**, sobald dein Projekt den Zustand erreicht hat. Die Karte lässt sich einklappen, in eine andere Ecke legen und pausieren. Der Fortschritt bleibt auf diesem Rechner erhalten.

| Lektion | Stufe, Richtzeit |
|---|---|
| Erstes Schild: Text gravieren und ausschneiden | Einsteiger, ca. 15 min |
| Teil ausschneiden mit Haltestegen | Einsteiger, ca. 10 min |
| Tasche und Gravur mit V-Fräser | Fortgeschritten, ca. 20 min |
| Nullpunkt und Antasten (Simulator) | Einsteiger, ca. 10 min |
| Mehrere Teile auf eine Platte (Plattenplaner) | Fortgeschritten, ca. 10 min |
| Maschine einrichten (Profil, Post, Verbindung) | Einsteiger, ca. 10 min |

* Die Lektionen beginnen auf Wunsch in einem **neuen leeren Projekt** (mit Rückfrage bei ungespeicherten Änderungen). Wer im offenen Projekt weitermacht, bekommt sofort abgehakt, was dort schon stimmt.
* Die Lektionen »Nullpunkt und Antasten« und »Maschine einrichten« laufen gegen den **Simulator**. Das Antasten ist an einer echten Maschine in diesem Zusammenhang nicht getestet.
* Jede Lektion verweist auf eine Anleitung. Das Programm bringt sie mit und zeigt sie in einem kleinen Leser. Die Anleitungen gibt es **nur auf Deutsch**, auch in der englischen Oberfläche.
* Die Erkennung sieht nur, was im Projekt und in den beobachteten Aktionen steckt. Ob ein Rechteck »ein Schild« ist, weiß sie nicht. Ein Meilenstein wie »Simulation abgespielt« gilt je Sitzung: Nach einem Neustart zählt er erst wieder, wenn du es erneut tust. Bereits abgehakte Aufgaben bleiben abgehakt.

## 5. Speichern und Rückgängig

* `Strg+S` speichert das Projekt als `.ocam`-Datei, `Strg+Umschalt+S` speichert unter einem neuen Namen.
* `Strg+Z` macht Schritte rückgängig (bis zu 200), `Strg+Y` oder `Strg+Umschalt+Z` stellt sie wieder her. Auch Aktionen von Assistenten, Schnellstart und Claude sind je ein Schritt.
* Alle 30 Sekunden sichert das Programm automatisch. Nach einem Absturz bietet es auf der Willkommensseite an, den Stand wiederherzustellen.

## Was als Nächstes?

* [Maschine einrichten](Maschine-einrichten): Katalog, Verfahrwege, Steuerung
* [Fräsen an der Maschine](Fräsen-an-der-Maschine): verbinden, Nullpunkt, Start-Check
* [Tastenkürzel](Tastenkürzel) und [Glossar](Glossar)
* Wenn etwas hakt: [Fehlersuche](Fehlersuche)
