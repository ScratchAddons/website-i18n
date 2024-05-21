---
title: Suggerimenti per il debug
description: Suggerimenti per debuggare facilmente gli userstyle e casi limite di cui tener conto.
---

Suggerimenti per debuggare facilmente gli userstyle e casi limite di cui tener conto.

## Suggerimenti

### Non sempre è necessario ricaricare l'estensione

Quando cambi il sorgente di un file JavaScript o CSS che esiste già non è necessario ricaricare l'estensione andando alla pagina `chrome://extensions`. In questi casi è sufficiente ricaricare la pagina.

### Usa l'API addon.* nella console

The `addon` object is accessible within the browser console through the `__addon` global variable when at least one addon is running.

### Imposta i punti di interruzione usando la keyword "debugger"

la keyword `debugger;` blocca la pagina quando viene eseguita se gli strumenti per gli sviluppatori sono aperti. Impostare dei punti di interruzione è utile per ispezionare durante l'esecuzione il valore delle variabili locali.

### Filtrare i messaggi delle console per ID degli addon

Inserisci l'ID dell'addon ID nella barra di ricerca "filter" della console per vedere solo log e warning o errori inseriti nella console con `console.error()`. Ricorda che questa nasconderà tutte le eccezioni a meno che tu nel tuo codice non le stia loggando esplicitamente.


## Casi limite


### Pagina e editor dei progetti di Scratch


#### Il DOM viene distrutto quando si entra o si esce dall'editor

Scratch crea tutti gli elementi HTML ogni volta che l'utente clicca "guarda dentro" o "vai alla pagina del progetto" e distrugge quelli vecchi.  
Questo problema può essere risolto usando `addon.tab.waitForElement` o l'evento `urlChange`.

#### La lingua dell'editor di Scratch può essere cambiata senza dover ricaricare la pagina

Diversamente dal sito di Scratch, l'editor di Scratch non si ricaricherà quando si chiama la lingua. Quando si seleziona una lingua diversa Scratch potrebbe distruggere e ricreare alcuni elementi HTML.

#### Altre situazioni da tener presente

- L'editor di progetti può essere usato senza un ID di progetto definito (ad esempio quando non si è loggati al sito).
- L'editor potrebbe passare dal LTR a RTL (o viceversa) senza che sia necessario ricaricare la pagina.


### Il sito di Scratch

#### le pagine di scratch-www non si ricaricano dopo che si è acceduto al sito

Diversamente dalle pagine di scratchr2, le pagine di scratch-www pages non forzano un ricaricamento della pagina dopo che si è acceduto al sito. Ad esempio, se vai alla pagina di un progetto dopo aver fatto il logout, poi fai il login, la pagina non sarà ricaricata. Questo riguarda anche la gallerie, la pagina dei messaggi, ecc.  
Invece tutte le pagine di Scratch vengono ricaricate dopo un logout.

#### Le pagina dei progetti non restituiscono mai un errore 404

Anche se il progetto non è più condiviso o non esiste, Scratch restituisce sempre il codice di stato HTTP 200. Il messaggio "our server is Scratch'ing its head" è aggiunto dinamicamente alla pagina dal server di Scratch.

#### Altre situazioni da tener presente

- Le 4 schede dentro le pagine delle gallerie ha URL diversi, ma non avviano una navigazione nel browser. Tutti gli addons che gestiscono una qualunque delle 4 pagine vengono quindi eseguiti, indipendentemente da quale sia l'URL iniziale.
