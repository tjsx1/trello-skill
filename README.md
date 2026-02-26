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

## API Key / Secret erstellen
1. Öffne: `https://trello.com/power-ups/admin`
2. Einloggen (falls nötig)
3. Unten auf der Seite findest du deinen **API Key**
4. Das **API Secret** ist auf derselben Developer-Seite verfügbar

## User Token erstellen
1. Nutze diesen Link (ersetze `<API_KEY>`):
   `https://trello.com/1/authorize?expiration=never&name=OpenClaw&scope=read,write&response_type=token&key=<API_KEY>`
2. Klicke auf **Allow**
3. Kopiere den angezeigten **User Token**

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
