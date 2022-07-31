---
title: Veelgestelde Vragen
description: Op deze pagina staan veelgestelde vragen verwant met de Scratch Addons-extensie en -project.
---

Op deze pagina staan veelgestelde vragen verwant met de Scratch Addons-extensie en -project.

### Wat is Scratch Addons?

Scratch Addons is een alles-in-een browserextensie voor de Scratchwebsite en -projecteditor. Het geeft je functies en thema's (intern genaamd addons) voor zowel de Scratchwebsite als de projecteditor. De missie van Scratch Addons is om alle bestaande Scratchextensies, userscripts en userstyles te combineren, gemaakt door meerdere leden van de Scratchgemeenschap, in een enkele makkelijk toegankelijke plaats, terwijl gebruikers nog steeds mogen kiezen welke ze willen aanzetten.

### Wat is precies een "addon"?

Een addon is vergelijkbaar met een extensie of een userscript, maar ze gebruiken speciale API's geleverd door de Scratch Addons-extensie. Deze API's geven addons de mogelijkheid om scripts op een Scratchpagina uit te voeren (userscripts) of stijlen toepassen op de Scratchwebsite (userstyles).

Userscripts kunnen de `addon.*` JavaScript-API's gebruiken, waar ze Scratch-gerelateerde informatie vandaan halen (bijvoorbeeld de ingelogde gebruiker), en ze gebruiken ook extensie-API's (zoals notificaties sturen).

### Als alles een addon is, wat doet Scratch Addons dan?

Op zichzelf is Scratch Addons gewoon een addonlader. Zijn hoofdtaken zijn:

- Laat gebruikers addons in- of uitschakelen en instellen.
- Addons uitvoeren en ze API's leveren.
- De globale status aan addons leveren (zoals de addon.auth API).
- Maak prototypes voor gebruik door addonsuserscripts.
- Manieren om toegang te krijgen tot Redux-status en het te bewerken geven.
- Vermijden dat addons elkaar onderbreken.
- Dubbel werk van andere addons vermijden.

### Is Scratch Addons veilig?

Ja. Scratch Addons zou geen beveiligingsproblemen moeten hebben in zijn laatste versie. Scratch Addons is een open-bron project, dus de code wordt constant gecheckt door Scratch Addons-helpers, net zoals door recensenten van de Chrome Web Store, Add-ons voor Firefox en Microsoft Edge Add-ons.

### Hoe kan ik een beveiligingskwetsbaarheid melden?

Als je een beveiligingskwetsbaarheid tegenkomt, neem dan privé contact op met World_Languages door een e-mail te sturen naar `worldxlanguages (at) gmail.com`. Als je binnen 48 uur geen antwoord krijgt, maak dan [hier](https://github.com/ScratchAddons/ScratchAddons/issues/) een issue dat vermeldt dat je een e-mail hebt gestuurd.

Je kunt [ons beveiligingsbeleid lezen](https://github.com/ScratchAddons/ScratchAddons/security/policy), of [onze gepubliceerde adviezen checken](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### Zal mijn account veilig zijn als ik Scratch Addons gebruik?

Scratch Addons gebruikt niet je accountgegevens om echt te werken. In feite kun je uitgelogd zijn van Scratch, en Scratch Addons zal nog steeds werken. Scratch Addons verstuurt alleen verzoeken gebaseerd op de cookies die je hebt, die worden geleverd door de browser voor elk verzoek, dus sommige addons zoals Scratch-Berichtgeving zullen niet werken als je niet bent ingelogd, maar het zal andere delen van de extensie niet beïnvloeden.

Addons op Scratch Addons zijn ook gecontroleerd door meerdere helpers op het archief, dus niemand kan gewoon stiekem gevaarlijke code gebruiken.

We versturen nooit Scratchaccountinformatie of extensie-instellingen buiten je browser. Bekijk [het extensie-privacybeleid](/docs/privacy/policies/extension) voor meer informatie.

### Kan ik andere mensen over Scratch Addons vertellen op Scratch?

Nee, en doe het alsjeblieft niet. Er is een beleid dat het reclame maken voor extensies/userscripts verbiedt [hier](https://scratch.mit.edu/discuss/post/2907564/). Je kunt wel andere manieren gebruiken om je vrienden te vertellen over Scratch Addons.

### Hoe kan ik meehelpen met Scratch Addons?

Allereerst, bedankt dat je geïnteresseerd bent om mee te helpen aan Scratch Addons. We stellen je interesse en je latere bijdragen op prijs.

Als een open-bron project heten we alle soorten bijdragen welkom. Je hoeft het ons niet eens te vragen en je hebt geen rang nodig. Iedereen is welkom. Er is zelfs een kans dat je niet eens weet dat je hebt meegeholpen aan het project!

Hoe dan ook, je kunt in veel manieren meehelpen, en sommige zijn heel makkelijk.

- **Code bijdragen**

  Als je JavaScript, HTML 5, en CSS kent, kun je meehelpen door een beetje te coderen/programmeren. Je kunt bugs oplossen, enkele verzoeken aanpakken, of je eigen addon maken.

  Daarna moet je een pull-verzoek maken. Dat kun je doen door een vertakking te maken van [het archief](https://github.com/ScratchAddons/ScratchAddons/), maak je nodige veranderingen, en maak een pull-verzoek. Als het goedgekeurd wordt, zullen we het samenvoegen.

  We heten ook bijdragen aan andere aspecten dan de extensie welkom. Je kunt onze archieven zien op [onze GitHub-organisatiepagina](https://github.com/ScratchAddons) en ons helpen met ze te bouwen.

- **Een idee geven**

  Heb je een idee voor iets wat een goede bijdrage zou leveren aan Scratch Addons? [Vertel het ons!](#i-think-you-missed-a-feature-what-can-i-do)

- **Een bug melden**

  Heb je een bug gevonden in een van onze addons, de instellingspagina, of iets anders in onze extensie? [Verstuur ons een bug-melding](#what-can-i-do-if-i-find-a-problem).

- **Scratch Addons Vertalen**

  Als je Engels en een andere taal vloeiend spreekt, kun je helpen met vertalen/lokaliseren van Scratch Addons in je eigen taal. Je kunt [hier](/docs/localization/joining-the-localization-team) starten.

- **De documentatie schrijven**

  Ben je bekend met Scratch Addons? Zo ja, dan kun je zijn documentatie schrijven. De documentatie kan inhouden hoe je het moet gebruiken of hoe het werkt. Neem contact met ons op op [onze Discussiepagina](https://github.com/ScratchAddons/ScratchAddons/discussions) voor meer informatie.

- **Feedback geven**

  Je kunt ons feedback geven op ons formulier op [de feedbackpagina](https://scratchaddons.com/feedback). Je feedback kan ons een ander beeld geven in de ontwikkeling van de extensie en laat ons weten over dingen die aandacht of oplossingen nodig hebben.

- **Laat een recensie achter op de winkels**

  Je kunt ons een recensie over Scratch Addons achterlaten op [de Chrome-extensiepagina](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco), [de Firefox-addonpagina](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) of de [Microsoft Edge-addonpagina](https://microsoftedge.microsoft.com/addons/detail/scratch-addons/iliepgjnemckemgnledoipfiilhajdjj).

- **Geef ons archief een ster**

  Eigenlijk is de GitHub-ster gelijk aan de Scratch-ster/favoriet. Je kunt dit doen door naar [ons archief](https://github.com/ScratchAddons/ScratchAddons) te gaan en te klikken op de "Ster"-knop rechtsbovenin.

- **Vertel het verder**

  Je kunt iedereen over Scratch Addons vertellen, zoals je vrienden, je bekenden, je familieleden, of zelfs je leerkracht, als je dat wilt. We vragen je alleen om dit [niet te doen op de Scratchwebsite](#can-i-tell-people-about-scratch-addons-on-scratch).

### Hoe maak ik mijn eigen addon?

Lees [hier](/docs/develop/getting-started) meer over hoe je een addon op Scratch Addons maakt.

### Hoe zet ik mijn naam op de [helperspagina](/contributors)?

Lees en volg graag de instructies van [deze issue](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}) om je naam op de pagina te krijgen.

### Hoe verwijder ik mijn naam van de [helperspagina](/contributors)?

Als je je naam niet op de pagina wilt hebben, vertel het ons graag door een issue op [ons helpersarchief](https://github.com/ScratchAddons/contributors/issues/) te openen, of op andere contactmethodes. Excuses voor het ongemak.

### Wat kan ik doen als ik een probleem vind?

Je kunt het ons vertellen door een van deze methodes.

- Verzend het door [ons feedbackformulier](https://scratchaddons.com/feedback).
- Maak een issue op [het archief](https://github.com/ScratchAddons/ScratchAddons/issues).
- Maak een post op [onze Discussiepagina](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Vertel het ons op [onze Discord-server](https://discord.gg/R5NBqwMjNc).

### Ik denk dat jullie een functie hebben gemist. Wat kan ik doen?

Als je denkt dat er een functie mist, of je wilt een addon voorstellen, of je hebt een goed idee, vertel het ons door [een van de bovengenoemde methodes te volgen](#what-can-i-do-if-i-find-a-problem).

### Waar kan ik discussiëren over Scratch Addons?

Je kunt het doen op [onze Discussiepagina](https://github.com/ScratchAddons/ScratchAddons/discussions) of [onze Discord-server](https://discord.gg/R5NBqwMjNc). Daar kun je erover discussiëren en vragen stellen als je problemen hebt.

### Ik heb het idee dat Scratch Addons Scratch vertraagd. Wat kan ik doen?

Probeer addons uit te zetten die je niet nodig hebt. Controleer ook opmerkingen en waarschuwingen in addons om te beslissen welke addons aan of uit moeten voor betere prestaties.

### Hoe kun je de easter-egg-addons inschakelen?

Om de easter-egg-addons te gebruiken, voer de Konami Code (↑↑↓↓←→←→BA) in op de instellingspagina. Daarna zullen de easter-egg-addons zichtbaar zijn zodat je ze kan aanzetten.

Sommige van onze easter-egg-addons zijn "Accountinstellingen Met Hoofdletters" en "Puntkommaglitch". Bekijk [de addonspagina](/addons) voor een complete lijst.

### Ik heb nog meer vragen!

Als je nog onbeantwoorde vragen hebt, kun je een post maken op [onze Discussiepagina](https://github.com/ScratchAddons/ScratchAddons/discussions) of verstuur een bericht [op onze Discord-server](https://discord.gg/R5NBqwMjNc). Iemand zal het voor je proberen te antwoorden.
