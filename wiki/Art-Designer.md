# Art Designer (Wandbilder aus Holz)

Seit Version 0.9.0 gibt es im Menü **Erstellen → Art Designer …** (oder mit `Strg+K` → »Art Designer«) einen Dialog, der in fünf Schritten ein **Wandbild aus Holz** macht: als **geschnitztes Relief** aus einem Block oder als **Schichtholzbild** aus gestapelten Sperrholzlagen. Er baut auf dem Relief-Studio auf und ersetzt es nicht.

> **Ehrlich zum Stand:** Alles ist **gerechnet und am Bildschirm geprüft, nichts wurde gefräst oder verleimt.** Die Fräsbarkeit (steilste Flanke bis etwa 65°, kleinster Innenradius ab etwa 1,8 mm) ist ein Rechenwert, kein Erfahrungswert. Geprüft wurde mit Tests, dem Simulator und Chromium, **nicht unter Windows (WebView2) und nicht an einer echten Maschine.** Die Motive sind **eigene, am Rechner erzeugte Muster**; sie erinnern an Wandbilder aus Holz, sind aber keine Kopien und nicht alle gleich gelungen. Teste zuerst mit einem Stück Abfallholz.

## So geht es

1. **Format:** Gruppe wählen (A-Reihe, Poster 30 × 40 bis 100 × 140 cm, Quadrat, Panorama oder **Eigene Maße** von 50 bis 3000 mm), hoch oder quer, Plattendicke. Zu jedem Motiv gibt es ein empfohlenes Format.
2. **Motiv:** Links stehen die Motive mit Vorschaubild. Mit den Reglern **Größe, Dichte, Weichheit, Variation** und **Tiefe** änderst du das Bild; der **Würfel** (Zufall) macht ein neues. Die Zahl neben dem Würfel (Seed) hält ein Bild fest.
3. **Rahmen und Kante:** Randbreite (0 = ohne Rand), **Auslauf** (das Relief steigt weich zum Rand an), Außenkante gerade oder mit **Fase**.
4. **Text und Signatur:** Text, Größe und Platz im Rand (unten mittig, links oder rechts); er wird **eingefräst**.
5. **Fertig:** Die Zusammenfassung zeigt Platte, Motiv und Hinweise. **»In Projekt einfügen«** ist ein Rückgängig-Schritt; **»Einfügen und Fräsen einrichten«** legt zusätzlich Schruppen und Schlichten an (wie im Relief-Studio, siehe [Reliefs modellieren](Modellieren-von-Reliefs) und [Bearbeitungen](Bearbeitungen)).

Die Vorschau zeigt **»Kugelfräser bis Ø …«**: Mit einem größeren Fräser gehen feine Rillen verloren. Unter der Vorschau stehen **Hinweise mit Lösung**, zum Beispiel zu zu steilen Flanken oder zu großen Platten (die Platte ist größer als der Arbeitsbereich der Maschine: kleineres Format wählen oder in mehreren Aufspannungen fräsen, siehe [Große Teile kacheln](Grosse-Teile-kacheln)).

## Die acht Motive

| Motiv | Bild |
|---|---|
| **Blattstrom** | viele geschwungene, einander überlagernde Blätter in einer Strömung, Adern als Rillen; am besten im Querformat |
| **Blattzweig** | wenige große Blätter an einem schlanken S-förmigen Zweig, ruhig (früher »Blattwirbel«) |
| **Monstera** | große herzförmige Blätter mit Schlitzen und Löchern (die schwächste der neuen Vorlagen) |
| **Ginkgo** | Fächerblätter mit Falten an einem geschwungenen Zweig |
| **Farn** | gefiederte Wedel, die aus einem Punkt auffächern; dicht und spitzig |
| **Palmwedel** | Wedel mit Fiedern an einer erhabenen Mittelrippe |
| **Federfächer** | lange Bänder, die fächerförmig aus wenigen Punkten auslaufen |
| **Fließende Bänder** | Wellen aus Bändern mit feinen Fugen |

Alles ist ein **Höhenfeld** (wie im Relief-Studio), also mit Kugelfräser von oben fräsbar; es gibt keine Hinterschnitte und keine durchbrochenen Platten.

## Schichtholz

Im Schritt **Motiv** schaltest du von **Geschnitzt** auf **Schichtholz**. Das Motiv wird dann in **3 bis 24 Lagen** aus Sperrholz zerlegt (Stärke 3, 4 oder 6 mm), dazu kommt eine **Rückwand** (3 bis 40 mm).

* **Lagen:** Jede Lage besteht aus einem Rahmenstück mit Löchern und einzelnen Inseln. Der Schritt **»Lagen«** zeigt sie einzeln, die anderen blass darunter.
* **Passstifte** zum Ausrichten, **Nummern** an den Teilen, optional eine **Klebehilfe**.
* **Sperrholzplatten:** Die Teile werden auf Platten verteilt; das Format wählst du selbst (Standard: Arbeitsbereich der Maschine). **Passt ein Teil nicht auf die Platte** (zum Beispiel ein Bild von 50 × 70 cm bei einer Maschine mit 600 × 400 mm Arbeitsbereich), meldet das Programm einen Fehler mit Lösung, und »In Projekt einfügen« bleibt gesperrt, bis ein größeres Plattenformat gewählt ist.
* **Montageplan:** Text und Liste mit der Reihenfolge beim Kleben, kopierbar.
* **Einfügen** legt die Rückwand und die Sperrholzplatten mit den Fräsaufträgen an (ein Rückgängig-Schritt).
* **Auslauf und Fase entfallen:** Jede Lage hat eine senkrechte Kante; die Kante brichst du bei Bedarf von Hand. Die **Schrift** bleibt (V-Carving in die oberste Lage, dazu ein V-Fräser 60°).

**Grenzen im Schichtholz:** Die oberste Lage besteht bei fast allen Motiven nur aus dem Rahmen. Ginkgo und Farn haben in den oberen Lagen sehr dünne Stege (das Programm warnt vor »dünnen Engstellen«). Der Blattstrom ist im Hochformat ab der vierten Lage dünn besetzt. Teile in den Löchern anderer Teile werden nicht geschachtelt, der Verschnitt ist deshalb höher als bei [Platten und Möbel](Platten-und-Möbel).

## Eigenes Bild (ab 0.10.0)

Im Schritt **Motiv** gibt es den Abschnitt **»Eigenes Bild«**. Du wählst eine Datei (PNG, JPEG oder WebP) oder ziehst sie auf den Dialog. Das Programm verkleinert sie vor dem Rechnen auf höchstens 1024 Bildpunkte. **Die Helligkeit des Bildes ist die Höhe:** hell = hoch, dunkel = tief.

* **Lage:** Regler für links–rechts, unten–oben, **Größe** und **Drehung**; in der Draufsicht verschiebst du das Bild mit der Maus und skalierst es mit dem Mausrad (auch Pfeiltasten und +/−).
* **Verschwimmen mit dem Muster:** Du wählst die **Seite** (ganzes Bild, linke, rechte, obere oder untere Hälfte oder Mitte) und stellst **Grenze**, **Weichheit des Übergangs** und **Bildanteil** ein. So kann ein Gesicht zur Hälfte als Bild gezeichnet sein und auf der anderen Seite nur noch das Muster zeigen. Optional: weich ausklingender Bildrand und »Muster unter dem Bild«.
* **Ton** (unter »Mehr«): Kontrast, Gamma, Weichzeichnen, Invertieren.
* **Tiefe schätzen (KI):** für Fotos, wenn das Tiefenmodell von **Foto → Relief** vorhanden ist; sonst ist die Auswahl gesperrt, mit Hinweis.
* Geht im Modus **Geschnitzt** und im **Schichtholz** (dort wird der weiche Übergang zu schmalen Bändern, eine je Lagenstärke).

**Ehrlich zum Ergebnis:** Ein Gesicht von vorn ergibt als Helligkeit nur ein **flaches Relief**, eher ein sanftes Siegel als ein Porträt. Besser gelingen Seitenansichten und Bilder mit klaren Hell-Dunkel-Flächen. Ein **dunkler Hintergrund** wird zu tiefem Grund (das Bild sitzt dann in einer Mulde): nimm einen hellen Hintergrund oder »Invertieren«. **Harte Kanten** (Weichheit 0) sind senkrechte Wände und nur als Stufe fräsbar; bei Fotos mit viel Struktur das Weichzeichnen erhöhen. Transparenz zählt nicht (durchsichtige Teile werden weiß). Das Bild gehört zum geöffneten Dialog; beim Schließen ist es weg. **Nichts davon wurde gefräst;** die KI-Schätzung ist nicht mit dem echten Modell geprüft. Bei Fotos von Personen brauchst du das Einverständnis der Abgebildeten, bei fremden Bildern die Erlaubnis des Urhebers.

## Gut zu wissen

* **Nur im Programm,** nicht im [Web-Designer des Portals](Web-Designer-im-Portal).
* Mit Claude: Der Art Designer ist über die lokale Schnittstelle erreichbar (`art.formats`, `art.plan`, `art.layers`, `art.assembly`, `art.create`; das Bild über `motif.image`); siehe [Claude, MCP und API](Claude-MCP-und-API).
* Die 3D-Vorschau läuft ohne Grafikkarte langsam.

Weiter: [Reliefs modellieren](Modellieren-von-Reliefs), [Foto → Relief](Foto-zu-Relief), [Prüfen und Simulation](Prüfen-und-Simulation).
