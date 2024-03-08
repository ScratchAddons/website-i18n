---
title: Å lage en tillegg
---
Nødvendig programvare: tekstredigeringsprogram, Chrome.
Hvis mulig, deaktiver Scratch Addons-utvidelsen du lastet ned fra butikken før du fortsetter for å unngå problemer.


{{< admonition info >}}
Hvis du planlegger å sende inn tillegget du utvikler som en pull request til vårt GitHub repositoriet, vennligst les våre [bidragsretningslinjer](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md) først.

I tilfelle det ikke finnes en eksisterende GitHub-utgave i den aktuelle lagringsplassen som er relatert til din nye tilleggsidé, vennligst [opprett en](https://github.com/ScratchAddons/ScratchAddons/issues/new/choose). Hvis det imidlertid allerede finnes en utgave relatert til din funksjonsidé, foreslår vi at du legger igjen en kommentar der og oppgir din intensjon om å utvikle tillegget. Dette vil gjøre det mulig for andre bidragsytere å gi tilbakemelding om hvorvidt tillegget kan aksepteres, eller om det kreves videre diskusjon.

Imidlertid, hvis du oppretter en tillegg for personlig bruk, kan du fortsette med denne veiledningen.
{{< /admonition >}}

## Trinn 1: Les om [tilleggsmodulgrunnleggende](/docs/develop/getting-started/addon-basics/)
Sørg for å lese den artikkelen for å bli kjent med terminologien.

## Trinn 2: Fork/klon [repoet](https://github.com/ScratchAddons/ScratchAddons)
Følg [disse instruksjonene](/docs/getting-started/installing/#from-source) for å laste ned kildekoden lokalt.

## Trinn 3: Last inn utvidelsen i Chrome
*Obs: Chrome anbefales for å jobbe med tillegg. Likevel forventes det at tillegg fungerer på Firefox og Edge.*
Nå som du har utvidelsen på filsystemet ditt, gå til `chrome://extensions` og slå på "utviklermodus".
Klikk på "last inn ukomprimert" og velg deretter mappen der Scratch Addons er plassert. Hvis du har problemer med dette, sørg for å velge mappen der `manifest.json` er plassert.
Det er det, du har lastet inn utvidelsen! Den skal se omtrent slik ut:
![bilde](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)
Obs: Du kan trygt ignorere at det står "feil". Det er bare en advarsel for en ukjent manifestnøkkel som kreves av Firefox.

## Trinn 4: Hva handler tillegget ditt om?
Nå kommer den morsomme delen!
Hva vil tillegget ditt gjøre? Tenk på en selvbeskrivende tilleggs-ID (ingen mellomrom eller spesialtegn, bortsett fra bindestreker).
Har du det?

## Trinn 5: Opprett mappen for tillegget
Bruk en filutforsker for å gå til mappen der Scratch Utvidelser befinner seg på filsystemet ditt. Finn mappen `addons`. 
Deretter opprett en ny mappe med ditt episke utvidelses-ID som navn.

## Trinn 6: Legg til en tilleggsmanifest
Utvidelsesmanifestet forteller Scratch Utvidelser hvordan utvidelsen din fungerer. Pass på å få dette riktig for å unngå hodepine.
Inne i mappen du nettopp opprettet, opprett en `addon.json`-fil.
Dette er en base du kan bruke for å starte kodingen, pass på å endre den i fremtiden.
```json
{
  "name": "Episk plassholdertekst i stedet for tilleggsnavn",
  "description": "Hei verden! Det ville vært veldig smart å erstatte denne plassholderteksten med en beskrivelse.",
  "tags": ["community"],
  "enabledByDefault": false
}
```
For mer informasjon om hva du kan erklære i manifestet, sjekk [denne artikkelen](/docs/reference/addon-manifest/).


## Trinn 7: Fortell Scratch Utvidelser hva ID-en til utvidelsen din er
Scratch Utvidelser kan ikke finne nye mapper av seg selv, så du må legge til navnet i en spesialfil. 
Gå til `scratchAddonsFolder/addons/addons.json` og legg til ID-en til utvidelsen din i arrayet.

## Trinn 8: Hei verden
Din utvidelse gjør ingenting for øyeblikket, så det er en god tid å sjekke om alt vi tidligere har laget fungerer. 
Gå til `chrome://extensions` og last inn Scratch Utvidelser ved å klikke på oppdateringssymbolet på kortet. 
Nå, høyreklikk på Scratch Utvidelser-ikonet og klikk på "alternativer". 
Du bør se utvidelsen din på listen! Når du finner den, aktiver den og sett eventuelle innstillinger du måtte ha.

## Trinn 9: Den morsomme delen, kode!
*Før du fortsetter, sørg for å lese wiki-artikkelen som er lenket i trinn 1.*

Her kommer den morsomme delen: lag dine egne JS- eller CSS-filer!
Protips: etter å ha gjort endringer i utvidelsen din, sørg for å oppdatere Scratch Utvidelser tilleg slik du gjorde i trinn 8.

Avhengig av hva du vil at tillegget ditt skal gjøre, bør du nå sjekke disse wikisidene:
- [Brukerscrpiter](/docs/develop/userscripts)
- [Brukerstyler](/docs/develop/userstyles)

## Trinn 10: Gjør tillegget ditt tilpasningsbart
Hvis du vil, kan du gjøre tillegget ditt tilpassbart!
Brukere av tillegget ditt vil kunne slå av og på innstillinger, skrive inn tall og mer!
For å komme i gang, se [hvordan du erklærer innstillinger i tilleggets manifest](/docs/reference/addon-manifest/#settings-object).
Deretter, gå til [addon.settings-dokumentasjonen](/docs/reference/addon-api/addon.settings) for å lære hvordan du får tilgang til brukervalg fra brukerskript.

## Trinn 11: Før du publiserer tillegget ditt
Nå som tillegget ditt fungerer, la oss sørge for at vi kan legge det til i tilleggsbiblioteket. Sørg for at tilleggets manifest er egnet, [mer informasjon her](/docs/reference/addon-manifest). Vær nøye med navnet, beskrivelsen og taggene til tillegget ditt. Sørg for å sette `"enabledByDefault"` til `false` eller fjern det. Sørg for at tillegget ditt ikke ødelegger andre tillegg. Sørg for at koden din er forståelig; det er bedre med unødvendige kommentarer enn ingen kommentarer.

## Trinn 12: Send en pull request!
Følg trinnene på våre [bidragsretningslinjer](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md). Enkelt sagt, forke repoet hvis du ikke allerede har gjort det, committ din nye tillegg og send en PR! Husk at vi kanskje ber deg om å gjøre noen endringer, men vi vil sannsynligvis godta tillegget ditt så lenge det er minimalt egnet.
