---
title: Userstyles
description: Userstyles laten je CSS injecteren op de Scratch-website - handig om je knoppen uit userscripts kleurrijk te maken, of om natieve Scratch-elementen aan te passen.
---
## Wat zijn ze?
Userstyles laten je CSS injecteren op de Scratch-website - handig om je knoppen uit userscripts kleurrijk te maken, of om natieve Scratch-elementen aan te passen.

## Hoe voeg ik een userstyle toe?
**Zorg ervoor dat je Scratch Addons ververst van `chrome://extensions` nadat je veranderingen maakt aan je addon.** 
Ga naar de manifest van je addon (addon.json) en voeg een eigenschap toe genaamd `userstyles"`. 
Deze eigenschap moet een array zijn. 
Elk item van de array moet de volgende eigenschappen hebben: `"url"` en `"matches"`. 
`"url"` moet een relatieve URL tot een JavaScript-bestand zijn. 
`"matches"` moet een array van URLs zijn waar je de userstyle op wilt uitvoeren. Je kunt asterisken (sterretjes) gebruiken.
Voorbeeldmanifest:
```json
{
  "name": "Scratch Berichtgeving",
  "description": "Laat je makkelijker je Scratchberichten lezen en erop antwoorden.",
  "userstyles": [
    {
      "url": "userstyle.css",
      "matches": ["https://scratch.mit.edu/*"]
    },
    {
      "url": "second_userstyle.css",
      "matches": ["https://scratch.mit.edu/projects/*", "https://scratch.mit.edu/users/*"]
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```

## Userstyles debuggen
**Ververs Scratch Addons van `chrome://extensions` nadat je veranderingen maakt aan je addon.** 
Als je userstyle niet werkt, zorgt ervoor dat je addon aanstaat. 
Als je nog steeds problemen hebt, maak dan een issue in dit archief.
