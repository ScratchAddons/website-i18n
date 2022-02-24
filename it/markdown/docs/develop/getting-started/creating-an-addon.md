---
title: Creare un Addon
---
Requisiti software: editor di testo, Chrome.  
Se possibile, per evitare problemi disabilita l'estensione Scratch Addon che hai scaricato dallo store prima di procedere.

## Passo 1: Leggi le [informazioni di base sugli addon](/docs/develop/getting-started/addon-basics/)
Assicurati di leggere quel paragrafo per acquisire familiarità con la terminologia.

## Passo 2: Forka/clona il repository
Oppure scaricalo come ZIP, se preferisci. In altre parole, scarica il codice sorgente localmente.

## Passo 3: Carica l'estensione in Chrome
*Nota: Chrome è raccomandato per lavorare con gli addon. Ciononostante, gli addon dovrebbero funzionare anche in Firefox.*  
Ora che hai l'estensione nel tuo filesystem, vai a `chrome://extensions` e abilita la "modalità sviluppatore".  
Clicca "carica estensione non pacchettizzata", poi seleziona la cartella dove si trovano gli Scratch Addon. Nel caso dovessi incontrare problemi, assicurati di selezionare la cartella dove si trova il file `manifest.json`.  
E' tutto, hai caricato l'estensione! Dovrebbe somigliare a questo:  
![image](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)  
Nota: puoi ignorare tranquillamente il messaggio "errors". E' solo un avvertimento per una chiave non riconosciuta nel file manifest necessaria per Firefox.

## Passo 4: Cosa farà il tuo addon?
Ora arriva la parte divertente! 
Cosa farà il tuo addon? Pensa ad un ID per l'addon che sia autodescrittivo (no spazi o caratteri speciali, ad eccezione dei trattini). 
Capito?

## Passo 5: Crea una cartelle per l'addon
Usando un file explorer vai alla cartella dove hai salvato Scratch Addon nel tuo filesystem. Localizza la cartella `addons`. 
Ora crea una nuova cartella chiamata come l'ID del tuo addon.

## Passo 6: Aggiungi il file manifest
Il manifest dell'addon dice a Scratch Addon come funziona il tuo addon. Assicurati che non ci siano errori per evitare problemi.  
Dentro la cartella che hai appena creato, crea un file `addon.json`. 
Questo è quello che ti serve per iniziare a scrivere il tuo codice, assicurati di adattarlo alle tue esigenze future:
```json
{
  "name": "Epico testo segnaposto del nome dell'addon",
  "description": "Ciao a tutti! Sarebbe perfetto rimpiazzare questo testo segnaposto con una descrizione.",
  "tags": ["community"],
  "enabledByDefault": false
}
```
Per ulteriori informazioni su cosa puoi inserire nel manifest, vai a [questo articolo](/docs/reference/addon-manifest/).


## Passo 7: Indica a Scratch Addon quale è l'ID del tuo addon
Scratch Addon non è in grado di trovare le nuove cartelle da solo, devi aggiungerne il nome in un file speciale.  
Vai a `scratchAddonsFolder/addons/addons.json` e aggiungi l'ID del tuo addon all'array.

## Passo 8: Hello world
Il tuo addon per ora non fa ancora nulla, quindi questo è un buon momento per verificare che tutto quello che abbiamo fatto finora funzioni correttamente.  
Vai a `chrome://extensions` e ricarica Scratch Addon cliccando il simbolo di aggiornamento nel suo riquadro.  
Ora clicca con il tasto destro l'icona di Scratch Addon e seleziona "opzioni".  
Dovresti vedere il tuo addon nella lista! Quando lo trovi abilitalo e abilita tutte le impostazioni.

## Passo 9: La parte divertente: il codice!
*Prima di procedere assicurati di leggere l'articolo del wiki linkato nel passo 1.*  

E ora arriva la parte divertente: crea i tuoi file JS o CSS!  
Suggerimento da professionisti: dopo aver fatto tutte le modifiche al tuo addon, assicurati di aggiornare l'estensione Scratch Addon come hai fatto nel passo 8.  

A seconda di cosa vuoi che il tuo addon faccia, dovresti dare un'occhiata alle seguenti pagine wiki:
- [Userscript](/docs/develop/addon-types/userscripts)
- [Userstyle](/docs/develop/addon-types/userstyles)

## Passo 10: Rendi il tuo addon personalizzabile
Se vuoi puoi rendere il tuo addon personalizzabile!  
Gli utenti del tuo addon potranno abilitare e disabilitare le impostazioni, inserire valori numerici e molto altro!  
Per iniziare vai alla pagina [come definire le impostazioni nel manifest dell'addon](/docs/reference/addon-manifest/#settings-object).  
Poi leggi la [documentazione di addon.settings](/docs/reference/addon-api/addon.settings) per imparare come accedere alle scelte utente negli userscript.

## Passo 11: Prima di pubblicare il tuo addon
Ora che il tuo addon funziona, assicurati che sia possibile aggiungerlo alla libreria degli addon.  
Assicurati che il manifest del tuo addon sia adatto, [trovi altre informazioni qui](/docs/reference/addon-manifest). Fai molta attenzione al nome, alla descrizione e ai tag del tuo addon. Assicurati di impostare `"enabledByDefault"` a `false` oppure rimuovilo.  
Assicurati che il tuo addon non interferisca negativamente con gli altri addon.  
Assicurati che il tuo codice sia comprensibile; commenti non indispensabili sono sempre meglio che nessun commento.

## Passo 12: Invia una richiesta di pull!
Se non lo hai già fatto, forka il repository, fai il commit del tuo nuovo addon e invia una richiesta di pull!  
Tieni conto che potremmo chiederti di fare dei cambiamenti ma che, probabilmente, accetteremo il tuo addon purché sia un minimo adatto.
