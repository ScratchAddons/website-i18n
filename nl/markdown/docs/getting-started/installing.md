---
title: Installeren
---

## Van extensiestores

Scratch Addons is beschikbaar in deze stores.

| Store | Installeren | Ondersteunde browsers | Systeemvereisten |
| - | - | - | - |
| Chrome Web Store | [![Installeren voor Chrome Web Store](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 80+<br />Microsoft Edge 80+<br />Opera 67+<br />Brave 1.3+<br />Vivaldi 2.11+<br />*Chromium 80+* | Windows 7+<br />OS X / MacOS 10.11+<br />Chromebooks minder dan ~6 jaar oud
| Add-ons voor Firefox | [![Installeren voor Add-ons voor Firefox](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 86+ | Windows 7+<br />OS X / MacOS 10.12+
| Microsoft Edge-Invoegtoepassingen | [![Installeren voor Microsoft Edge-Invoegtoepassingen](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 80+ | Windows 7+<br />OS X / MacOS 10.11+

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

### Installeren op Google Chrome of Microsoft Edge

1. Typ `chrome://extensions` in je adresbalk om de Extensiebeheerpagina te openen.

2. Klik de schakelaar naast `Ontwikkelaarmodus` om het aan te zetten. Dit geeft je de mogelijkheid om extensies van een map of bestand te downloaden.

   ![Extension Management top bar screenshot](/assets/img/docs/developer-mode-toggle.png)

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

