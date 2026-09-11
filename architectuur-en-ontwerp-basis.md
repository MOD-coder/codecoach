# Architectuur en ontwerp – basis voor studentprojecten


## Van idee naar ontwerp in 5 stappen

1. Probleem en doelgroep in 2 zinnen.
2. User stories met acceptatiecriteria (MoSCoW).
3. Domeinmodel: welke 'dingen' zijn er (Student, Cursus, Inschrijving) en hoe hangen ze samen?
4. Technische keuzes: taal, framework, database, hosting – met één zin waarom.
5. Walking skeleton: kleinste werkende keten van UI → logica → data.


## Lagenarchitectuur (voor de meeste schoolprojecten)

| Laag | Verantwoordelijkheid | Voorbeeld |
|---|---|---|
| Presentatie (UI/API) | Invoer ontvangen, uitvoer tonen | Flask/FastAPI routes, Razor pages, React |
| Logica (services/domein) | Regels en berekeningen | InschrijvingService.schrijfIn() |
| Data (repositories) | Opslaan en ophalen | StudentRepository met SQL/ORM |

Regel: een laag praat alleen met de laag eronder. Logica bevat geen print/HTML en geen SQL.


## Klassendiagram in tekst (Mermaid)

```
classDiagram
  class Student { +int id +string naam +schrijfIn(Cursus) }
  class Cursus { +int id +string titel +int maxPlaatsen }
  class Inschrijving { +date datum +Status status }
  Student "1" --> "*" Inschrijving
  Cursus "1" --> "*" Inschrijving
```


## ERD in tekst

```
studenten(id PK, naam, email UNIQUE)
cursussen(id PK, titel, max_plaatsen)
inschrijvingen(id PK, student_id FK→studenten.id, cursus_id FK→cursussen.id, datum, status)
```


## REST API-ontwerp

| Actie | Methode + pad | Status |
|---|---|---|
| Alle cursussen | GET /cursussen | 200 |
| Eén cursus | GET /cursussen/{id} | 200 / 404 |
| Cursus aanmaken | POST /cursussen | 201 |
| Cursus wijzigen | PUT of PATCH /cursussen/{id} | 200 |
| Cursus verwijderen | DELETE /cursussen/{id} | 204 |
| Inschrijven | POST /cursussen/{id}/inschrijvingen | 201 / 409 (vol) |

- Zelfstandige naamwoorden in het meervoud; geen werkwoorden in paden.
- JSON in en uit; consistente foutstructuur {"error": "..."}.
- Versie in pad (/api/v1) als het een extern gebruikte API is.


## Design patterns die studenten vaak nodig hebben

| Pattern | Wanneer | Voorbeeld |
|---|---|---|
| Strategy | Verschillende regels voor hetzelfde doel | Verzendkosten per land |
| Factory | Objecten maken op basis van invoer | Maak juiste Betaalmethode |
| Observer | Meerdere onderdelen reageren op een gebeurtenis | UI updaten bij nieuwe score |
| Repository | Data-toegang scheiden van logica | StudentRepository |
| Singleton (voorzichtig) | Precies één instantie | Configuratie – liever dependency injection |


## SOLID in één zin per letter

- S – Een klasse heeft één reden om te veranderen.
- O – Uitbreiden zonder bestaande code te wijzigen.
- L – Een subklasse moet overal werken waar de superklasse werkt.
- I – Liever meerdere kleine interfaces dan één grote.
- D – Hang af van abstracties (interfaces), niet van concrete klassen.


## Architectuurbeslissing vastleggen (ADR-mini)

```
# ADR-001: Keuze database
Context: kleine webapp, 1 team, geen serverbeheer.
Beslissing: SQLite in ontwikkeling, PostgreSQL in productie via ORM.
Gevolgen: eenvoudig starten; migraties nodig; ORM leren.
```
