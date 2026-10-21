# Wiki des Repositorys: Anleitung für den Betreiber

In diesem Ordner liegen die Seiten des GitHub-Wikis von `KlapSC/ortino-cam` als Markdown-Dateien. Hier werden sie gepflegt und von hier aus in das Wiki übertragen. **Diese Datei ist nur eine Anleitung und erscheint nicht im Wiki:** Der Workflow kopiert sie nicht.

## Aufbau

* Der **Dateiname ist der Seitenname**. Bindestriche werden im Wiki zu Leerzeichen im Titel (`Erste-Schritte.md` heißt »Erste Schritte«). Umlaute sind erlaubt.
* `Home.md` ist die Startseite, `_Sidebar.md` die Seitenleiste, `_Footer.md` die Fußzeile. Die Seitenleiste muss jede neue Seite aufführen.
* Links zwischen Seiten stehen im Format `[Text](Seitenname)`, ohne `.md`. Links ins Repository sind absolut.
* Bilder gibt es im Wiki nicht als Ordner. Die Seiten binden die vorhandenen Bilder aus `docs/bilder/` über ihre absolute Adresse `https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/<Datei>` ein (jeweils die helle Variante). Die Bilder müssen deshalb auf `main` des öffentlichen Repositorys liegen.

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

* Jede Seite beginnt mit genau einer Überschrift der ersten Ebene.
* Jeder Link `[Text](Seitenname)` zeigt auf eine vorhandene Datei, jedes Bild auf eine vorhandene Datei in `docs/bilder/`.
* `_Sidebar.md` führt alle Seiten auf.
* Im Wiki stehen keine internen Pfade, Quelltext-Namen, persönlichen Daten oder Zugangsdaten.
* Aussagen zur Erprobung stimmen mit der `README.md` überein: Was nur gegen Simulator und Tests geprüft ist, steht auch so im Wiki.

## Wenn eine neue Version erscheint

Das Wiki beschreibt eine bestimmte veröffentlichte Version (Angabe auf `Home.md` und in `_Footer.md`). Vor der Übertragung nach einem neuen Release die betroffenen Seiten anpassen und die Versionsangabe aktualisieren, und erst dann übertragen. Beschreibe im Wiki nur, was in der veröffentlichten Version enthalten ist.
