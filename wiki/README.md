# Wiki des Repositorys: Anleitung für den Betreiber

In diesem Ordner liegen die Seiten des GitHub-Wikis von `KlapSC/ortino-cam` als Markdown-Dateien. Hier werden sie gepflegt und von hier aus in das Wiki übertragen. **Diese Datei ist nur eine Anleitung und erscheint nicht im Wiki:** Der Workflow kopiert sie nicht.

## Aufbau

* Der **Dateiname ist der Seitenname**. Bindestriche werden im Wiki zu Leerzeichen im Titel (`Erste-Schritte.md` heißt »Erste Schritte«). Umlaute sind erlaubt.
* `Home.md` ist die Startseite, `_Sidebar.md` die Seitenleiste, `_Footer.md` die Fußzeile. Die Seitenleiste muss jede neue Seite aufführen.
* Links zwischen Seiten stehen im Format `[Text](Seitenname)`, ohne `.md`. Links ins Repository sind absolut.
* Bilder gibt es im Wiki nicht als Ordner. Die Seiten binden die vorhandenen Bilder aus `docs/bilder/` über ihre absolute Adresse `https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/<Datei>` ein (jeweils die helle Variante). Die Bilder müssen deshalb auf `main` des öffentlichen Repositorys liegen.

## Zwei Sprachen

Jede Seite gibt es auf Deutsch und auf Englisch. Die deutschen Texte sind die Vorlage; die englischen sind eine treue Übersetzung ohne eigenen Inhalt (keine Zahl, keine Behauptung stärker oder schwächer als im Deutschen).

* **Dateinamen:** Die englische Schwester hat einen eigenen Dateinamen (Tabelle unten). Vier Namen sind in beiden Sprachen gleich (`Art-Designer`, `Community-Portal`, `Export-STL-3MF`, `Videos`); damit sie sich nicht überschreiben, heißen die englischen Seiten dort `Art-Designer-en`, `Community-Portal-en`, `Export-STL-3MF-en` und `Videos-en`, wie die Startseite `Home-en`.
* **Sprachlink:** Die erste Zeile jeder Seite führt zur Schwester, danach folgt eine Leerzeile und die Überschrift. Deutsch: `[English](<englischer Seitenname>) | **Deutsch**`. Englisch: `**English** | [Deutsch](<deutscher Seitenname>)`.
* **Links im Text:** In einer englischen Seite zeigen Seitenlinks auf englische Seiten. Anker folgen der GitHub-Regel (klein, Leerzeichen zu `-`, Satzzeichen weg) und werden aus der **englischen** Überschrift gebildet; sie unterscheiden sich also von den deutschen.
* **Seitenleiste und Fußzeile:** `_Sidebar.md` hat oben den Sprachwechsel, dann die deutschen Einträge und darunter den Abschnitt »English« mit denselben Gruppen. Eine neue Seite kommt in ihrer Sprache in den passenden Abschnitt. `_Footer.md` steht in beiden Sprachen.
* **Pflege:** Wer eine deutsche Seite ändert, ändert die englische Schwester im selben Zug (und umgekehrt). Dasselbe gilt für `README.md` und `README.en.md` sowie für `docs/index.html` und `docs/en/index.html` (Projektseite) und `docs/llms.txt` und `docs/en/llms.txt`. Zitate von Beschriftungen des Programms nehmen in der englischen Fassung die englische Beschriftung der Oberfläche.
* **Prüfung:** `node --test scripts/wiki-zweisprachig.test.mjs` (im privaten Repository) meldet fehlende Schwestern, fehlende Sprachlinks, Seiten, die in der Seitenleiste fehlen, tote Seitenlinks und Anker, deutsche Funktionswörter in englischen Seiten und abweichende Gliederung. `node --test scripts/schaufenster-zweisprachig.test.mjs` prüft README, Projektseite, Sitemap und `llms.txt` in beiden Sprachen.
* **Übertragen:** Der Workflow kopiert alle `*.md` unter `wiki/` (außer dieser Datei), die englischen Seiten also ohne Änderung des Ablaufs. Die englische Startseite `Home-en` muss auf `main` mit übertragen werden, sonst führt der Sprachlink ins Leere.

### Namen der Seiten

| Deutsch | Englisch |
|---|---|
| Home | Home-en |
| 3D-Modelle-importieren | Importing-3D-Models |
| Art-Designer | Art-Designer-en |
| Bearbeitungen | Operations |
| Claude-MCP-und-API | Claude-MCP-and-API |
| Community-Portal | Community-Portal-en |
| Creator | Creators |
| Doppelseitig-fraesen | Double-Sided-Milling |
| Eigene-Vorlagen | Custom-Templates |
| Erste-Schritte | Getting-Started |
| Export-STL-3MF | Export-STL-3MF-en |
| Fehlersuche | Troubleshooting |
| Fester-Taster-und-Opferplatte | Fixed-Probe-and-Spoilboard |
| Formen-und-Muster-Generator | Shape-and-Pattern-Generator |
| Foto-zu-Relief | Photo-to-Relief |
| Fräsen-an-der-Maschine | Milling-on-the-Machine |
| Glossar | Glossary |
| Grosse-Teile-kacheln | Tiling-Large-Parts |
| Handy-Fernbedienung | Phone-Remote-Control |
| Installation-und-Updates | Installation-and-Updates |
| KI-Modelle-und-Startseite | AI-Models-and-Start-Page |
| Kamera-auf-der-Arbeitsplatte | Camera-on-the-Worktable |
| Kuechen-Rendering | Kitchen-Rendering |
| Kunden-und-Angebote | Customers-and-Quotes |
| Maschine-einrichten | Setting-Up-the-Machine |
| Mitmachen-und-Tests | Contributing-and-Testing |
| Modellieren-von-Reliefs | Modelling-Reliefs |
| Moebel-Designer | Furniture-Designer |
| Opferplatte-markieren | Marking-the-Spoilboard |
| Platten-und-Möbel | Sheets-and-Furniture |
| Plattenzuschnitt | Sheet-Cutting |
| Postprozessoren-und-Steuerungen | Post-Processors-and-Controllers |
| Prüfen-und-Simulation | Checking-and-Simulation |
| Rüstblatt-und-Angebot | Setup-Sheet-and-Quote |
| Sicherung-im-Portal | Backup-in-the-Portal |
| Stand-der-Erprobung | Testing-Status |
| Tastenkürzel | Keyboard-Shortcuts |
| Touch-und-Stift | Touch-and-Pen |
| Videos | Videos-en |
| Web-Designer-im-Portal | Web-Designer-in-the-Portal |
| Werkstatt-und-Team | Workshop-and-Team |
| Werkzeuge-und-Schnittdaten | Tools-and-Cutting-Data |
| Zeichnen-und-Importieren | Drawing-and-Importing |


## Einmalig einrichten

1. Im öffentlichen Repository **Settings → General → Features** das Häkchen bei **Wikis** setzen.
2. Im Reiter **Wiki** auf **Create the first page** klicken, eine beliebige Seite (zum Beispiel »Home« mit einem Wort) speichern. Erst dadurch entsteht das Wiki-Repository `ortino-cam.wiki.git`. Ohne diesen Schritt bricht der Workflow mit einer Meldung ab.
3. Unter **Settings → Actions → General → Workflow permissions** muss Schreiben für Workflows möglich sein, falls das dort eingeschränkt ist. Der Workflow fordert `contents: write` selbst an.

## Übertragen

* **Automatisch:** Jede Änderung unter `wiki/` auf `main` startet den Workflow »Wiki synchronisieren« (`.github/workflows/wiki-synchronisieren.yml`).
* **Von Hand:** Reiter **Actions → Wiki synchronisieren → Run workflow**. Starte ihn auf dem Branch, dessen Stand veröffentlicht werden soll (normalerweise `main`).

Der Workflow ersetzt **alle `*.md`-Dateien im Wiki** durch die aus `wiki/` (ohne diese `README.md`) und legt bei Änderungen einen Commit von `github-actions[bot]` an. Er benutzt nur `actions/checkout` und den automatisch bereitgestellten Zugang des Laufs. Dieser wird nur über eine Umgebungsvariable gelesen und steht nie in einer Befehlszeile oder Ausgabe. Änderungen, die jemand nur im Wiki selbst macht, gehen bei der nächsten Übertragung verloren. Pflege die Seiten deshalb nur hier.

### Ohne Workflow (von Hand)

```bash
git clone https://github.com/KlapSC/ortino-cam.wiki.git wiki-ziel
rm wiki-ziel/*.md
cp wiki/*.md wiki-ziel/
rm wiki-ziel/README.md
cd wiki-ziel
git add --all
git commit -m "Wiki aktualisiert"
git push
```

## Prüfen vor dem Übertragen

* Jede Seite beginnt mit dem Sprachlink (erste Zeile, danach eine Leerzeile) und hat genau eine Überschrift der ersten Ebene.
* Jeder Link `[Text](Seitenname)` und jeder Anker `[Text](Seitenname#anker)` zeigt auf eine vorhandene Seite und Überschrift, jedes Bild auf eine vorhandene Datei in `docs/bilder/`.
* `_Sidebar.md` führt alle Seiten auf, die deutschen im deutschen und die englischen im englischen Abschnitt.
* Im Wiki stehen keine internen Pfade, Quelltext-Namen, persönlichen Daten oder Zugangsdaten.
* Aussagen zur Erprobung stimmen mit der `README.md` überein: Was nur gegen Simulator und Tests geprüft ist, steht auch so im Wiki.

## Wenn eine neue Version erscheint

Das Wiki beschreibt eine bestimmte veröffentlichte Version (Angabe auf `Home.md` und in `_Footer.md`). Vor der Übertragung nach einem neuen Release die betroffenen Seiten anpassen und die Versionsangabe aktualisieren, und erst dann übertragen. Beschreibe im Wiki nur, was in der veröffentlichten Version enthalten ist.
