# Trello Skill

## Zweck
Zugriff auf Trello mit **Lesen + Schreiben**:
- Boards / Lists / Cards auslesen
- Karten erstellen und aktualisieren
- Karten zwischen Listen verschieben
- Labels, Due-Dates, Members setzen

## Credentials
Lade Credentials aus:
`memory/trello_creds.md.secret`

Alternativ über Umgebungsvariablen:
- `TRELLO_API_KEY`
- `TRELLO_API_SECRET`
- `TRELLO_TOKEN`

Benötigt:
- `api_key`
- `token`

`api_secret` ist optional für manche Flows, für Standard-REST-Aufrufe reichen Key+Token.

## API-Basis
- Base URL: `https://api.trello.com/1`
- Auth immer als Query-Parameter: `key=<api_key>&token=<token>`

## Standard-Workflow
1. **Board finden**
   - `GET /members/me/boards?fields=name,url,id`
2. **Listen eines Boards laden**
   - `GET /boards/{boardId}/lists?fields=name,id,pos,closed`
3. **Cards einer Liste laden**
   - `GET /lists/{listId}/cards?fields=name,desc,idList,idLabels,due,url`
4. **Card erstellen**
   - `POST /cards` mit `idList`, `name`, optional `desc`, `due`, `idMembers`, `idLabels`
5. **Card updaten**
   - `PUT /cards/{cardId}` (z. B. `name`, `desc`, `due`, `closed`)
6. **Card verschieben**
   - `PUT /cards/{cardId}` mit neuem `idList` (optional `pos`)

## Häufige Aktionen (Beispiele)

### Karte erstellen
`POST /cards?idList=<LIST_ID>&name=<TITLE>&desc=<DESC>&key=<KEY>&token=<TOKEN>`

### Karte in andere Liste schieben
`PUT /cards/<CARD_ID>?idList=<TARGET_LIST_ID>&key=<KEY>&token=<TOKEN>`

### Due Date setzen
`PUT /cards/<CARD_ID>?due=2026-03-01T12:00:00.000Z&key=<KEY>&token=<TOKEN>`

### Label hinzufügen
`POST /cards/<CARD_ID>/idLabels?value=<LABEL_ID>&key=<KEY>&token=<TOKEN>`

## Regeln
- Nie Secret/Token im User-Chat posten.
- Vor Schreibaktionen möglichst kurz validieren (Board/List/Card existiert).
- Bei Mehrdeutigkeit (gleiche Listennamen) IDs bevorzugen.
- Änderungen kurz bestätigen (was wurde wo geändert).

## Fehlerbehandlung
- `401 unauthorized`: Token prüfen/neu erzeugen.
- `400 invalid value`: meist falsche ID oder Feldname.
- `404`: Objekt (Board/List/Card) nicht gefunden oder kein Zugriff.
