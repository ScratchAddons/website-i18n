---
title: Namestitev
---

## Iz trgovin z razširitvami

Scratch Addons is available in these stores.

| Store | Namesti | Supported browsers | Sistemske zahteve |
| - | - | - | - |
| Chrome Web Store | [![Install for Chrome Web Store](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 96+<br />Microsoft Edge 96+<br />Opera 82+<br />Brave 1.33+<br />Vivaldi 5.0+<br />*Chromium 96+* | Windows 7+<br />OS X / MacOS 10.11+
| Add-ons for Firefox | [![Install for Add-ons for Firefox](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 109+ | Windows 7+<br />OS X / MacOS 10.12+
| Microsoft Edge Add-ons | [![Install for Microsoft Edge Addons](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 96+ | Windows 7+<br />OS X / MacOS 10.11+

## Z izvirno kodo

### About GitHub releases

[The releases page](https://github.com/ScratchAddons/ScratchAddons/releases) contains the code and installation files for all development builds of Scratch Addons, as well as the mirror of the store builds.

### Podvajanje kode

This is the recommended way to install Scratch Addons for development purposes. This assumes you have Git installed.

To download the repository, simply clone `https://github.com/ScratchAddons/ScratchAddons.git`.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
To update Scratch Addons, first `cd` into its folder, and then run the following commands.

```sh
$ git fetch
$ git pull
```

This will update Scratch Addons and get it ready for code editing. Note that you will need to see the finish updating section [here](#install-on-google-chrome) if you are using Google Chrome.


### Prenos datoteke .zip

If you don't have Git installed, you can try this method instead. Note that you will need to manually repeat this process every time you want to update Scratch Addons.

1. Go to the [repository](https://github.com/ScratchAddons/ScratchAddons) and find the download code button.

   ![Posnetek zaslona z gumbom Download code](/assets/img/docs/download-code-button.png)

2. Kliknite ga in izberite "Download ZIP".

   ![Posnetek zaslona z gumbom Download ZIP](/assets/img/docs/download-zipball-button.png)

3. Extract the archive into a folder.

### Installing on Google Chrome or Microsoft Edge

1. V naslovno vrstico vnesite `chrome://extensions`, da odprete stran za upravljanje razširitev.

2. Kliknite stikalo `Način za razvijalce`, da vključite način za razvijalce. To omogoča nameščanje razširitev iz map ali datotek.

   ![Extension Management top bar screenshot](/assets/img/docs/developer-mode-toggle.png)

3. Prikazati bi se moral gumb `Naloži razpakirano`. Ko ga kliknite, lahko izberete mapo.

   ![Posnetek zaslona z gumbom Naloži razpakirano](/assets/img/docs/load-unpacked-button.png)

4. Select the extracted folder.
5. Razširitev bi zdaj morala biti naložena.

To finish updating (assuming you followed the updating steps [here](#cloning-the-repository)), click the `Update` button:

![Update button screenshot](/assets/img/docs/update-button.png)


### Namestitev v brskalniku Mozilla Firefox

1. V naslovno vrstico vnesite `about:debugging`, da odprete stran za razhroščevanje.

2. Click `This Firefox` on the left-hand menu.

   ![Posnetek zaslona menija na levi strani](/assets/img/docs/left-hand-menu.png)

4. Kliknite `Naloži začasen dodatek...`.

   ![Load Temporary Add-on button screenshot](/assets/img/docs/load-addon.png)

6. Select the manifest.json file inside the extracted folder.
7. Razširitev bi zdaj morala biti naložena.

Note: Firefox temporary add-ons are actually temporary. Restarting Firefox will remove them, so if you want to use the development version of Scratch Addons all the time, it is recommended that you use a Chromium-based browser like Google Chrome.

