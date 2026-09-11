# Security-basis voor studentprojecten (OWASP Top 10 in gewone taal)

Gebaseerd op de OWASP Top 10-categorieën; raadpleeg owasp.org voor de actuele lijst en details.

| Risico | Wat is het | Hoe voorkom je het in je project |
|---|---|---|
| Broken Access Control | Gebruikers kunnen dingen zien/doen die niet mogen | Controleer rechten server-side bij elke request; deny by default |
| Cryptographic Failures | Gevoelige data slecht beschermd | HTTPS; wachtwoorden hashen (bcrypt/argon2); geen eigen crypto |
| Injection | Invoer wordt als code uitgevoerd (SQL, OS, LDAP) | Geparametriseerde queries/ORM; invoer valideren |
| Insecure Design | Beveiliging niet meegenomen in ontwerp | Threat modeling: wat kan misgaan? Denk bij elke user story aan misbruik |
| Security Misconfiguration | Standaardwachtwoorden, debug aan, open poorten | Debug uit in productie; secrets in env; least privilege |
| Vulnerable Components | Verouderde libraries met bekende lekken | Dependabot/npm audit/pip-audit; regelmatig updaten |
| Identification & Authentication Failures | Zwakke login, sessies | Sterk wachtwoordbeleid, rate limiting, MFA waar mogelijk, veilige sessiecookies |
| Software & Data Integrity Failures | Onbetrouwbare updates/pipelines | Alleen vertrouwde pakketbronnen; CI met gecontroleerde acties |
| Logging & Monitoring Failures | Aanvallen worden niet opgemerkt | Log logins en fouten (zonder gevoelige data); bekijk logs |
| Server-Side Request Forgery | Server haalt URL's op die de aanvaller kiest | Whitelist van toegestane hosts; valideer URL's |


## Veilige code – voorbeeld injectie

```
# ONVEILIG
cursor.execute(f"SELECT * FROM users WHERE naam = '{naam}'")

# VEILIG (geparametriseerd)
cursor.execute("SELECT * FROM users WHERE naam = ?", (naam,))
```


## Secrets beheren

```
# .env (NIET in Git)      # .env.example (WEL in Git)
DB_PASSWORD=geheim123      DB_PASSWORD=
API_KEY=abc                API_KEY=

# Python
import os
from dotenv import load_dotenv
load_dotenv()
wachtwoord = os.getenv("DB_PASSWORD")
```


## Security-checklist vóór inleveren

- Geen secrets in repo (controleer geschiedenis).
- Alle queries geparametriseerd.
- Wachtwoorden gehasht.
- Invoer gevalideerd; output ge-escaped.
- Afhankelijkheden gescand.
- Rechtencontrole op elke gevoelige actie.
- Foutmeldingen lekken geen technische details naar de gebruiker.


## Ethiek

Test alleen systemen waarvoor je expliciete toestemming hebt (eigen project, oefenomgevingen zoals OWASP Juice Shop). CodeCoach helpt niet bij het aanvallen van systemen van anderen.
