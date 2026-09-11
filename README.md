# CodeCoach Kennisbank (publieke site)

Publieke leerbronnen software development – kennisbron voor de agent *CodeCoach – Leer programmeren* (Copilot Chat, ongemeterd).

## Publiceren op GitHub Pages
1. Maak een repository, bijv. `codecoach`, en zet deze bestanden in de root (of map `docs/`).
2. Settings → Pages → Source: *Deploy from a branch* → branch `main`, map `/ (root)`.
3. De site komt op `https://<organisatie>.github.io/codecoach/` – deze URL voeg je toe als website-kennisbron in Agent Builder.
4. Controleer dat de site publiek bereikbaar is (geen login) en geen vertrouwelijk materiaal bevat.

Alternatief: plaats `index.html`, `style.css` en de map `docs/` op de openbare website van de opleiding.

## Inhoud
- [Leerpaden software development](docs/leerpaden.md)
- [Coderichtlijnen voor studenten](docs/coderichtlijnen.md)
- [Debug-methode en veelvoorkomende foutmeldingen](docs/debug-methode.md)
- [Git-workflow voor studentprojecten](docs/git-workflow.md)
- [Code-review checklist](docs/code-review-checklist.md)
- [Testen – basis voor studenten](docs/testen-basis.md)
- [Projectplanning – templates](docs/project-planning-templates.md)
- [README-template](docs/readme-template.md)
- [Begrippenlijst software development](docs/begrippenlijst.md)
- [AI-gebruik en academische integriteit – beleid (template)](docs/ai-gebruik-en-integriteit.md)
- [Veelgestelde vragen van studenten](docs/veelgestelde-vragen.md)
- [Prompt-gids: zo haal je het meeste uit CodeCoach](docs/prompt-gids-voor-studenten.md)
- [Oefenopgaven-bank (met hints en oplossingen)](docs/oefenopgaven-bank.md)
- [Skills-overzicht CodeCoach (Basic en Pro)](docs/skills-overzicht-codecoach.md)
- [Security-basis voor studentprojecten (OWASP Top 10 in gewone taal)](docs/security-basis-owasp.md)
- [Architectuur en ontwerp – basis voor studentprojecten](docs/architectuur-en-ontwerp-basis.md)

`docs/*.md` zijn dezelfde teksten in Markdown (voor wiki's, LMS of Docusaurus). `docs/*.html` zijn de weergegeven pagina's.

## Aanpassen
Zoek op `[` voor placeholders (o.a. in *AI-gebruik en academische integriteit*) en vul ze in vóór publicatie.
