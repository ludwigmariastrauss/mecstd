# Blog – Admin-Anleitung

## Struktur

```
tests/blog/
├── index.html      → Startseite / Übersicht
├── post.html       → Einzelner Beitrag (via ?id=...)
├── submit.html     → Formular für Gastbeiträge
├── posts.json      → Alle Blog-Posts (hier pflegst du den Inhalt)
└── ADMIN.md        → Diese Datei
```

---

## GitHub Pages einrichten

1. Repository öffnen → **Settings** → **Pages**
2. Source: `main` Branch, Ordner: `/ (root)`
3. Speichern – GitHub erstellt automatisch eine URL wie:  
   `https://DEIN-USERNAME.github.io/DEIN-REPO/tests/blog/`

---

## `submit.html` konfigurieren

Öffne `submit.html` und passe Zeile mit `GITHUB_REPO` an:

```javascript
const GITHUB_REPO = 'DeinUsername/DeinRepo';
```

Ersetze `DeinUsername/DeinRepo` mit deinem echten GitHub-Pfad.

---

## Gastbeiträge genehmigen

### Workflow

1. Gast füllt das Formular aus
2. GitHub öffnet sich automatisch mit einem vorausgefüllten **Issue**
3. Du siehst das Issue im Tab **Issues** deines Repositories
4. Du prüfst den Inhalt
5. Bei Freigabe: füge den Beitrag in `posts.json` ein (s.u.)
6. Schließe das Issue mit Kommentar: „Veröffentlicht ✓"

### GitHub Label anlegen (einmalig)

Damit Gastbeiträge leicht zu finden sind, lege ein Label an:

1. Issues → **Labels** → **New label**
2. Name: `gastbeitrag`, Farbe: `#00e5a0`

---

## Neuen Post in `posts.json` einfügen

Öffne `posts.json` und füge oben in das Array einen neuen Eintrag ein:

```json
{
  "id": "003",
  "title": "Titel des Beitrags",
  "author": "Name des Autors",
  "date": "2026-05-20",
  "tags": ["IT", "Produktion"],
  "excerpt": "Kurze Zusammenfassung für die Übersichtsseite (1–2 Sätze).",
  "content": "Der vollständige Text des Beitrags.\n\n## Überschrift\n\nWeiterer Absatz.\n\n- Listenpunkt 1\n- Listenpunkt 2"
}
```

### Formatierung im `content`-Feld

| Syntax | Ergebnis |
|--------|----------|
| `\n\n` | Neuer Absatz |
| `## Titel` | Überschrift |
| `- Punkt` | Listenpunkt |

### IDs vergeben

Die `id` muss eindeutig sein – einfach fortlaufend nummerieren: `"001"`, `"002"`, `"003"` usw.

---

## Sortierung

Posts werden automatisch nach Datum sortiert (neueste zuerst). Das `date`-Feld im Format `YYYY-MM-DD` bestimmt die Reihenfolge.

---

## Tipps

- **Vorschau lokal:** Starte einen einfachen HTTP-Server im Projektordner:  
  ```bash
  python3 -m http.server 8080
  ```
  Dann: `http://localhost:8080/tests/blog/`

- **Gastbeiträge ablehnen:** Issue einfach schließen mit Kommentar – der Gast wird per GitHub-Notification informiert (falls er eingeloggt war).
