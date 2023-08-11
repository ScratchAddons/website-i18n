---
title: Userscripts
description: Userscripts zijn JavaScript-bestanden die worden uitgevoerd zodra de pagina wordt geladen. Ze kunnen de HTML van het document aanpassen, nieuwe knoppen toevoegen, het gedrag van de Scratcheditor aanpassen en nog veel meer.
---

Userscripts zijn JavaScript-bestanden die worden uitgevoerd zodra de pagina wordt geladen. Ze kunnen de HTML van het document aanpassen, nieuwe knoppen toevoegen, het gedrag van de Scratcheditor aanpassen en nog veel meer.

Userscripts van Scratch Addons bestaan uit stukjes JavaScript die in dezelfde uitvoercontext worden uitgevoerd als de JavaScript-code van Scratch zelf (vergelijkbaar met userscripts die je misschien downloadt voor userscriptmanagers zoals Tampermonkey of Greasemonkey). In het browserextensie-woordenboek noemen we dit ook wel de "main world".

Ook al zijn Scratch Addons userscripts onderdeel van een browserextensie, ze hebben geen toegang tot enige `chrome.*` of `browser.*`-API's. Scratch Addons biedt een [`addon.*`-API](/docs/reference/addon-api/) aan als vervanging.


## Userscripts declareren in de addonmanifest

{{< admonition warning >}}
**Sommige veranderingen vereisen dat je de extensie herlaadt** van `chrome://extensions` om effect te hebben, zoals het addonmanifest-bestand updaten.

Het is niet nodig om de extensie de herladen wanneer je de bron van een al bestaand userscript JavaScript-bestand verandert. In die gevallen is de pagina herladen genoeg.
{{< /admonition >}}

Userscripts worden binnen een "userscripts"-array gedeclareerd.

Elk item van de array moet de volgende eigenschappen hebben:
- `"url"`: de relatieve URL tot een JavaScript-bestand.
- `"matches"`: de lijst van Scratch-pagina's waar de userscript wordt uitgevoerd. Lees [matches](/docs/reference/addon-manifest/#matches) voor meer informatie.

Voorbeeldmanifest:
```json
{
  "name": "Kopieer link naar opmerking-knop",
  "description": "Voegt een \"Kopieer Link\"-knop toe aan alle opmerkingen op de website, naast de \"Melden\"-knop.",
  "userscripts": [
    {
      "url": "userscript.js",
      "matches": ["projects", "https://scratch.mit.edu/", "profiles", "studios"]
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```

## Je eerste userscript maken

In tegenstelling tot extensie-contentscripts en Tampermonkey-userscripts, moet je al je code in een "module default export" zetten:
```js
// Voorbeeld userscript
export default async function ({ addon, console }) {
  console.log("Hallo, " + await addon.auth.fetchUsername());
  console.log("Hoe gaat het met je?");
}
```

Onthoud dat je in JavaScript functies kunt declareren binnenin andere functies, bijvoorbeeld:
```js
export default async function ({ addon, console }) {
  async function sayHelloToUser() {
    console.log("Hallo, " + await addon.auth.fetchUsername());
  }

  await sayHelloToUser();
  console.log("Hoe gaat het met je?");
}
```

{{< admonition info >}}
Je kunt toegang krijgen tot vele `addon.*`-API nutsvoorzieningen van userscripts. Je kunt bijvoorbeeld de huidige gebruikersnaam krijgen, wachten tot een element bestaat op de pagina, of krijg een verwijzing naar het Scratch VM-object.

Lees de [API-referentie](/docs/reference/addon-api/) voor meer informatie.
{{< /admonition >}}


## De HTML wijzigen

Gebruik [browser DOM-API's](https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API) om de HTML van de pagina aan te passen.

Hier is een voorbeeld:
```js
const myButton = document.createElement("button");
myButton.textContent = "Klik op mij!";
myButton.classList.add("button");
myButton.setAttribute("title", "Je zweeft over een knop");

const myContainer = document.querySelector(".container");
myContainer.append(myButton);
```

## Userscripts lokaliseren

Addon-userscripts moeten soms Engelse woorden of zinnen bevatten. Zorg ervoor dat je ze niet hard-codeert zodat ze vertaald kunnen worden.

{{< admonition error >}}
```js
// Doe dit niet:
document.querySelector(".sa-find-bar").placeholder = "Vind blokken";
```
{{< /admonition >}}

Om een vertaalbare string te maken volg je deze stappen:
1. Maak een bestand genaamd `addon-id.json` in de map `/addon-l10n/en`.
2. Geef elke string een ID:
```json
{
  "addon-id/find": "Find blocks"
}
```
3. Zorg ervoor dat je de `msg()`-functie importeert in je userscript. De eerste regel van je userscript zou er zo uit moeten zien:
```js
export default async function ({ addon, console, msg  }) {
                                              // ^^^
```
4. Gebruik de `msg()`-functie in je code, i.p.v. een hard-gecodeerde string:
```js
document.querySelector(".sa-find-bar").placeholder = msg("vinden");
```

{{< admonition info >}}
Lees [deze pagina](/docs/localization/localizing-addons/) voor meer informatie over userscripts lokaliseren.
{{</admonition >}}


## Technische details

Elke userscript is een JavaScript-module die een functie exporteert. Scratch Addons importeert de module alleen als dat nodig is, en voert 'm uit nadat de pagina volledig is geladen.

Userscripts zijn JavaScript-modules, dus ze worden altijd uitgevoerd op ["strikte modus"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode). Dit betekent ook dat userscripts misschien ["top-level imports"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) kunnen gebruiken om andere JavaScript-bestanden te importeren.

De volgorde waarin userscript zich uitvoeren kan elke keer dat de pagina wordt geladen verschillen. De gebruiker kan addons altijd dynamisch inschakelen, dus de uitvoervolgorde is nooit zeker. Sommige API's zoals [`addon.tab.appendToSharedSpace`](/docs/reference/addon-api/addon.tab/addon.tab.appendtosharedspace/) maken een poging om enkele zeldzame gevallen en onverwacht gedrag te voorkomen wanneer addons dynamisch worden ingeschakeld.

### runAtComplete

Userscripts kunnen kiezen of ze uitgevoerd moeten worden voordat de pagina volledig is geladen door `"runAtComplete": false` in de addonmanifest te includeren, één keer per userscript.

Op dit moment is alleen `document.head` gegarandeerd om te bestaan wanneer een userscript vroeg uitvoert. In de toekomst wordt dit ook het geval voor `document.body`, dus geen enkele userscript wordt uitgevoerd voordat het HTML-bestand genoeg is geladen om `</head> <body>` te bereiken.
