---
title: Installazione
---

## Dagli store di estensioni

Scratch Addons è disponibile sia nel Chrome Web Store sia in Add-ons per Firefox.

- Chrome Web Store (per Google Chrome, Opera, Brave, Vivaldi, Microsoft Edge (>79) e altri brower basati su Chromium)  
  https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco  
- Add-ons per Firefox (per Mozilla Firefox)  
  https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/  


## Dal codice sorgente

### Info sulle release di GitHub

[La pagina delle release](https://github.com/ScratchAddons/ScratchAddons/releases) contiene il codice e i file per l'installazione per tutti i build dello sviluppo di Scratch Addons, nonché il mirror dei build presenti negli store.

### Clonare il repository

Questo è il modo raccomandato di installare Scratch Addon per scopi di sviluppo. Assume che tu abbia già installato Git.

Per scaricare il repository basta clonare `https://github.com/ScratchAddons/ScratchAddons.git`.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
Per aggiornare Scratch Addon `cd` nella sua cartella e poi esegui i comandi seguenti.

```sh
$ git fetch
$ git pull
```

Questo aggiornerà Scratch Addons e lo preparerà per le successive modifiche al codice. Nota che dovrai consultare le sezione per il completamento dell'aggiornamento che trovi [here](#install-on-google-chrome) se stai usando Google Chrome.


### Scaricamento del file zip

Se non hai installato Git puoi provare questo metodo alternativo. Nota che dovrai ripetere manualmente questo processo ogni volta che vuoi aggiornare Scratch Addon.

1. Vai al [repository](https://github.com/ScratchAddons/ScratchAddons) e localizza il pulsante per lo scaricamento del codice.

   ![Screenshot del pulsante per lo scaricamento del codice](/assets/img/docs/download-code-button.png)

2. Cliccalo e seleziona "Scarica ZIP".

   ![Screenshot del pulsante Scarica ZIP](/assets/img/docs/download-zipball-button.png)

3. Estrai il file zip nella cartella.

### Installazione su Google Chrome

1. DIgita `chrome://extensions` nella barra degli indirizzi per aprire la pagina di Gestione delle Estensioni.

2. Clicca il selettore a fianco a `Modalità sviluppatore` per attivare la Modalità sviluppatore. Questo ti permette di installare estesioni da una cartella o da un file.

   ![Screenshot della barra superiore del Gestore delle Estensioni](/assets/img/docs/developer-mode-toggle.png)

3. Dovresti veder apparire il pulsante `Carica estensione non pacchettizzata`. Cliccandolo potrai selezionare la cartella da caricare.

   ![Screenshot del pulsante Carica estensione non pacchettizzata](/assets/img/docs/load-unpacked-button.png)

4. Seleziona la cartella dove l'hai estratta.
5. L'estensione dovrebbe ora essere caricata.

Per completare l'aggiornamento (assumendo che tu abbia seguito i passi di aggiornamento descritti [qui](#cloning-the-repository)), clicca il pulsante `Aggiorna`:

![Screenshot pulsante Aggiorna](/assets/img/docs/update-button.png)


### Installazione su Mozilla Firefox

1. Digita `about:debugging` nella barra dell'indirizzo per aprire la pagina di debug.

2. Clicca `Questo Firefox` nel menu a sinistra.

   ![Screenshot del menu sinistro](/assets/img/docs/left-hand-menu.png)

4. Click `Carica Add-on Temporaneo...`.

   ![Screenshot pulsante Carica Add-on Temporaneo](/assets/img/docs/load-addon.png)

6. Seleziona il file manifest.json file nella cartella estratta.
7. L'estensione dovrebbe essere ora caricata.

Nota: gli add-ons temporanei di Firefox sono effettivamente temporanei. Riavviare Firefox li rimuove, quindi se vuoi usare ogni volta la versione di sviluppo degli Scratch Addons suggeriamo di usare un browser basato su Chromium come ad esempio Google Chrome.

