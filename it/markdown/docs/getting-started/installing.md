---
title: Installazione
---

## Dagli store di estensioni

Scratch Addons è disponibile in questi store.

| Store | Installa | Browser supportati | Requisiti di sistema |
| - | - | - | - |
| Web Store di Chrome | [![Installa da Chrome Web Store](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 80+<br />Microsoft Edge 80+<br />Opera 67+<br />Brave 1.3+<br />Vivaldi 2.11+<br />*Chromium 80+* | Windows 7+<br />OS X / MacOS 10.11+<br />Chromebooks con meno di ~6 anni
| Add-on di Firefox | [![Installa negli Add-ons di Firefox](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 86+ | Windows 7+<br />OS X / MacOS 10.12+
| Componenti aggiuntivi di Microsoft Edge | [![Installa negli Addon di Microsoft Edge](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 80+ | Windows 7+<br />OS X / MacOS 10.11+

## Dal codice sorgente

### Info sulle release GitHub

[La pagina delle release](https://github.com/ScratchAddons/ScratchAddons/releases) contiene il codice e i file per l'installazione di tutti i build di Scratch Addons, nonché il mirror dei build presenti negli store.

### Clonare il repository

Questo è il modo raccomandato di installare Scratch Addons per scopi di sviluppo. Assume che tu abbia già installato Git.

Per scaricare il repository basta clonare `https://github.com/ScratchAddons/ScratchAddons.git`.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
Per aggiornare Scratch Addons, fai `cd` nella sua cartella e poi esegui i comandi seguenti.

```sh
$ git fetch
$ git pull
```

Questo aggiornerà Scratch Addons e lo preparerà per le successive modifiche al codice. Nota che se stai usando Google Chrome dovrai consultare la sezione per il completamento dell'aggiornamento che trovi [qui](#install-on-google-chrome).


### Scaricamento del file zip

Se non hai installato Git puoi provare questo metodo alternativo. Nota che dovrai ripetere manualmente questo processo ogni volta che vuoi aggiornare Scratch Addons.

1. Vai al [repository](https://github.com/ScratchAddons/ScratchAddons) e localizza il pulsante per lo scaricamento del codice.

   ![Screenshot del pulsante per lo scaricamento del codice](/assets/img/docs/download-code-button.png)

2. Cliccalo e seleziona "Download ZIP".

   ![Screenshot del pulsante Scarica ZIP](/assets/img/docs/download-zipball-button.png)

3. Estrai il file zip in una cartella.

### Installazione per Google Chrome o Microsoft Edge

1. Digita `chrome://extensions` nella barra degli indirizzi per aprire la pagina di Gestione delle Estensioni.

2. Clicca il selettore a fianco a `Modalità sviluppatore` per attivare la Modalità Sviluppatore. Questo ti permette di installare estensioni da una cartella o da un file.

   ![Screenshot della barra superiore del Gestore delle Estensioni](/assets/img/docs/developer-mode-toggle.png)

3. Dovresti veder comparire il pulsante `Carica estensione non pacchettizzata`. Cliccandolo potrai selezionare la cartella che vuoi caricare.

   ![Screenshot del pulsante Carica estensione non pacchettizzata](/assets/img/docs/load-unpacked-button.png)

4. Seleziona la cartella che hai estratto.
5. L'estensione dovrebbe essere ora caricata.

Per completare l'aggiornamento (assumendo che tu abbia seguito i passi di aggiornamento descritti [qui](#cloning-the-repository)), clicca il pulsante `Aggiorna`:

![Screenshot pulsante Aggiorna](/assets/img/docs/update-button.png)


### Installazione per Mozilla Firefox

1. Digita `about:debugging` nella barra dell'indirizzo per aprire la pagina di debug.

2. Clicca `Questo Firefox` nel menu a sinistra.

   ![Screenshot del menu sinistro](/assets/img/docs/left-hand-menu.png)

4. Clicca `Carica componente aggiuntivo temporaneo...`.

   ![Screenshot pulsante Carica componente aggiuntivo temporaneo](/assets/img/docs/load-addon.png)

6. Seleziona il file manifest.json nella cartella che hai estratto.
7. L'estensione dovrebbe essere ora caricata.

Nota: gli add-ons temporanei di Firefox sono effettivamente temporanei. Quando si riavvia Firefox vengono rimossi, quindi se hai bisogno di usare ogni volta la versione di sviluppo degli Scratch Addons ti suggeriamo di usare un browser basato su Chromium come ad esempio Google Chrome.

