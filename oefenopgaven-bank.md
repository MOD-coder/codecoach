# Oefenopgaven-bank (met hints en oplossingen)

CodeCoach gebruikt deze opgaven als voorbeeld en genereert varianten op niveau. Oplossingen alleen op verzoek van de student tonen.


## Beginner


### B1 – FizzBuzz (Python)

Print de getallen 1 t/m 30. Bij veelvouden van 3 print je 'Fizz', van 5 'Buzz', van beide 'FizzBuzz'.

Hint: gebruik de modulo-operator % en controleer eerst de combinatie (15).

```
for i in range(1, 31):
    if i % 15 == 0: print("FizzBuzz")
    elif i % 3 == 0: print("Fizz")
    elif i % 5 == 0: print("Buzz")
    else: print(i)
```


### B2 – Temperatuur omrekenen

Vraag een temperatuur in Celsius en print Fahrenheit (F = C × 9/5 + 32). Vang ongeldige invoer af.

Hint: try/except ValueError rond float(input()).


### B3 – Woorden tellen

Tel hoe vaak elk woord voorkomt in een zin. Voorbeeld: 'de kat en de hond' → {'de': 2, 'kat': 1, 'en': 1, 'hond': 1}.

Hint: split() en een dictionary met .get(woord, 0) + 1.


### B4 – Getal raden

De computer kiest een getal 1–100; de speler raadt; geef 'hoger'/'lager' tot het klopt en tel de pogingen.

Hint: while-loop; random.randint.


### B5 – Even/oneven filter (JavaScript)

Schrijf een functie die uit een array alleen de even getallen teruggeeft. Hint: filter en %.


## Gemiddeld


### G1 – Bankrekening (OOP, Java/C#/Python)

Maak een klasse Bankrekening met saldo, storten(bedrag), opnemen(bedrag). Opnemen boven saldo geeft een fout; negatief bedrag is ongeldig. Schrijf 4 unit tests.

Hint: valideer eerst, wijzig daarna het saldo; gebruik een specifieke exceptie.

```
class Bankrekening:
    def __init__(self, saldo: float = 0):
        self._saldo = saldo
    @property
    def saldo(self): return self._saldo
    def storten(self, bedrag):
        if bedrag <= 0: raise ValueError("Bedrag moet positief zijn")
        self._saldo += bedrag
    def opnemen(self, bedrag):
        if bedrag <= 0: raise ValueError("Bedrag moet positief zijn")
        if bedrag > self._saldo: raise ValueError("Onvoldoende saldo")
        self._saldo -= bedrag
```


### G2 – Palindroom

Controleer of een zin een palindroom is, negeer spaties, leestekens en hoofdletters ('Meet systeem' → True).

Hint: filter op isalnum(), lower(), vergelijk met omgekeerde.


### G3 – CSV-rapport

Lees cijfers.csv (naam, vak, cijfer) en print per student het gemiddelde, gesorteerd van hoog naar laag.

Hint: csv.DictReader; dictionary naam → lijst cijfers; sorted met key.


### G4 – To-do API (REST)

Ontwerp endpoints voor een to-do lijst: lijst ophalen, item toevoegen, afvinken, verwijderen. Geef methode, pad, request- en responsevoorbeeld.

Hint: GET /todos, POST /todos, PATCH /todos/{id}, DELETE /todos/{id}; statuscodes 200/201/404.


### G5 – SQL-joins

Tabellen studenten(id, naam, klas_id), klassen(id, naam). Geef per klas het aantal studenten, ook klassen zonder studenten.

```
SELECT k.naam, COUNT(s.id) AS aantal
FROM klassen k
LEFT JOIN studenten s ON s.klas_id = k.id
GROUP BY k.naam
ORDER BY aantal DESC;
```


### G6 – Recursie: faculteit en Fibonacci

Implementeer beide recursief; leg uit waarom naïeve Fibonacci traag is en verbeter met memoization.


## Gevorderd


### V1 – Strategy pattern

Een webshop berekent verzendkosten per land met verschillende regels. Implementeer een Strategy-interface en drie strategieën; voeg een nieuwe strategie toe zonder bestaande code te wijzigen.


### V2 – Veilige login

Bouw registratie en login met gehashte wachtwoorden (bcrypt/argon2), geparametriseerde queries en rate limiting. Schrijf tests voor verkeerde wachtwoorden.


### V3 – Complexiteitsanalyse

Implementeer bubble sort en merge sort, meet de looptijd voor n = 1.000 / 10.000 / 100.000 en verklaar met Big-O.


### V4 – CI-pipeline

Voeg aan je project een GitHub Actions-workflow toe die bij elke push linting en tests draait; laat een PR bewust falen en repareer.


### V5 – Refactor-kata

Neem een functie van 80+ regels uit een eerder project en refactor naar functies van max. 20 regels zonder gedrag te veranderen; bewijs met tests.


## Zelftoets-vragen (per week te gebruiken)

- Leg in eigen woorden uit wat het concept van deze week doet en wanneer je het gebruikt.
- Geef een voorbeeld uit het dagelijks leven.
- Wat is de meest voorkomende fout en hoe herken je die?
- Schrijf uit je hoofd een minimaal voorbeeld van 5 regels.
