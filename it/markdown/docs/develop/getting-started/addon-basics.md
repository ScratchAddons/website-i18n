---
title: Informazioni di Base sugli Addon
---

## Ma cose quindi un addon?
Un addon è essenzialmente uno userscript, uno userstyle o una combinazione di questi due elementi. Se sono correlati, allora li rendiamo parte dello stesso addon sotto uno stesso nome. Ad esempio, l'addon "Scratch 3 Developer Tools" è composto da uno userscript che si occupa di aggiungere una casella di ricerca all'editor di Scratch e uno userstyle che aggiunge un CSS a quella casella.

## Cos'è uno userscript?
Uno userscript è del codice JavaScript che viene eseguito in associazione al codice contenuto in una scheda del browser. Puoi dire quando lo userscript viene eseguito, ad esempio soltanto nelle pagine dei progetti. Gli userscript sono simili ai content script delle estensioni del browser. Se hai già usato un manager di userscript noterai che sono essenzialmente la stessa cosa.
Gli userscript sono utili per cambiare il comportamento del sito di Scratch, ad esempio permettendo di aggiungere o rimuovere pulsanti dalla barra di navigazione.

## Cos'è uno userstyle?
Uno userstyle è simile ad uno userscript; puoi anche specificare dei pattern per gli URL. Tuttavia gli userstyle aggiungono dei CSS invece che JavaScript. Sono spesso usati in associazione con gli userscript per dare uno stile particolare agli elementi aggiunti, ma possono anche essere usati per cambiare lo stile degli elementi nativi di Scratch. In quest'ultimo caso vengono solitamente chiamati "temi".

## Concettualmente, cosa dovrebbe essere realizzato come addon?
Puoi chiederti se sia meglio creare un nuovo addon o modificarne uno esistente. 
Se 2 addon condividono alcuni degli elementi seguenti, probabilmente dovrebbero essere riuniti in un unico addon.
- Entrambi necessitano, o non necessitano, di permessi che richiedono l'interazione dell'utente (come avviene ad esempio per le notifiche).
- Condividono una buona parte del codice.
- L'utente si aspetterebbe da quell'addon entrambe le funzionalità.
- Se separati, interferirebbero l'uno con l'altro.

Ricorda che gli addon possono essere personalizzati dall'utente - l'aggiunta di nuove funzionalità non deve influenzare i precedenti utenti dell'addon, a meno che non venga fatto intenzionalmente.