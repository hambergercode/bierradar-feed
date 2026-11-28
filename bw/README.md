# Bierradar Baden-Württemberg

Ableger des Bierradars für Baden-Württemberg. Er läuft getrennt vom österreichischen Bierradar und lässt sich einzeln ein- und ausschalten.

## Dateien

| Datei | Zweck |
|---|---|
| `bierradar-bw-feed.json` | Aktionen, Händler-Rabatte und Stand. Wird täglich von der geplanten Aufgabe „Bierradar BW aktualisieren“ neu geschrieben. |
| `web/index.html` | Seite für den Server. Liest den Feed direkt von GitHub (`raw.githubusercontent.com`), braucht kein PHP und keine Datenbank. |

## Auf hamberger.me veröffentlichen

1. `web/index.html` nach `/bier/bw/index.html` hochladen.
2. Fertig: Die Seite holt sich Theme (`../assets/app.css`), Schriften und Logo (`../assets/favicon.svg`) vom österreichischen Bierradar und die Daten aus dem Feed.
3. Optional im österreichischen Bierradar in der Navigation einen Link `bw/` mit dem Text „Baden-Württemberg“ ergänzen.

Liegt die Seite woanders als unter `/bier/bw/`, müssen die Pfade `../assets/…` und der Link „Österreich“ (`../`) in `index.html` angepasst werden.

## Ein- und ausschalten

Der Schalter ist das Feld `meta.active` (true/false).

- **Am einfachsten:** Im Artefakt „Bierradar Baden-Württemberg“ unten auf „Bierradar BW deaktivieren“ bzw. „wieder aktivieren“ klicken (nur für Bearbeiter sichtbar). Die tägliche Aktualisierung übernimmt den Schalter beim nächsten Lauf in diesen Feed; die Server-Seite zeigt dann statt der Aktionen einen Hinweis.
- **Sofort auf dem Server:** in `bierradar-bw-feed.json` `"active": false` setzen und committen (wirkt nach wenigen Minuten, aber nur bis zur nächsten täglichen Aktualisierung; dauerhaft gilt der Schalter im Artefakt).
- **Ganz stoppen:** die geplante Aufgabe „Bierradar BW aktualisieren“ pausieren und/oder `/bier/bw/` vom Server löschen. Der österreichische Bierradar und seine Aufgabe „bier-aktuell“ sind davon nicht betroffen.
