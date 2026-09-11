# Projectplanning – templates


## User story-template

```
Als <rol> wil ik <doel/actie> zodat <waarde/reden>.

Acceptatiecriteria (Given/When/Then):
- Gegeven <situatie>, wanneer <actie>, dan <resultaat>.
- ...
Prioriteit (MoSCoW): Must / Should / Could / Won't
Schatting: S / M / L (of story points)
```

Voorbeeld: Als student wil ik mijn boodschappenlijst kunnen opslaan, zodat ik hem later weer kan openen. Gegeven een lijst met items, wanneer ik op Opslaan klik, dan staat de lijst in lijst.json en zie ik 'Opgeslagen'.


## MoSCoW-prioritering

| Categorie | Betekenis | Vuistregel |
|---|---|---|
| Must have | Zonder dit is het project mislukt | Max. 60% van de tijd |
| Should have | Belangrijk, maar er is een workaround | ± 20% |
| Could have | Leuk als er tijd over is | ± 20% |
| Won't have (nu) | Bewust buiten scope | Vastleggen om discussie te voorkomen |


## Definition of Done (voorbeeld)

- Code voldoet aan de coderichtlijnen.
- Unit tests geschreven en groen.
- Gereviewd door een teamgenoot via PR.
- Gemerged in main.
- Documentatie/README bijgewerkt.
- Gedemonstreerd aan de product owner/docent.


## Sprint-template (2 weken)

| Onderdeel | Inhoud |
|---|---|
| Sprintdoel | Eén zin: wat kan de gebruiker aan het eind? |
| Geselecteerde user stories | Lijst met MoSCoW en schatting |
| Taakverdeling | Wie doet wat; max. 2 taken per persoon tegelijk |
| Risico's | Wat kan misgaan en wat doen we dan? |
| Ceremonies | Daily stand-up (15 min), review, retrospective |


## Daily stand-up (3 vragen)

- Wat heb ik gisteren gedaan?
- Wat ga ik vandaag doen?
- Waar loop ik vast?


## Retrospective-template

- Wat ging goed? (behouden)
- Wat ging minder? (stoppen)
- Wat gaan we anders doen? (starten) – maximaal 2 concrete acties met eigenaar


## Planning van een schoolproject in 4 sprints (8 weken)

| Sprint | Focus | Oplevering |
|---|---|---|
| 1 | Requirements, user stories, ontwerp (ERD/klassendiagram), repo opzetten, walking skeleton | Werkend 'hello world' van de hele keten |
| 2 | Must-haves bouwen | Kernfunctionaliteit met tests |
| 3 | Must-haves afronden, should-haves, integratie | Demo-versie |
| 4 | Could-haves, bugfixes, documentatie, presentatie | Eindproduct + verslag + presentatie |


## Risico-checklist

- Te grote scope → MoSCoW strak houden.
- Teamlid valt uit → kennis delen via PR-reviews en documentatie.
- Techniek te nieuw → spike van max. 1 dag, daarna beslissen.
- Laat beginnen met integratie → walking skeleton in sprint 1.
