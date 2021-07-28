---
title: Informazioni di Base sugli Addon
---

## Ma cose quindi un addon?
Un addon è una combinazione di almeno uno dei seguenti elementi: script persistenti, userscript e userstyle. Se sono correlati, allora li rendiamo parte dello stesso addon sotto uno stesso nome. Ad esempio, l'addon "Scratch 3 Developer Tools" è composto da uno userscript che si occupa di aggiungere una casella di ricerca all'editor di Scratch e uno userstyle che aggiunge un CSS alla casella.

## Cos'è uno script persistente?
Uno script persistente non è altro che codice JavaScript che viene eseguito in background continuamente, anche quando l'utente non sta usando la scheda in cui viene eseguito Scratch. Sono utili ad esempio per segnalare all'utente che c'è stato un aggiornamento sul sito di Scratch. Gli script persistenti sono simili agli script di background nelle estensioni del browser.

## Cos'è uno userscript?
Uno userscript non è altro che codice JavaScript che viene eseguito in associazione alla scheda del browser in cui viene eseguito Scratch. A differenza degli script persistenti puoi dire quando lo userscript viene eseguito. Gli userscript sono simili ai content script delle estensioni del browser. Se hai già usato un manager di userscript noterai che sono essenzialmente la stessa cosa.
Gli userscript sono utili per cambiare il comportamento del sito di Scratch, ad esempio permettendo di aggiungere o rimuovere pulsanti dalla barra di navigazione.

## Cos'è uno userstyle?
Uno userstyle è simile ad uno userscript; puoi anche specificare dei pattern per gli URL. Tuttavia gli userstyle aggiungono dei CSS invece che JavaScript. Sono spesso usati in associazione con gli userscript per dare uno stile particolare agli elementi aggiunti, ma possono anche essere usati per cambiare lo stile degli elementi nativi di Scratch. In quest'ultimo caso vengono solitamente chiamati "temi".

## Concettualmente, cosa dovrebbe essere realizzato con un addon?
Puoi chiederti se sia meglio create un nuovo addon o modificarne uno esistente. 
Se 2 addon condividono alcuni degli elementi seguenti, probabilmente dovrebbero essere riuniti in un unico addon.
- Entrambi necessitano, o non necessitano, di permessi che richiedono l'interazione dell'utente (come avviene ad esempio per le notifiche).
- Condividono una buona parte del codice.
- L'utente si aspetterebbe da quell'addon entrambe le funzionalità.
- Se separati, interferirebbero l'uno con l'altro.

Ricorda che gli addon possono essere personalizzati dall'utente - l'aggiunta di nuove funzionalità non deve influenzare i precedenti utenti dell'addon, a meno che non venga fatto intenzionalmente.