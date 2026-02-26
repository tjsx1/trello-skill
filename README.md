# Trello Skill (Public)

Dieser Skill beschreibt, wie ein Agent Trello lesen und schreiben kann:
- Boards/Listen/Karten auslesen
- Karten erstellen/aktualisieren
- Karten zwischen Listen verschieben

## Voraussetzungen
Du brauchst folgende Trello-Zugangsdaten:

1. **API Key**
2. **API Secret**
3. **User Token** (mit mindestens `read,write` Scope)

## Empfohlene Ablage
Lege die Werte lokal in `memory/trello_creds.md.secret` ab (nicht committen), oder nutze Umgebungsvariablen:
- `TRELLO_API_KEY`
- `TRELLO_API_SECRET`
- `TRELLO_TOKEN`

## API Basis
- Base URL: `https://api.trello.com/1`
- Authentifizierung über Query-Parameter `key` und `token`

## Sicherheit
- **Nie** API Secret oder User Token in öffentliche Repositories committen.
- Für Public-Repos nur Skill-Doku ohne Credentials veröffentlichen.
