# Git-workflow voor studentprojecten


## Basisbegrippen

| Begrip | Betekenis |
|---|---|
| Repository (repo) | Map met je project en de volledige geschiedenis |
| Commit | Een opgeslagen 'foto' van je wijzigingen met een bericht |
| Branch | Een aparte lijn van ontwikkeling (bijv. feature/login) |
| Merge | Wijzigingen van de ene branch in de andere samenvoegen |
| Pull request (PR) | Verzoek om jouw branch te reviewen en te mergen |
| Remote (origin) | De online kopie op GitHub/Azure DevOps/GitLab |
| Clone / Pull / Push | Ophalen van een repo / laatste wijzigingen binnenhalen / jouw commits uploaden |


## Dagelijkse workflow (feature-branch)

```
git pull origin main                     # 1. begin up-to-date
git checkout -b feature/login-form       # 2. nieuwe branch
# ... werk aan je code ...
git status                               # 3. wat is er veranderd?
git add .                                # 4. wijzigingen klaarzetten
git commit -m "feat: voeg loginformulier toe met validatie"   # 5. commit
git push -u origin feature/login-form    # 6. naar remote
# 7. open een pull request → review → merge in main
git checkout main && git pull            # 8. terug naar main en bijwerken
```


## Commit-berichten (Conventional Commits)

- Formaat: type: korte beschrijving in de tegenwoordige tijd (max. 72 tekens).
- Types: feat (nieuwe functie), fix (bugfix), docs, style, refactor, test, chore.
- Voorbeelden: feat: voeg zoekfunctie toe aan boekenlijst · fix: voorkom crash bij lege invoer · test: voeg tests toe voor Bankrekening.
- Commit klein en vaak: één logische wijziging per commit.


## Branch-afspraken voor teams

- main is altijd werkend; nooit direct op main committen.
- Branchnamen: feature/<naam>, fix/<naam>, docs/<naam>.
- Elke PR heeft minimaal 1 reviewer; reviewer gebruikt de Code-Review-Checklist.
- Verwijder de branch na de merge.
- .gitignore bevat: venv/, node_modules/, bin/, obj/, .env, *.log, .vs/, .idea/.


## Merge conflicts oplossen

1. git pull of merge meldt CONFLICT; open het bestand.
2. Zoek de markeringen <<<<<<< HEAD (jouw versie), ======= en >>>>>>> (andere versie).
3. Kies of combineer de juiste code en verwijder de markeringen.
4. Test of het programma nog werkt.
5. git add <bestand> en git commit om de merge af te ronden.
6. Voorkom conflicten: pull vaak, werk in kleine branches, spreek af wie aan welk bestand werkt.


## Handige commando's

| Doel | Commando |
|---|---|
| Geschiedenis bekijken | git log --oneline --graph --all |
| Verschil zien | git diff |
| Laatste commit aanpassen (niet gepusht) | git commit --amend |
| Wijziging ongedaan maken in werkmap | git restore <bestand> |
| Bestand uit staging halen | git restore --staged <bestand> |
| Commit terugdraaien met nieuwe commit | git revert <hash> |
| Tijdelijk werk opzij zetten | git stash / git stash pop |
| Branch verwijderen | git branch -d feature/x |


## Pull request-checklist

- Titel en beschrijving: wat en waarom; link naar issue/user story.
- Alle tests slagen; nieuwe code heeft tests.
- Geen secrets, geen debug-prints, geen uitgecommentarieerde code.
- README/documentatie bijgewerkt indien nodig.
- Kleine PR (< 400 regels) zodat review haalbaar is.
