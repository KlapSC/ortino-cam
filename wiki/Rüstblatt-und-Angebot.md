# Rüstblatt und Angebot

Mit einem Klick erzeugt ortino.CAM ein **PDF** für den Tisch der Maschine (das **Rüstblatt**) und für den Kunden (die **Kostenrechnung** oder das **Angebot**). Beide Teile stehen in einer Datei oder einzeln. Beides gibt es auf Deutsch und Englisch, je nach Programmsprache.

![Dialog Rüstblatt und Angebot mit Kosteneingaben und Seitenvorschau (erfundene Beispielwerte)](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/ruestblatt-light.png)

> **Ehrlich zum Stand:**
>
> * **Zeiten und Kosten sind Näherungen.** Die Fräszeit ist die Zeitschätzung der Werkzeugwege (mit Beschleunigung an Ecken, aber ohne Werkzeugwechsel, Spindelhochlauf, Rüsten und Nachbearbeitung). Die Schätzung wurde nicht mit echten Laufzeiten verglichen. Das ist **kein verbindliches Angebot**, das steht auch auf jeder Angebotsseite.
> * Die PDF-Dateien wurden mit mehreren Prüfwerkzeugen und im Browser angesehen. **Nicht geprüft** sind Acrobat, die Vorschau unter macOS, die PDF-Betrachter von Edge und Chrome unter Windows, das Drucken und der Dateidialog unter Windows.
> * Die Beträge im Bild sind erfunden.

## So geht's

1. Lege im Schritt **Bearbeitung** deine Bearbeitungen an. Je besser die Werkzeugwege berechnet sind, desto besser stimmt die Zeit.
2. Öffne den Dialog: Knopf **»Rüstblatt / Angebot …«** im Schritt »Fräsen« (unter »G-Code speichern«) oder im Schritt »Prüfen«, im Datei-Menü (»Rüstblatt / Angebot (PDF) …«) oder über die Befehlspalette (`Strg+K`: »Rüstblatt«, »Angebot«).
3. Wähle links die **Dokumentart** (*Beides*, *Rüstblatt*, *Angebot*), bei mehreren Platten die Platte, trage Kunde, Auftragsnummer und Hinweise zum Spannen ein.
4. Gib Preise und Sätze ein (siehe unten). Rechts siehst du die Seiten als Vorschau, darunter die Kostenaufschlüsselung.
5. **PDF speichern** oder **Drucken**. Vorgeschlagen wird der Dateiname `<Projekt>_Ruestblatt_Angebot.pdf` (ohne Umlaute).

Deine Eingaben werden **im Projekt gespeichert** und sind beim nächsten Öffnen wieder da (ein Rückgängig-Schritt). Im Einfach-Modus siehst du nur Dokumentart, Kunde, Materialpreis, Maschinenstundensatz, Aufschlag und Mehrwertsteuer. Der Rest liegt unter »Mehr Einstellungen«.

## Was im Rüstblatt steht

Je Platte eine bis wenige A4-Seiten:

| Abschnitt | Inhalt |
|---|---|
| Kopf | Projekt, Platte, geschätzte Fräszeit, Zahl der Bearbeitungen, Werkzeuge und Werkzeugwechsel |
| Auftrag, Material, Nullpunkt | Maschine, Postprozessor, Material, Dicke, Plattenmaß, Maserung, Nullpunkt X/Y/Z, Sicherheitshöhe, Kunde, Auftragsnummer, dazu eine Skizze der Platte mit Nullpunkt-Marke und Achsen |
| Spannmittel und Hinweise | Spannmittel und Sperrzonen, dein Text »Hinweise zum Spannen«, Projektnotizen |
| Werkzeuge | in der Reihenfolge der ersten Verwendung: Nummer, Name, Typ, Durchmesser, Drehzahl, Vorschub, **Einsatzzeit** |
| Reihenfolge der Bearbeitungen | Name, Art, Werkzeug, Tiefe, geschätzte Zeit, Bänder für die Werkzeugwechsel |
| Prüfliste und Hinweise | Meldungen der Prüfliste mit Lösung (höchstens 30), Warnungen des Postprozessors |
| Vor dem Start | sechs Kästchen zum Abhaken: Spannen, Nullpunkt, Werkzeug, Absaugung und Schutz, Rahmen oder Luftschnitt, Not-Aus |
| Vorschau der Werkzeugwege | maßstabsgetreue Draufsicht: Schneidwege je Werkzeug in einer Farbe, Linienbreite gleich Werkzeugdurchmesser, Nullpunkt und Maßstab |
| Notizen und Abzeichnen | Linien für Notizen, drei Unterschriftsfelder (eingerichtet, geprüft, freigegeben) |

Die Vorschau zeigt Wege, keine Tiefen, keine Eilgänge und mehrfach gefahrene Strecken nur einmal. Bei sehr vielen Punkten vereinfacht das Programm die Wege und schreibt das unter die Vorschau. Der Start-Check der Maschine hängt an der Verbindung und läuft offline nicht. Das Rüstblatt übernimmt deshalb nur Prüfliste und Postprozessor-Warnungen und bildet den Rest als Abhak-Liste ab. Eine **Opferplatte** bekommt ein Rüstblatt mit Hinweis, zählt aber nicht zum Angebot.

## Die Kostenrechnung

Alle Eingaben sind freiwillig. Voreingestellt sind Mehrwertsteuer 19 % und Währung Euro (wählbar: EUR, CHF, USD, GBP).

| Eingabe | Bedeutung |
|---|---|
| Materialpreis | je Platte oder je Quadratmeter |
| Berechnung des Materials | anteilig nach **Teilefläche** (die Plattenausnutzung aus dem Plattenplaner), nach dem **benutzten Bereich** oder die **ganze Platte** |
| Maschinenstundensatz | Preis je Stunde Fräszeit |
| Rüstzeit je Platte | in Minuten |
| Werkzeugverschleiß je Stunde | in Geld |
| Stundensatz Handarbeit | gilt auch fürs Rüsten |
| Handarbeit insgesamt | in Minuten |
| Aufschlag | in Prozent |
| Mehrwertsteuer | in Prozent |

**Rechenweg:** Material (Plattenpreis mal Anteil) plus Maschinenzeit (Stunden mal Stundensatz) plus Werkzeugverschleiß plus Rüsten plus Handarbeit ergibt die **Zwischensumme**. Darauf kommt der Aufschlag, daraus ergibt sich die **Nettosumme**, dann die Mehrwertsteuer und der **Gesamtbetrag**. Gerechnet wird in ganzen Cent, jede Position wird kaufmännisch gerundet. Die gedruckte Summe ist deshalb genau die Summe der gedruckten Positionen. Zusätzlich steht als Richtwert der Nettopreis je erkanntem Teil auf der Seite.

**Beispiel (erfundene Werte):** Platte 2500 × 1250 mm, Teile füllen 48 %, Platte 85,00 €, Fräszeit 1,25 h, Maschine 48 €/h, Verschleiß 2,40 €/h, Rüsten 30 min und Handarbeit 20 min bei 36 €/h, Aufschlag 15 %, Mehrwertsteuer 19 %:

| Position | Betrag |
|---|---:|
| Material (85,00 € × 0,48) | 40,80 € |
| Maschinenzeit (1,25 h × 48,00 €) | 60,00 € |
| Werkzeugverschleiß (1,25 h × 2,40 €) | 3,00 € |
| Rüsten (0,5 h × 36,00 €) | 18,00 € |
| Handarbeit (⅓ h × 36,00 €) | 12,00 € |
| Zwischensumme | 133,80 € |
| Aufschlag 15 % | 20,07 € |
| Nettosumme | 153,87 € |
| Mehrwertsteuer 19 % | 29,24 € |
| **Gesamtbetrag** | **183,11 €** |

**Nicht eingerechnet** sind: Verschnitt und Restplatten (dafür ist der Aufschlag gedacht), Zeit für Werkzeugwechsel und Spindelhochlauf, das Einrichten des Programms, Energie, Absaugung und Transport. Das Angebot rechnet **einen Auftrag mit einem Durchlauf je Platte**. Für mehrere Exemplare passt du die Zahl der Platten oder die Handarbeit an. Es gibt auch keinen Kundenstamm, keine Angebotsnummern und keine Zahlungsbedingungen. Material aus dem Reststück-Lager wird mit dem eingegebenen Plattenpreis bewertet, einen geringeren Preis trägst du selbst ein. Schriften im PDF sind die Standardschriften (Helvetica), Zeichen außerhalb von Windows-1252 erscheinen als Ersatz oder `?`.

## Zeitschätzung mit deinen Läufen kalibrieren

Weil die Zeitschätzung nicht mit echten Laufzeiten verglichen wurde, protokolliert das Programm deine echten Läufe (siehe [Werkzeuge und Schnittdaten](Werkzeuge-und-Schnittdaten), Abschnitt zum Job-Protokoll). Der Schalter **»Zeitschätzung mit meinen Läufen kalibrieren«** (Standard aus) multipliziert die Maschinenzeit mit dem Zeitfaktor aus deinen bisherigen Läufen. Das geht erst nach mindestens drei abgeschlossenen Läufen von je fünf Minuten. Die Angebotsseite nennt Faktor und Zahl der Läufe. Bisher nur gegen den Simulator geprüft.

## Datenschutz

Kunde, Auftragsnummer, Spannhinweise und vor allem **Preise und Stundensätze sind privat**. Beim Erstellen eines Designpakets für das [Community-Portal](Community-Portal) lässt das Programm diese Eingaben weg. Wenn du aber eine `.ocam`-Projektdatei weitergibst, geben sie mit.

## Weiter

* [Prüfen und Simulation](Prüfen-und-Simulation)
* [Platten und Möbel](Platten-und-Möbel)
