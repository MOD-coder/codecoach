# Debug-methode en veelvoorkomende foutmeldingen


## De 6-stappen debug-methode

1. LEES de foutmelding volledig: type, boodschap, bestand en regelnummer. Begin bij de laatste regel van de stacktrace en werk omhoog.
2. REPRODUCEER: bij welke invoer gaat het mis? Maak het kleinste voorbeeld dat de fout laat zien.
3. HYPOTHESE: wat denk je dat er misgaat? Formuleer het in één zin.
4. TEST de hypothese: voeg een print/log of breakpoint toe en controleer de waarde van variabelen.
5. ISOLEER: comment code uit of splits de functie tot je de exacte regel hebt.
6. FIX en VERIFIEER: los het op, draai je tests en leg in één zin vast wat de oorzaak was.


## Vragen die CodeCoach stelt

- Wat is de exacte foutmelding (kopieer de hele tekst)?
- Welke regel code hoort bij het regelnummer?
- Wat verwachtte je dat er zou gebeuren en wat gebeurde er?
- Wat heb je als laatste veranderd?
- Met welke invoer gaat het wél goed?


## Veelvoorkomende fouten – Python

| Foutmelding | Betekenis | Waar zoek je |
|---|---|---|
| SyntaxError: invalid syntax | Typfout in de code (vergeten dubbele punt, haakje, aanhalingsteken) | Regel vóór of op het regelnummer |
| IndentationError | Inspringing klopt niet | Mix van tabs en spaties; blok na if/for/def |
| NameError: name 'x' is not defined | Variabele of functie bestaat (nog) niet | Typfout in naam; definitie staat lager; scope |
| TypeError: unsupported operand / can only concatenate str | Datatypes passen niet bij elkaar | str + int → gebruik str() of f-string |
| ValueError: invalid literal for int() | Conversie van tekst naar getal mislukt | Gebruikersinvoer valideren met try/except |
| IndexError: list index out of range | Index buiten de lijst | Off-by-one; lengte controleren; range(len(lijst)) |
| KeyError | Sleutel bestaat niet in dictionary | Gebruik .get() of controleer met in |
| AttributeError: 'NoneType' object has no attribute | Variabele is None | Functie zonder return; mislukte zoekopdracht |
| ModuleNotFoundError | Pakket niet geïnstalleerd of verkeerde omgeving | pip install; juiste virtual environment |
| ZeroDivisionError | Delen door nul | Controleer de deler vóór de deling |
| RecursionError | Recursie zonder (bereikbare) basisgeval | Controleer de stopconditie |


## Veelvoorkomende fouten – Java

| Foutmelding | Betekenis | Waar zoek je |
|---|---|---|
| cannot find symbol | Naam onbekend: typfout, ontbrekende import of declaratie | Import; hoofdletters; scope |
| incompatible types | Type klopt niet met declaratie | Casten of type aanpassen |
| NullPointerException | Object is null | Initialisatie; return null; Optional gebruiken |
| ArrayIndexOutOfBoundsException | Index buiten array | Off-by-one; array.length - 1 |
| ClassCastException | Ongeldige cast | instanceof controleren |
| NumberFormatException | Tekst → getal mislukt | Invoer valideren |
| ConcurrentModificationException | Lijst aangepast tijdens iteratie | Iterator.remove of kopie maken |
| missing return statement | Niet elk pad geeft een waarde terug | Return in alle takken |


## Veelvoorkomende fouten – C#

| Foutmelding | Betekenis | Waar zoek je |
|---|---|---|
| CS0103 The name does not exist | Onbekende naam | Typfout; using; scope |
| CS0029 Cannot implicitly convert type | Typeconversie | Cast, Parse, ToString |
| NullReferenceException | Object is null | Initialisatie; ?. operator; null-checks |
| IndexOutOfRangeException | Index buiten array/lijst | Count - 1; loopgrenzen |
| InvalidCastException | Ongeldige cast | as/is gebruiken |
| FormatException | Parse mislukt | int.TryParse gebruiken |
| CS1002 ; expected | Puntkomma vergeten | Regel ervoor |


## Veelvoorkomende fouten – JavaScript/TypeScript

| Foutmelding | Betekenis | Waar zoek je |
|---|---|---|
| ReferenceError: x is not defined | Variabele bestaat niet | Typfout; let/const vergeten; scope |
| TypeError: Cannot read properties of undefined | Object/element is undefined | querySelector vond niets; async data nog niet geladen |
| TypeError: x is not a function | Aanroep van iets dat geen functie is | Naam; import; this-binding |
| SyntaxError: Unexpected token | Typfout, vergeten haakje/komma | JSON.parse op ongeldige JSON |
| Uncaught (in promise) | Fout in async code zonder catch | try/await/catch toevoegen |
| CORS error | Browser blokkeert API-call | Server-configuratie; proxy; niet omzeilen in productie |
| TS2322 Type is not assignable | Typefout in TypeScript | Types aanpassen of interface uitbreiden |


## Debug-gereedschap

- Print/console.log met duidelijke labels: print(f"DEBUG saldo={saldo}")
- Breakpoints en stap-voor-stap in VS Code / Visual Studio / IntelliJ
- Rubber duck debugging: leg de code regel voor regel uit aan CodeCoach
- Unit test schrijven die de fout reproduceert
