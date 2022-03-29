---
title: Installeren
---

## Van extensiestores

Scratch Addons is beschikbaar in de Chrome Web Store en Add-ons voor Firefox.

- Chrome Web Store (voor Google Chrome, Opera, Brave, Vivaldi, Microsoft, Edge >79, en andere Chromium-gebaseerde browsers)
  https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco

- Add-ons voor Firefox (voor Mozilla Firefox)  
  https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/

- Microsoft Edge Add-ons (voor Microsoft Edge >79)  
  https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj

## Van bron

### Over GitHub-releases

[De pagina met releases](https://github.com/ScratchAddons/ScratchAddons/releases) bevat de code en installatiebestanden voor alle ontwikkelingsbuilds van Scratch Addons, net zoals de spiegel van de store-builds.

### Het archief kopiëren

Dit is de aanbevolen manier om Scratch Addons voor ontwikkelingsredenen te installeren. Dit gaat ervan uit dat je Git hebt geïnstalleerd.

Om het archief te downloaden, kopieer simpelweg `https://github.com/ScratchAddons/ScratchAddons.git`.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
Om Scratch Addons bij te werken, doe eerst `cd` in zijn map, en voer dan de volgende commando's uit.

```sh
$ git fetch
$ git pull
```

Dit zal Scratch Addons updaten en het klaarmaken voor het bewerken van code. Onthoud wel dat je [hier](#install-on-google-chrome) het stuk over updates voltooien moet lezen als je Google Chrome gebruikt.


### De zipball downloaden

Als je Git niet geïnstalleerd hebt, kun je in plaats daarvan dit proberen. Onthoud dat je dit proces elke keer handmatig moet herhalen als je Scratch Addons wilt updaten.

1. Ga naar het [archief](https://github.com/ScratchAddons/ScratchAddons) en vind de code downloaden-knop.

   ![Screenshot van code-downloadknop](/assets/img/docs/download-code-button.png)

2. Klik erop en selecteer "ZIP downloaden".

   ![Screenshot van ZIP-downloadknop](/assets/img/docs/download-code-button.png)

3. Pak het archief in een map uit.

### Installeren op Google Chrome

1. Typ `chrome://extensions` in je adresbalk om de Extensiebeheerpagina te openen.

2. Klik de schakelaar naast `Ontwikkelaarmodus` om het aan te zetten. Dit geeft je de mogelijkheid om extensies van een map of bestand te downloaden.

   ![Screenshot van Extensiebeheer bovenste balk](/assets/img/docs/developer-mode-toggle.png)

3. Je zou de `Uitgepakte extensie laden`-knop moeten zien. Als je erop klikt kun je een bestand selecteren om te uploaden.

   ![Screenshot van uitgepakte extensie laden-knop](/assets/img/docs/load-unpacked-button.png)

4. Selecteer het uitgepakte bestand.
5. De extensie zou nu geladen moeten zijn.

Om het updaten af te ronden (ervan uitgaand dat je [hier](#cloning-the-repository) de stappen voor het updaten hebt gevolgd), klik op de `Updaten`-knop.

![Screenshot van updaten-knop](/assets/img/docs/update-button.png)


### Installeren op Mozilla Firefox

1. Typ `about:debugging` in je adresbelk om de debugpagina te openen.

2. Klik op `Deze Firefox` in het menu links.

   ![Screenshot van linker menu](/assets/img/docs/left-hand-menu.png)

4. Klik op `Tijdelijke Add-on Laden...`.

   ![Screenshot van Tijdelijke Add-on Laden-knop](/assets/img/docs/load-addon.png)

6. Selecteer het manifest.json-bestand in de uitgepakte map.
7. De extensie zou nu geladen moeten zijn.

Opmerking: Tijdelijke add-ons zijn ook echt tijdelijk. Firefox opnieuw opstarten zal ze verwijderen, dus als je altijd de ontwikkelingsversie van Scratch Addons wilt gebruiken, is het aanbevolen om een Chromium-gebaseerde browser te gebruiken zoals Google Chrome.

