# Coderichtlijnen voor studenten

Deze richtlijnen gebruikt CodeCoach bij code reviews. Vervang of vul aan met de richtlijnen van je opleiding.


## 1. Algemene principes

- Leesbaarheid boven slimheid: code wordt vaker gelezen dan geschreven.
- Kleine functies met één verantwoordelijkheid (max. ± 20–30 regels).
- Betekenisvolle namen: een naam vertelt wat iets is of doet (aantalStudenten, berekenTotaal()).
- Geen magic numbers: gebruik constanten (MAX_POGINGEN = 3).
- DRY – Don't Repeat Yourself: herhaalde code wordt een functie.
- KISS – Keep It Simple: kies de eenvoudigste oplossing die werkt.
- Fouten netjes afhandelen: nooit lege catch/except-blokken.
- Geen wachtwoorden, API-keys of verbindingsstrings in code; gebruik omgevingsvariabelen of een .env-bestand dat in .gitignore staat.


## 2. Naamgeving per taal

| Taal | Variabelen/functies | Klassen | Constanten | Bestanden |
|---|---|---|---|---|
| Python | snake_case (bereken_totaal) | PascalCase (Bankrekening) | UPPER_SNAKE (MAX_POGINGEN) | snake_case.py |
| Java | camelCase (berekenTotaal) | PascalCase | UPPER_SNAKE | PascalCase.java (één publieke klasse per bestand) |
| C# | camelCase lokaal; PascalCase methoden/properties | PascalCase | PascalCase of UPPER_SNAKE | PascalCase.cs |
| JavaScript/TypeScript | camelCase | PascalCase | UPPER_SNAKE | kebab-case.js of camelCase.js |
| SQL | snake_case tabellen en kolommen (student_id) | — | — | — |


## 3. Structuur en opmaak

- Gebruik de standaardformatter: Python → black/PEP 8, Java → Google Java Style, C# → dotnet format, JS/TS → Prettier.
- Eén statement per regel; consistente inspringing (4 spaties Python/Java/C#, 2 spaties JS).
- Imports bovenaan, gegroepeerd (standaardbibliotheek, externe pakketten, eigen modules).
- Maximaal ± 100 tekens per regel.
- Scheid logica (berekeningen) van presentatie (print/UI) en data-toegang.


## 4. Commentaar en documentatie

- Commentaar legt WAAROM uit, niet WAT (de code zelf laat zien wat er gebeurt).
- Elke publieke functie/klasse krijgt een docstring/JavaDoc/XML-doc met doel, parameters en returnwaarde.
- Verwijder uitgecommentarieerde code voordat je commit.
- Een README beschrijft: doel, installatie, gebruik, structuur, auteurs (zie README-template).


## 5. Foutafhandeling

- Vang alleen fouten die je kunt afhandelen; laat andere netjes doorgeven.
- Geef de gebruiker een begrijpelijke melding, log de technische details.
- Valideer invoer aan de rand van je programma (gebruikersinvoer, bestanden, API's).
- Gebruik specifieke exceptietypen (ValueError, FileNotFoundError) in plaats van alles vangen.


## 6. Veiligheid (minimum)

- Gebruik altijd geparametriseerde queries (nooit SQL samenstellen met string-concatenatie).
- Hash wachtwoorden (bcrypt/argon2), sla ze nooit in platte tekst op.
- Valideer en escape gebruikersinvoer in webapplicaties (XSS).
- Houd afhankelijkheden up-to-date; controleer op bekende kwetsbaarheden.
- Secrets nooit in Git; gebruik .gitignore en een voorbeeldbestand (.env.example).


## 7. Testbaarheid

- Schrijf functies die een waarde teruggeven in plaats van direct printen.
- Vermijd globale state; geef afhankelijkheden mee als parameters.
- Elke bugfix krijgt een test die de bug reproduceert.


## 8. Voorbeeld: vóór en na

```
# Vóór
def f(l):
    t=0
    for i in l:
        if i>0: t=t+i
    return t

# Na
def som_positieve_getallen(getallen: list[float]) -> float:
    """Telt alleen de positieve getallen uit de lijst op."""
    return sum(g for g in getallen if g > 0)
```
