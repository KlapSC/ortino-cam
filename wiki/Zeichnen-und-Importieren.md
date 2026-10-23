# Zeichnen und Importieren

Im Schritt **Design** entwirfst du, was gefräst werden soll: Formen, Text, importierte Zeichnungen. Alles lässt sich mit Formeln und Variablen **parametrisch** halten, also später per Zahlenänderung anpassen.

![ortino.CAM: Entwurf eines Türschilds mit Text, Bohrungen und Außenkontur im Zeichenbereich](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/entwurf-light.png)

Die Platte ist das Material, aus dem du fräst. Ihr Ursprung liegt links unten, die Y-Achse zeigt nach oben. Alle Längen sind in Millimetern (oder Zoll, wenn du das Projekt so angelegt hast; die Einheit lässt sich danach nicht mehr ändern). Eine Liste der Tasten steht unter [Tastenkürzel](Tastenkürzel).

## Navigieren und Fangen

* **Zoom:** Mausrad. **Verschieben:** mittlere Maustaste ziehen oder Leertaste halten und mit der linken Taste ziehen. **Einpassen:** `F` passt die Ansicht an die Platte an, `Z` zoomt auf die Auswahl.
* **Fangen** rastet auf Raster, Endpunkte, Mitten, Plattenränder und Hilfslinien ein. Beim Ziehen von Knoten schaltet `Alt` das Fangen ab.
* **Rückgängig:** `Strg+Z` (bis zu 200 Schritte, getippte Änderungen werden zusammengefasst). **Autosave** speichert alle 30 Sekunden in eine Wiederherstellungsdatei. Findet das Programm beim Start einen automatisch gesicherten Stand, bietet es auf der Willkommensseite an, ihn wiederherzustellen.

## Formen zeichnen

| Werkzeug | Taste | Hinweis |
|---|---|---|
| Auswählen | `V` | Pfeiltasten verschieben die Auswahl um einen Rasterschritt (mit `Umschalt` zehnfach) |
| Knoten bearbeiten | `A` | siehe unten |
| Rechteck | `R` | mit Eckenradius |
| Ellipse / Kreis | `E` | |
| Vieleck / Stern | `P` | Ecken 3 bis 32, `S` schaltet zwischen Vieleck und Stern |
| Linie / Polylinie | `L` | |
| Stift (Bézier-Kurven) | `B` | Klick = Ecke, Klick und Ziehen = Kurve, Klick auf den Startpunkt schließt |
| Freihand | `Umschalt+B` | wird geglättet, Ecken bleiben Ecken, ein Regler stellt die Glättung ein |
| Text | `T` | |
| Messen | `M` | |

Jede Form hat Eigenschaften (Lage, Größe, Eckenradius, Drehung), in die du Zahlen **oder Formeln** schreiben kannst.

## Text und Schriften

Text bleibt **editierbar**: mehrzeilig, mit Ausrichtung sowie Buchstaben- und Zeilenabstand. Zur Wahl stehen die Schriften deines Windows und die mitgelieferten DejaVu-Schriften, mit Kerning und Ligaturen. Für Fräsbahnen wird Text in Umrisse aufgelöst. Mit »In Kurven« wird aus Text ein freier Pfad.

* **Text auf Pfad:** Der Text folgt einer Linie, einem Bogen, einem Kreis, Rechteck, Vieleck oder beliebigen Pfad und **bleibt Text**. Typisch ist ein Kreisschild mit Schrift außen herum. Du wählst die Form, öffnest den Abschnitt »Text auf diesem Pfad« und gibst den Text ein. Einstellbar sind Seite (außen, innen, mittig), Startversatz oder Winkel, Abstand zur Linie, die Leserichtung, »Kopf stehend vermeiden« und »Auf Pfadlänge einpassen«. Ändert sich die Pfadform, folgt der Text. Das Programm warnt, wenn der Pfad zu kurz oder zu eng ist oder sich Buchstaben berühren würden. Gebundene Texte verschachtelt der Plattenplaner nicht einzeln.
* **Einzellinienschriften:** Elf Hershey-Schriften (zum Beispiel Roman Simplex, Script, Gothic) liefern **offene Linien** statt Flächen, gedacht zum Gravieren mit dem Profil »Auf Linie«. Umlaute (Ä Ö Ü ä ö ü) setzt das Programm aus Buchstabe und zwei Punkten zusammen. **ß, €, Akzente und der Unterstrich fehlen** und werden gemeldet statt ersetzt.

* **Variable Felder und Seriennummern:** In einem Text darfst du Platzhalter in geschweiften Klammern setzen: `{n}` (Zähler, Start 1), `{n:001}` (Zähler mit drei Ziffern und Start 001: Die Ziffern geben Mindestbreite und Startwert an, `{n:100}` zählt 100, 101 …), `{datum}` (heutiges Datum, auch mit Muster wie `{datum:TT.MM.JJ}`), `{projekt}` (Projektname) und `{platte}` (Name der Platte). `{{` und `}}` ergeben je eine Klammer. Im Eigenschaften-Panel eines Textes zeigt der Abschnitt **»Variable Felder«** eine Vorschau des Ergebnisses. Die Zähler zählen in **Rechteck-, Kreis- und Pfad-Arrays** und in **Serien** hoch (Start und Schrittweite einstellbar, das Original ist Nr. 0; in einer Serie zählt jede Tabellenzeile). **Ungültige Platzhalter** bleiben wörtlich im Text stehen und lösen eine Warnung mit Lösung aus, nichts wird still verworfen.
  * **Grenzen:** `{datum}` kommt aus der Systemuhr in **UTC** (kurz nach Mitternacht Ortszeit kann es noch der Vortag sein). Der Zähler zählt je Kopie, nicht je Exemplar einer Stückzahl. Rechenausdrücke wie `{n+1}` gibt es nicht.

> **Nie gefräst oder graviert.** Text auf Pfad, Einzellinienschrift und Seriennummern sind rechnerisch und im Browser geprüft. Gravurqualität, Eintauchen an Strichenden und Reihenfolge der Striche sind ungeprüft.

## Formen bearbeiten

Im Eigenschaften-Panel und in der Befehlspalette (`Strg+K`) findest du:

* **Verschieben, Skalieren, Drehen, Spiegeln, Ausrichten, Verteilen, Duplizieren.**
* **Kombinieren** (Boolesche Operationen): **Verschweißen** (Vereinigung), **Subtrahieren**, **Schnittmenge**, **Ausschluss**. Beim Subtrahieren werden alle Formen von der zuerst gewählten abgezogen. »Originale behalten« ist wählbar.
* **Versatz:** eine Kontur nach außen oder innen um einen Abstand parallel verschieben.
* **Ecken runden**, **Fase**, **Kürzen** und **Verlängern** (Tasten `O`, `H`, `X`, `N`). Eine Vorschau zeigt das Ergebnis, das entfernte Stück gestrichelt in Rot. Bögen bleiben Bögen.
* **Array:** Kopien in einem **Raster** (Spalten, Zeilen, Lücken), auf einem **Kreis** (Anzahl, Winkel, Mitte, Kopien mitdrehen) oder **entlang eines Pfads** (siehe unten).
* **Verbinden:** offene Linien zu geschlossenen Konturen verketten.

### Array entlang eines Pfads

Wähle die Formen, öffne im Eigenschaften-Panel **Array …** und dort das dritte Segment **Entlang Pfad**. Als Pfad dienen Linie, Polylinie, Bogen, Kreis, Rechteck, Vieleck und Bézier-Kurve. Du gibst entweder die **Anzahl** oder den **Abstand** an, gemessen entlang der Bogenlänge. Unter »Mehr Einstellungen« stellst du Anfangs- und Endversatz ein, ob die letzte Kopie am Ende steht, die Richtung, ob die Kopien an der Tangente ausgerichtet werden, die Zusatzdrehung und den Bezugspunkt. Im Zeichenbereich siehst du live, wo die Kopien entstehen. **Kopien anlegen** ist ein einziger Rückgängig-Schritt.

* Bei einem **geschlossenen** Pfad wird die letzte Lage nicht doppelt gesetzt: Ein Kreis mit dem Abstand »Umfang durch 10« ergibt genau 10 Kopien.
* Bei Bézier-Pfaden gilt die auf Bögen gerundete Bahn. Die Abstände weichen höchstens um den Rundungsfehler von der echten Kurvenlänge ab.
* Text und Muster musst du vorher in Kurven umwandeln, wenn sie Pfad sein sollen. Höchstens 10 000 Kopien je Schritt. Bei jedem Fehler bleibt das Projekt unverändert, und das Programm nennt eine Lösung.
* **Nie gefräst:** Die Abstände sind mit Tests nachgemessen, geprüft ist nur gegen den Simulator und einen Browser.

### Knoten bearbeiten

Mit dem Knotenwerkzeug (`A`, oder Doppelklick auf eine Form) siehst du die Knoten: Quadrat = Ecke, Kreis = glatt, Raute = symmetrisch. Du kannst Knoten und Griffe ziehen, Segmente biegen, Knoten einfügen und löschen, Linie, Bogen und Kurve umschalten, Pfade verbinden, schließen und trennen und die **Einstichstelle** bestimmen, an der die Fräsbahn beginnt. »Knoten reduzieren« vereinfacht dichte Linienzüge zu wenigen Kurven. Parametrische Formen (Rechteck, Ellipse, Text) werden beim ersten Bearbeiten zu freien Pfaden, `Strg+Z` macht das rückgängig. Kurven bleiben im Dokument Kurven und werden erst beim Fräsen, Exportieren und Simulieren mit einer einstellbaren Toleranz in Kreisbögen gerundet.

## Variablen und Formeln

Mit Variablen änderst du ein Maß an einer Stelle, und alles, was davon abhängt, passt sich an. Lege sie im Schritt **Projekt** an (»Variablen …«). In jedem Zahlenfeld darfst du eine Formel mit Einheiten schreiben:

```text
Breite/2 - 5mm
1/4in
Dicke + 0,3mm
```

Das Programm kennt Funktionen und erkennt Zirkelbezüge. Tiefen als `Dicke + 0,3mm` schneiden immer ganz durch, auch wenn du die Plattendicke änderst. Das Beispielprojekt `tuerschild.ocam` nutzt eine Variable `Rand`.

## Dateien importieren

Mit `Strg+I` (Datei-Menü: »Importieren …«) oder per **Drag & Drop** auf das Fenster. Das Programm erkennt den Typ am Dateinamen.

| Format | Was passiert |
|---|---|
| **SVG** | Vektoren werden übernommen. Bei SVG gilt 1 px = 0,2646 mm (96 dpi). Stimmen die Maße nicht, hilft ein Skalierungsfaktor (Schnellwahl zum Beispiel »72 → 96 dpi ×1,33«). |
| **DXF** | Vektoren, Layer wahlweise als Layer übernommen. Eine Einheitenangabe in der Datei wird automatisch in Millimeter umgerechnet. Unterstützt werden DXF R12 bis 2018. |
| **PDF** und **AI** (mit PDF-Teil) | Vektoren, Seitenvorschau, Seitenwahl, Einheit und Maßstab, Ebenen werden zu Ebenen, eingebettete Schriften werden Umrisse. |
| **PNG, JPEG, WebP** | Das Bild wird zu Vektoren **nachgezeichnet**. |

Im Importdialog wählst du die **Platzierung** (automatisch auf die Platte passend, Position beibehalten, an der Plattenecke, zentriert), die Skalierung, die Ziel-Platte und den Ziel-Layer. Der Dialog zeigt Hinweise zum Import an.

**Was bei SVG und PDF mit Kurven passiert:** Freie Kurven (S-Kurven, Schriftzüge, Blobs) bleiben als **Bézier-Kurven mit Knoten und Griffen** erhalten und lassen sich mit dem Knotenwerkzeug nachbearbeiten. Kreise, Rundungen an Rechtecken, Langlöcher werden zu **Strecken und Kreisbögen** (einstellbare Toleranz, Voreinstellung 0,02 mm; beim PDF war das schon so, beim SVG ist es neu, dort kamen Kreise und Rundungen bisher als dichte Strecken). Sehr große oder aufwendige Dateien (mehr als 20 000 Kurvensegmente, über 4 Millionen Kurvenpunkte oder 10 Sekunden Rechenzeit) werden mit Hinweis wie bei ausgeschaltetem Schalter in Strecken zerlegt. Der Schalter **»Kurven als Béziers mit Knoten übernehmen«** im Importdialog (bei PDF unter »Mehr Einstellungen«) ist standardmäßig an, ausgeschaltet gilt das frühere Verhalten. Offene Kurven, die sich beim Verbinden zu einer Kontur verketten, verlieren dabei ihre Bézier-Fassung. Bei DXF (Splines) und beim Nachzeichnen von Bildern bleibt es bei Strecken und Bögen, Text aus PDF-Schriften bleibt ein Umriss. **Nur mit selbst erzeugten SVG- und PDF-Dateien geprüft**, nicht mit echten Dateien aus Illustrator, Inkscape oder CorelDRAW.

**Grenzen beim PDF-Import:**

* **Nicht mit echten Dateien aus Illustrator, Inkscape oder CorelDRAW erprobt.** Geprüft wurde mit Dateien aus anderen Programmen und selbst gebauten PDFs.
* Bilder in der PDF, Transparenz und Beschneidungspfade werden **nur gemeldet**, nicht umgesetzt. Zu Rasterbildern gibt es den Knopf »Als Bild nachzeichnen«.
* Strichbreiten und Strichelung werden ignoriert, es zählt die Mittellinie. Verläufe und Muster werden nur als Umriss übernommen.
* Nicht eingebettete Schriften werden gemeldet und nicht geraten. Lösung: Text in der Quelle in Umrisse umwandeln.
* EPS, `.ai` ohne PDF-Teil und DWG werden mit einer Erklärung abgelehnt. Speichere Illustrator-Dateien »PDF-kompatibel« oder exportiere aus dem CAD als DXF oder SVG.
* Passwortgeschützte PDFs werden abgelehnt.

### Bild nachzeichnen

Der Assistent zeichnet Fotos, Logos und Skizzen als fräsbare Konturen nach. Du wählst eine Voreinstellung (**Logo**, **Skizze**, **Foto-Kontur**, **Stufen**, **Farben**), die Zielgröße (oder »An die Platte anpassen (…)«) und mit **einem Regler** den Detailgrad. Eine **Live-Vorschau** zeigt Original, Schwarzweiß, Pfade und Überlagerung. Hinweise sagen dir, wenn das Bild zu klein ist, zu wenig Kontrast hat oder eher ein Foto ist (dann »Foto-Kontur« wählen). Mit »Dunkles / Helles nachzeichnen« und »Invertieren« legst du fest, was Vordergrund ist. Innenliegende Konturen werden zu Löchern. Das Ergebnis ist ein Rückgängig-Schritt.

## Exportieren

Unter Datei findest du **Als SVG exportieren** und **Als DXF exportieren** (die Vektoren der Platte). Den G-Code erzeugst du im Schritt »Fräsen«, siehe [Fräsen an der Maschine](Fräsen-an-der-Maschine). Einen Export als STL oder 3MF gibt es nicht.

## Probleme in der Zeichnung finden

Die **Geometrie-Prüfung** findet offene oder fast geschlossene Konturen, Doppelte, Selbstschnitte, Mikrosegmente, zu enge Innenradien für den Fräser, zu kleine Teile, dünne Stege und Formen außerhalb der Platte. Die meisten Funde repariert ein Klick (ein Rückgängig-Schritt). Siehe [Prüfen und Simulation](Prüfen-und-Simulation).

## Muster- und Relief-Studio

Zwei Studios erzeugen aufwendige Flächen mit wenigen Reglern: das **Muster-Studio** für gelochte Paneele (Waben, Sterne, Voronoi, Text und Bild als Lochraster) und das **Relief-Studio** für 3D-Reliefs. Du öffnest sie über die Werkzeugpalette oder die Befehlspalette (»Muster & Reliefs …«). Wie du daraus Werkzeugwege machst, steht unter [Bearbeitungen](Bearbeitungen).

## Weiter

* [Bearbeitungen](Bearbeitungen)
* [Werkzeuge und Schnittdaten](Werkzeuge-und-Schnittdaten)
