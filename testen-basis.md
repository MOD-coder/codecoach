# Testen – basis voor studenten


## Waarom testen

- Je weet zeker dat je code werkt – ook na wijzigingen.
- Tests documenteren wat de code moet doen.
- Bugs vind je vroeger, dus goedkoper.


## Soorten tests

| Soort | Wat | Voorbeeld |
|---|---|---|
| Unit test | Eén functie/klasse geïsoleerd | bereken_btw(100) == 21 |
| Integratietest | Meerdere onderdelen samen | Opslaan in database en weer ophalen |
| End-to-end / acceptatietest | Hele applicatie vanuit gebruiker | Inloggen en een bestelling plaatsen |
| Regressietest | Controleert dat oude bugs niet terugkomen | Test die bug #42 reproduceert |


## AAA-patroon

- Arrange: zet de testsituatie op.
- Act: voer de actie uit.
- Assert: controleer het resultaat.


## Testcases afleiden uit acceptatiecriteria

User story: 'Als student wil ik mijn gemiddelde cijfer zien zodat ik weet of ik geslaagd ben.' Acceptatiecriteria → testcases:

| Criterium | Testcase | Verwacht |
|---|---|---|
| Gemiddelde van cijfers | [7, 8, 9] | 8.0 |
| Geen cijfers | [] | 0 of duidelijke fout |
| Eén cijfer | [6] | 6.0 |
| Afronding | [7, 8] | 7.5 |
| Ongeldig cijfer | [11] | ValueError |


## Voorbeelden per taal


### Python – pytest

```
# test_cijfers.py
import pytest
from cijfers import gemiddelde

def test_gemiddelde_normaal():
    assert gemiddelde([7, 8, 9]) == 8.0

def test_gemiddelde_leeg_geeft_nul():
    assert gemiddelde([]) == 0

def test_ongeldig_cijfer():
    with pytest.raises(ValueError):
        gemiddelde([11])
# uitvoeren: pytest -v
```


### Java – JUnit 5

```
@Test
void gemiddeldeNormaal() {
    assertEquals(8.0, Cijfers.gemiddelde(List.of(7, 8, 9)), 0.001);
}
@Test
void ongeldigCijferGeeftException() {
    assertThrows(IllegalArgumentException.class, () -> Cijfers.gemiddelde(List.of(11)));
}
```


### C# – xUnit

```
[Fact]
public void Gemiddelde_Normaal_Geeft8()
{
    Assert.Equal(8.0, Cijfers.Gemiddelde(new[] { 7, 8, 9 }));
}
[Theory]
[InlineData(new int[] { 6 }, 6.0)]
[InlineData(new int[] { 7, 8 }, 7.5)]
public void Gemiddelde_MeerdereGevallen(int[] input, double verwacht)
{
    Assert.Equal(verwacht, Cijfers.Gemiddelde(input));
}
```


### JavaScript – Jest

```
test('gemiddelde van 7, 8, 9 is 8', () => {
  expect(gemiddelde([7, 8, 9])).toBe(8);
});
test('lege lijst geeft 0', () => {
  expect(gemiddelde([])).toBe(0);
});
```


## Goede tests

- Eén ding per test; duidelijke naam die het gedrag beschrijft.
- Onafhankelijk van volgorde en van elkaar.
- Snel; geen echte netwerk/database in unit tests (gebruik mocks/fakes).
- Test randgevallen expliciet.
- Tests draaien in CI bij elke push (GitHub Actions).


## Minimale GitHub Actions-workflow (Python)

```
name: tests
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with: { python-version: '3.12' }
      - run: pip install -r requirements.txt pytest
      - run: pytest
```
