---
title: Installerer
---

## Fra utvidelsesbutikker

Scratch Addons er tilgjengelig i disse butikkene.

| Butikk | Installer | Støttede nettlesere | Systemkrav |
| - | - | - | - |
| Chrome Web Store | [![Installer for Chrome Web Store](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 80+<br />Microsoft Edge 80+<br />Opera 67+<br />Brave 1.3+<br />Vivaldi 2.11+<br />*Chromium 80+* | Windows 7+<br />OS X / MacOS 10.11+<br />Chromebooks mindre enn ~6 år gamle
| Tillegg for Firefox | [![Installer tilleggsprogrammer for Firefox](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 86+ | Windows 7+<br />OS X / MacOS 10.12+
| Microsoft Edge-tillegg | [![Installer for Microsoft Edge Addons](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 80+ | Windows 7+<br />OS X / MacOS 10.11+

## Fra kilde

### Om GitHub-utgivelser

[Releases-siden](https://github.com/ScratchAddons/ScratchAddons/releases) inneholder koden og installasjonsfilene for alle utviklingsversjoner av Scratch Addons, samt speilet av butikkversjonene.

### Kloning av repositoriet

Dette er den anbefalte måten å installere Scratch Addons for utviklingsformål. Dette forutsetter at du har Git installert.

For å laste ned repositoriet, kan du enkelt klone `https://github.com/ScratchAddons/ScratchAddons.git`.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
For å oppdatere Scratch Addons, først `cd` inn i mappen sin, og deretter kjør følgende kommandoer.

```sh
$ git fetch
$ git pull
```

Dette vil oppdatere Scratch Addons og gjøre det klart for kode-redigering. Merk at du må se avsnittet om ferdig oppdatering [her](#install-on-google-chrome) hvis du bruker Google Chrome.


### Laste ned zipball

Hvis du ikke har Git installert, kan du prøve denne metoden i stedet. Merk at du må gjenta denne prosessen manuelt hver gang du vil oppdatere Scratch Addons.

1. Gå til [repositoriet](https://github.com/ScratchAddons/ScratchAddons) og finn nedlastingskoden.

   ![Last ned kodeknapp skjermbilde](/assets/img/docs/download-code-button.png)

2. Klikk på den og velg "Last ned ZIP".

   ![Last ned ZIP-knapp skjermbilde](/assets/img/docs/download-zipball-button.png)

3. Pakk ut arkivet i en mappe.

### Installerer på Google Chrome eller Microsoft Edge

1. Skriv `chrome://extensions` i adressefeltet for å åpne siden for utvidelseshåndtering.

2. Klikk på bryteren ved siden av `Utviklermodus` for å aktivere utviklermodus. Dette lar deg installere utvidelser fra en mappe eller fil.

   ![Extension Management top bar screenshot](/assets/img/docs/developer-mode-toggle.png)

3. Du bør se knappen `Last inn ukomprimert` vises. Ved å klikke på den kan du velge en mappe å laste opp.

   ![Last opp pakket knapp skjermbilde](/assets/img/docs/last-opp-pakket-knapp.png)

4. Velg den uttrukne mappen.
5. Utvidelsen skal nå være lastet.

For å fullføre oppdateringen (forutsatt at du fulgte oppdateringsstegene [her](#kloning-av-repositoriet)), klikk på `Oppdater`-knappen.

![Oppdateringsknapp skjermbilde](/assets/img/docs/update-button.png)


### Installerer på Mozilla Firefox

1. Skriv `about:debugging` i adressefeltet for å åpne feilsøkingsiden.

2. Klikk på `Denne Firefox` i venstremenyen.

   ![Venstremeny skjermbilde](/assets/img/docs/venstremeny.png)

4. Klikk på `Last inn midlertidig tillegg...`.

   ![Last inn midlertidig tilleggsknapp skjermbilde](/assets/img/docs/load-addon.png)

6. Velg manifest.json-filen inne i den utpakkede mappen.
7. Utvidelsen skal nå være lastet.

Merk: Midlertidige tillegg i Firefox er faktisk midlertidige. Hvis du starter Firefox på nytt, vil de bli fjernet, så hvis du vil bruke utviklingsversjonen av Scratch Addons hele tiden, anbefales det at du bruker en Chromium-basert nettleser som Google Chrome.

