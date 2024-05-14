---
title: Installazione
---

## Dagli store di estensioni

Scratch Addons è disponibile in questi store.

| Store | Installa | Browser supportati | Requisiti di sistema |
| - | - | - | - |
| Web Store di Chrome | [![Installa da Chrome Web Store](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 96+<br />Microsoft Edge 96+<br />Opera 82+<br />Brave 1.33+<br />Vivaldi 5.0+<br />*Chromium 96+* | Windows 7+<br />OS X / MacOS 10.11+
| Add-on di Firefox | [![Installa negli Add-ons di Firefox](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 109+ | Windows 7+<br />OS X / MacOS 10.12+
| Componenti aggiuntivi di Microsoft Edge | [![Installa negli Addon di Microsoft Edge](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 96+ | Windows 7+<br />OS X / MacOS 10.11+

## Dal codice sorgente

{{< admonition info >}}
Unlike the store releases, installing from source requires a browser based on Chromium 121+ or Firefox 121+.
{{< /admonition >}}

### Info sulle release GitHub

[La pagina delle release](https://github.com/ScratchAddons/ScratchAddons/releases) contiene il codice e i file per l'installazione di tutti i build di Scratch Addons, nonché il mirror dei build presenti negli store.

### Clonare il repository

This is the recommended way to install Scratch Addons for development purposes, assuming you have Git installed.

If you plan on contributing, fork the repository on GitHub first and then clone the fork, replacing `<username>` with your Github username.

```sh
$ git clone https://github.com/<username>/ScratchAddons.git
```
Per aggiornare Scratch Addons, fai `cd` nella sua cartella e poi esegui i comandi seguenti.

```sh
$ git fetch
$ git pull
```

Remember to also update Scratch Addons from the browser.


### Downloading the Zip

{{< admonition warning >}}
  This method is not recommended for development unless Git cannot be installed on the system since it will need to be manually repeated every time you update Scratch Addons.
{{< /admonition >}}

If you don not have Git installed, use this method instead.

1. Vai al [repository](https://github.com/ScratchAddons/ScratchAddons) e localizza il pulsante per lo scaricamento del codice.

1. Cliccalo e seleziona "Download ZIP".

1. Estrai il file zip in una cartella.

### Installazione per Google Chrome o Microsoft Edge

To load the extension into Google Chrome and most Chromium-based browsers such as Microsoft Edge, Opera, Brave or Vivaldi:

1. Go to [chrome://extensions](chrome://extensions)

1. Turn on "Developer mode" in the top-right corner

1. Click "Load unpacked" and select the `ScratchAddons` folder.

To update the extension when testing, click the refresh icon on the extension's card.

{{< admonition info >}}
  The "Unrecognized manifest key" warnings may safely be ignored, since they are required by Firefox.
{{< /admonition >}}


### Installazione per Mozilla Firefox

To load the extension into Mozilla Firefox:

{{< admonition info >}}
  Addons loaded into Firefox this way are temporary and must be reloaded every time the browser is restarted. Because of this Chrome is recommended for development, but everything is still expected to work on Firefox.
{{< /admonition >}}

1. Go to [about:debugging](about:debugging)

1. Click "This Firefox" on the sidebar

1. Click "Load Temporary Add-on..."

1. Select the `manifest.json` file in the `ScratchAddons` folder.

1. If a permission tab opens, click the "Enable" button.

To reload the extension when testing, click the "Reload" button on the extension's card.

{{< admonition info >}}
  The unexpected WebExtension manifest property warnings may safely be ignored, since they are required by Chrome.
{{< /admonition >}}

