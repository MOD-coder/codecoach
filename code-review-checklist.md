# Code-review checklist

CodeCoach gebruikt deze checklist voor reviews en geeft maximaal 5 verbeterpunten, geprioriteerd van belangrijk naar minder belangrijk.


## Prioriteit 1 – Correctheid

- Doet de code wat de opdracht/user story vraagt?
- Worden randgevallen afgehandeld (leeg, nul, negatief, heel groot, ongeldige invoer)?
- Zijn er off-by-one fouten in loops en indexen?
- Klopt de logica van condities (and/or, ==/=, </<=)?


## Prioriteit 2 – Veiligheid

- Geen secrets in code of repo.
- Geparametriseerde queries; geen SQL-injectie.
- Invoer gevalideerd en (voor web) ge-escaped.
- Wachtwoorden gehasht.
- Geen gevoelige data in logs.


## Prioriteit 3 – Leesbaarheid en structuur

- Duidelijke namen volgens de coderichtlijnen.
- Functies klein, één verantwoordelijkheid.
- Geen duplicatie.
- Consistent geformatteerd.
- Commentaar legt het waarom uit; geen dode code.


## Prioriteit 4 – Foutafhandeling

- Specifieke excepties; geen lege catch-blokken.
- Begrijpelijke foutmeldingen voor de gebruiker.
- Resources netjes gesloten (with / using / try-with-resources).


## Prioriteit 5 – Testen en onderhoudbaarheid

- Zijn er tests voor de belangrijkste paden en randgevallen?
- Is de code testbaar (geen verborgen afhankelijkheden)?
- Is de README/documentatie bijgewerkt?


## Prioriteit 6 – Performance (alleen als relevant)

- Onnodige geneste loops (O(n²)) waar een dictionary/set volstaat?
- Herhaalde databasequeries in een loop (N+1)?
- Grote bestanden volledig in geheugen laden waar streaming kan?


## Feedback-formaat

```
1. [Correctheid] Lege lijst geeft ZeroDivisionError in gemiddelde() – controleer len(getallen) == 0 en geef 0 of raise ValueError.
   Waarom: voorkomt crash bij een gebruiker zonder cijfers.
2. [Leesbaarheid] Variabele 'x' → 'totaal_cijfers'.
   Waarom: de naam maakt de bedoeling duidelijk zonder commentaar.
Sterk punt: goede scheiding van invoer en berekening.
```


## Toon van feedback

- Begin met wat goed is.
- Formuleer als vraag of suggestie: 'Wat gebeurt er als de lijst leeg is?'
- Gericht op code, niet op de persoon.
- Eén verbetering per punt, met voorbeeld.
