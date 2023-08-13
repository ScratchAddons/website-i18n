---
title: Debugtips
description: Tips om userscripts makkelijk te debuggen, en randgevallen om rekening mee te houden.
---

Tips om userscripts makkelijk te debuggen, en randgevallen om rekening mee te houden.

## Tips

### Het is niet altijd nodig om de extensie te herladen

Het is niet nodig om de extensie te herladen door naar `chrome://extensions` te gaan wanneer je de bron van al bestaande JavaScript of CSS-bestanden aanpast. In die gevallen is de pagina herladen genoeg.

### Gebruik de addon.*-API vanuit de console

Voor ontwikkelingsredenen kan je kiezen om het `addon`-object te exposen als een globale variabele, zodat het toegankelijk is voor de browser-console.

```js
export default async function ({ addon, console }) {
  window.addon = addon;
  // ...
}
```

### Stel breekpunten in met het "debugger"-sleutelwoord

Het `debugger:`-sleutelwoord in JavaScript laat de pagina bevriezen als de ontwikkelaarstools openstaan. Breekpunten instellen is handig om de waarden van lokale variabelen te checken tijdens uitvoering.

### Consoleberichten filteren op addon-ID

Voer het addon-ID in bij de "filter"-zoekbalk in de console om alleen logs en waarschuwingen te zien, en ook errors die gelogd zijn met `console.error()`. Onthoud dat dit alle exceptions verbergt, behalve als je ze specifiek logt in je code.


## Randgevallen


### Projectpagina en editor van Scratch


#### De DOM wordt vernietigd na de editor in of uit te gaan

Elke keer dat de gebruiker op "bekijk van binnen" of "bekijk de project pagina" klikt, maakt Scratch alle HTML-elementen en vernietigd de oude.
Normaal gesproken kan dit worden opgelost met `addon.tab.waitForElement` of het `urlChange`-evenement.

#### De taal van de Scratch editor kan worden veranderd zonder te herladen

In tegenstelling tot de Scratch website herlaadt de Scratch editor niet wanneer de taal wordt veranderd. Misschien vernietigd Scratch sommige HTML-elementen en maakt ze opnieuw indien de taal verandert.

#### Andere situaties om rekening mee te houden

- De projecteditor kan gebruikt worden zonder een gedefinieerd project-ID (bijvoorbeeld, de gebruiker is uitgelogd).
- De editor kan van de links-naar-rechts-indeling wisselen naar de rechts-naar-links-indeling (of andersom) zonder de pagina te herladen.


### Scratch website

#### scratch-www pagina's herladen niet nadat de gebruiker inlogt

In tegenstelling tot scratchr2-pagina's herladen scratch-www pagina's niet nadat de gebruiker inlogt. Als je bijvoorbeeld naar een projectpagina gaat terwijl je uitgelogd bent en dan inlogt, dan herlaadt de pagina niet. Dit gebeurt ook bij studio's, de berichtenpagina, etc.
Alle Scratch-pagina's herladen WEL als je UITlogt.

#### Projectpagina's geven nooit een 404

Zelfs als het project niet is gedeeld of niet bestaat geeft Scratch een 200 HTTP statuscode. Het bericht "er is een fout opgetreden" wordt dynamisch toegevoegd aan de pagina door Scratch.

#### Andere situaties om rekening mee te houden

- Elk van de 4 tabbladen van studio's hebben verschillende URL's, maar trigger geen browsernavigatie. Addons die een van de vier pagina's beïnvloeden moeten uitvoeren, ongeacht de aanvankelijke URL.
