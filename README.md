# VakkenPakket

Webtool waarmee leerlingen van klas 3 van gymnasium Haganum hun vakkenpakket samenstellen: eerst het profiel en de vakken voor klas 4, daarna de definitieve keuze voor klas 5 en 6. De tool laat live zien welke vakken doorlopen, welke na klas 4 afvallen en welke in klas 5 nieuw zijn. Bij elk vak staat achtergrondinformatie.

Het is één statische pagina (`index.html`) zonder build-stap of server.

## Gebruiken

Open `index.html` in een browser. Om de tool online te zetten, kun je het bestand op elke statische host plaatsen, zoals GitHub Pages, Netlify of de webserver van school.

Keuzes worden alleen in de browser van de leerling bewaard (`localStorage`) en nergens naartoe gestuurd.

Klas 5 wordt automatisch ingevuld met de keuzes uit klas 4. Wat de leerling in klas 5 zelf aanpast, blijft staan. De knop "Zet terug naar klas 4" laat alles weer de keuzes uit klas 4 volgen.

Onder "Keuze doorgeven" vult de leerling naam en klas in. Daarna kan die de keuze als nette mail openen in het eigen mailprogramma (via een `mailto:`-link), of de tekst kopiëren en zelf in een mail plakken. Zet het adres van de decaan in de constante `MAIL_TO` in `index.html`; is die leeg, dan vult de leerling het adres zelf in.

## Bronnen

- Haganum-schema "Profielkeuze klas 4": 11 vakken.
- Haganum-schema "Definitieve vakkenkeuze voor klas 5 en 6": 10 vakken.
- De vakinformatie is algemeen en komt uit de landelijke vwo-examenprogramma's. Actuele syllabi staan op [examenblad.nl](https://www.examenblad.nl), toelatingseisen op [studiekeuze123.nl](https://www.studiekeuze123.nl).

## Regels die de tool afdwingt

- Een vak kan maar één keer in het pakket.
- Kiest een leerling in een hoger onderdeel een vak dat al lager in het pakket staat, dan schuift het vak naar boven en vervalt de lagere keuze. De volgorde is: gemeenschappelijk deel, verplichte profielvakken, keuze-profielvakken, vrije deel, extra vakken.
- Maximaal 2 extra vakken per leerjaar. Bij een tweede extra vak verschijnt de melding "2e extra vak alleen op advies van de school".
- Wiskunde D kan alleen met wiskunde B en pas vanaf klas 5.
- CM en EM in klas 4: maximaal 1 bètavak (natuurkunde, scheikunde, biologie) in het vrije deel.
- In klas 5 kies je alleen uit vakken die je in klas 4 volgde. Uitzonderingen zijn maatschappijleer + profielwerkstuk (verplicht) en wiskunde D.
- Wiskunde in klas 5: B alleen als je in klas 4 B had. A, en bij CM ook C, kan na A of B in klas 4.

## Aannames, nog te bevestigen bij de decaan

- NT in klas 4: biologie ligt vast als keuze-profielvak. In klas 5 kies je tussen biologie en wiskunde D.
- Het vrije vak in klas 5 ("vak naar keuze*") gebruikt dezelfde keuzelijst als in klas 4, met wiskunde D erbij.
- Het profiel blijft in klas 5 en 6 hetzelfde als in klas 4.
- De vakteksten zijn niet afgestemd met de vaksecties van het Haganum.

## Aanpassen

Alle gegevens staan bovenaan het `<script>` in `index.html`:

| Constante | Inhoud |
|---|---|
| `MAIL_TO` | E-mailadres waar de keuze naartoe gaat |
| `MAX_EXTRAS` | Maximaal aantal extra vakken |
| `S` | Vaknamen per code |
| `FREE4`, `FREE5` | Keuzelijst "vak naar keuze" voor klas 4 en klas 5 |
| `BETA` | Vakken die meetellen als bètavak |
| `INFO` | Achtergrondinformatie per vak |
| `PROFILES` | Verplichte vakken, keuzevakken en vrije deel per profiel |
| `ICONS` | Icoon per profiel (SVG) |
| `groupsFor()` | Opbouw per leerjaar (gemeenschappelijk deel, enzovoort) |
| `blockReason()` | Waarom een vak niet gekozen kan worden |

## Disclaimer

Dit is geen officieel inschrijfformulier van het Haganum. Leerlingen bespreken hun keuze met hun mentor of decaan en leveren hem in zoals de school dat vraagt.
