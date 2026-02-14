# Standard Features for All Web Apps

Denne fil beskriver standardfunktioner som skal implementeres i alle webapps.

---

## 1. Admin Tab (Developer Tools)

En skjult admin-fane til at lette udvikling og fejlfinding.

### Adgang
- Kun synlig for brugere med admin-rolle
- Tilgås via Settings eller en skjult gesture (f.eks. tryk 5x på versionsnummer)

### Clear Cache
- **Knap: "Clear Local Cache"** — rydder localStorage, sessionStorage og IndexedDB
- **Knap: "Clear Firestore Cache"** — rydder lokal Firestore-cache og tvinger ny hentning
- **Knap: "Hard Reload"** — rydder alt og genindlæser appen
- Vis bekræftelsesdialog før sletning

### Log / Debug Console
- In-app log-viewer der viser de seneste 200 log-entries
- Log-niveauer: `INFO`, `WARN`, `ERROR`
- Automatisk opfangning af:
  - API/Firestore kald (request + response tid)
  - Auth events (login, logout, token refresh)
  - Uventede fejl (JavaScript errors, unhandled promise rejections)
- Mulighed for at kopiere log til clipboard
- Mulighed for at eksportere log som .txt-fil
- Filtrer log efter niveau og søg i log-tekst

### Øvrige Admin-funktioner
- Vis app-version og build-info
- Vis aktuel brugers UID, rolle og auth-status
- Toggle feature flags (hvis relevant)

---

## 2. Feedback & Feature Requests (i Settings)

En sektion i Settings-skærmen hvor brugere kan foreslå nye features og stemme på andres forslag.

### Indsend Forslag
- Simpel formular med:
  - **Titel** (kort beskrivelse, maks 100 tegn)
  - **Beskrivelse** (uddybende tekst, valgfri, maks 500 tegn)
  - **Kategori** (dropdown: Bug, Feature, Forbedring, Andet)
- Forslaget gemmes i Firestore med brugerens UID og timestamp
- Brugeren kan se og redigere/slette egne forslag

### Feature Board (Oversigt)
- Liste over alle forslag sorteret efter antal stemmer (højest først)
- Hvert forslag viser:
  - Titel
  - Kategori-badge
  - Antal stemmer (upvotes)
  - Status-badge: `Ny`, `Under overvejelse`, `Planlagt`, `Implementeret`, `Afvist`
- Brugere kan trykke en upvote-knap (en stemme per bruger per forslag)
- Filtrering efter kategori og status

### Admin-håndtering
- Admin kan ændre status på forslag
- Admin kan svare/kommentere på forslag
- Admin kan markere duplikater

---

## Implementeringsnotes

- Brug Firestore-collection `feedback` til at gemme forslag
- Brug Firestore-collection `feedback_votes` til at tracke stemmer (forhindrer dobbelt-stemme)
- Admin-rollen bestemmes af et felt `role: "admin"` på brugerens Firestore-dokument
- Log-data gemmes kun lokalt (ikke i Firestore) for at bevare privatliv
- Feedback-boardet er synligt for alle brugere; admin-funktioner er kun synlige for admins
