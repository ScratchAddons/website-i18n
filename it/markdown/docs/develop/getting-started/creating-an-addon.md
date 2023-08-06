---
title: Creare un Addon
---
Requisiti software: editor di testo, Chrome.  
Prima di procedere, per evitare problemi, disabilita se possibile l'estensione Scratch Addons che hai scaricato dallo store.


{{< admonition info >}}
Se stai pensando di proporci il tuo addon con una pull request sul nostro repository GitHub, leggi prima le nostre [linee guida per contribuire](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md). 

Nel caso non ci sia già un issue nel repository GitHub per l'addon che voi sviluppare,  [creane uno](https://github.com/ScratchAddons/ScratchAddons/issues/new/choose). Se invece c'è già un issue, ti suggeriamo di inserire un commento che indichi che hai intenzione di sviluppare l'addon. Questo permetterà agli altri contribuenti di dare un parere sul fatto che questo addon possa essere accettato o meno, o se è necessario discutere  ulteriormente su questo addon.

Se invece stai creando un addon per il tuo uso personale, puoi procedere usando questa guida.
{{< /admonition >}}

## Passo 1: Leggi le [informazioni di base sugli addon](/docs/develop/getting-started/addon-basics/)
Assicurati di leggere quell'articolo per acquisire familiarità con la terminologia.

## Passo 2: Forka/clona il [repository](https://github.com/ScratchAddons/ScratchAddons)
Segui [queste istruzioni](/docs/getting-started/installing/#from-source) per scaricare il codice sorgente sul tuo PC.

## Passo 3: Carica l'estensione in Chrome
*Nota: per lavorare con gli addon raccomandiamo l'uso di Chrome. Ciononostante, gli addon dovrebbero funzionare anche in Firefox e Edge.*  
Ora che hai l'estensione nel tuo filesystem, vai a `chrome://extensions` e abilita la "modalità sviluppatore".  
Clicca "carica estensione non pacchettizzata", poi seleziona la cartella di Scratch Addons. Nel caso dovessi incontrare problemi, assicurati di aver selezionato la cartella dove si trova il file `manifest.json`.  
E' tutto! Ora hai caricato l'estensione. Dovrebbe comparire come mostrato qui sotto:  
![image](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)  
Nota: puoi ignorare tranquillamente il messaggio "errors". E' solo un avvertimento per una chiave non riconosciuta nel file manifest che è necessaria per Firefox.

## Passo 4: Cosa vuoi che faccia il tuo addon?
Ora arriva la parte divertente! 
Cosa vuoi che faccia il tuo addon? Pensa ad un ID per il tuo addon che sia autodescrittivo (non usare spazi o caratteri speciali, ad eccezione dei trattini). 
Ci siamo?

## Passo 5: Crea una cartelle per l'addon
Usando un file explorer vai alla cartella dove hai salvato Scratch Addons nel tuo filesystem. Localizza la cartella `addons`. 
Ora crea una nuova cartella chiamata esattamente come l'ID del tuo addon.

## Passo 6: Aggiungi il file manifest dell'addon
Il file manifest dell'addon dice a Scratch Addons come funziona il tuo addon. Assicurati che non ci siano errori per evitare problemi difficili da scoprire.  
Dentro la cartella che hai appena creato, crea un file `addon.json`. 
Questo è quello che ti serve per iniziare a scrivere il codice, ma assicurati di adattarlo alle tue esigenze future:
```json
{
  "name": "Testo segnaposto del nome dell'addon",
  "description": "Ciao a tutti! Sarebbe perfetto rimpiazzare questo testo segnaposto con una descrizione.",
  "tags": ["community"],
  "enabledByDefault": false
}
```
Per ulteriori informazioni su cosa puoi mettere nel file manifest, leggi [questo articolo](/docs/reference/addon-manifest/).


## Passo 7: Indica a Scratch Addons quale è l'ID del tuo addon
Scratch Addons non è in grado di trovare le nuove cartelle da solo, quindi devi aggiungerne il nome in un file speciale.  
Vai a `scratchAddonsFolder/addons/addons.json` e aggiungi l'ID del tuo addon all'array.

## Passo 8: Hello world
Il tuo addon per ora non fa ancora nulla, quindi questo è un buon momento per verificare che tutto quello che abbiamo fatto finora funzioni correttamente.  
Vai a `chrome://extensions` e ricarica Scratch Addons cliccando il simbolo di aggiornamento che trovi nella sua scheda.  
Ora clicca con il tasto destro l'icona di Scratch Addons e seleziona "opzioni".  
Ora dovresti vedere il tuo addon nella lista! Appena lo trovi abilitalo, e abilitane tutte le impostazioni.

## Passo 9: La parte divertente: il codice!
*Prima di procedere assicurati di leggere l'articolo del wiki segnalato nel passo 1.*  

E ora arriva la parte divertente: crea i tuoi file JS o CSS!  
Suggerimento per professionisti: dopo aver modificato il tuo addon, assicurati di aggiornare l'estensione Scratch Addons come hai fatto al passo 8.  

A seconda di cosa vuoi che il tuo addon faccia, dovresti dare un'occhiata a queste pagine del wiki:
- [Userscript](/docs/develop/userscripts)
- [Userstyle](/docs/develop/userstyles)

## Passo 10: Rendi il tuo addon personalizzabile
Se vuoi puoi rendere il tuo addon personalizzabile!  
Gli utenti del tuo addon potranno abilitare e disabilitare le impostazioni, inserire valori numerici e molto altro!  
Per iniziare vai alla pagina [come definire le impostazioni nel file manifest dell'addon](/docs/reference/addon-manifest/#settings-object).  
Poi leggi la [documentazione di addon.settings](/docs/reference/addon-api/addon.settings) per imparare come accedere negli userscript alle impostazioni dell'utente.

## Passo 11: Prima di pubblicare il tuo addon
Ora che il tuo addon funziona, assicurati che sia possibile aggiungerlo alla libreria degli addon.  
Assicurati che il manifest del tuo addon sia ben fatto, [trovi qui altre informazioni](/docs/reference/addon-manifest). Fai molta attenzione al nome, alla descrizione e ai tag del tuo addon. Assicurati di impostare `"enabledByDefault"` a `false` oppure rimuovilo.  
Assicurati che il tuo addon non interferisca negativamente con gli altri addon.  
Assicurati che il tuo codice sia comprensibile; la presenza di commenti non indispensabili è sempre meglio che nessun commento.

## Passo 12: Invia una richiesta di pull!
Segui i passi che trovi nelle nostre [linee guida per contribuire al codice](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md). In poche parole, se non lo hai già fatto forka il repository, fai il commit del tuo addon a invia una richiesta di pull!  
Ricorda che potremmo richiederti di fare delle modifiche, ma che accetteremo il tuo addon sempre che sia idoneo.
