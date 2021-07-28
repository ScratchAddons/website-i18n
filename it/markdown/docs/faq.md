---
title: Domande Frequenti
description: Questa pagina elenca le domande frequenti sull'estensione e sul progetto Scratch Addon.
---

Questa pagina elenca le domande frequenti sull'estensione e sul progetto Scratch Addon.

### Cos'è Scratch Addon?

Scratch Addon è un'estensione del browser che raccoglie e rende disponibili nuove funzionalità e nuovi temi (chiamati addon) per il sito web e l'editor di progetti di Scratch. L'obiettivo è quello di riunificare tutte le estensioni, gli userstyle e gli userscript sviluppati da membri della comunità di  Scratch in un unico strumento, pur lasciando gli utenti liberi di scegliere quali desiderano attivare.

### Ma cos'è quindi esattamente un "addon"?

Un addon è simile ad un'estensione o uno userscript, ma usa le speciali API rese disponibili dall'estensione Scratch Addon. Queste API permettono agli addon di eseguire script in una pagina di Scratch (userscript), di eseguire script in background (script persistenti) o di applicare degli stili al sito di Scratch (userstyle).

Gli userscript e gli script persistenti possono usare le API `addon.*` che permettono di ottenere informazioni su Scratch (ad esempio ricavare il nome dell'utente collegato) e di usare le API dell'estensione (ad esempio per inviare notifiche). 

### Se tutto è un addon allora cosa fa Scratch Addon?

Di per sé Scratch Addon è soltanto un caricatore di addon. I suoi compiti principali sono:

- Permettere agli utenti di abilitare, disabilitare e configurare gli addon.
- Eseguire gli addon e rendere disponibili le loro API.
- Rendere disponibile uno stato globale per gli addon (ad esempio l'API addon.auth).
- Modificare i prototipi degli oggetti di base per poter essere usati con gli userscript degli addon.
- Rendere accessibile e modificabile lo stato della libreria Redux.
- Evitare che gli addon interferiscano tra di loro.
- Evitare la sovrapposizione di funzionalità in addon diversi.

### Scratch Addon è sicuro?

Si. Scratch Addon non dovrebbe avere nessun problema di sicurezza nella sua versione più recente. Scratch Addon è un progetto opensource, quindi il codice è constantemente verificato da chi contribuisce al codice di Scratch Addon ma anche da chi rivede i contenuti del Web Store di Chrome e degli Add-on di Firefox. 

### Come posso segnalare una vulnerabilità?

Se ti capita di trovare una vulnerabilità contatta subito World_Languages in privato scrivendo a `worldxlanguages (at) gmail.com`. Se non ricevi una risposta in 48 ore crea una segnalazione [qui](https://github.com/ScratchAddons/ScratchAddons/issues/) specificando che hai inviato un'email.

Puoi [leggere la nostra policy sulla sicurezza](https://github.com/ScratchAddons/ScratchAddons/security/policy) o [controllare gli avvisi di sicurezza che abbiamo pubblicato](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### Il mio account sarà al sicuro quando uso Scratch Addon?

Scratch Addon non usa le tue credenziali per funzionare. Infatti Scratch Addon continuerà a funzionare anche se ti scolleghi da Scratch. Scratch Addon invierà solo richieste basate sui cookie che vengono resi disponibili dal browser ad ogni richiesta, quindi, anche se alcuni addon come Scratch Messaging non funzioneranno quando ti stai collegando, questo non interferirà con altre parti dell'estensione.

Gli addon di Scratch Addon sono stati verificati da molti tra coloro che hanno contribuito al repository, quindi nessuno può far scivolare del codice nocivo sotto i nostri occhi.

Non inviamo mai informazioni e impostazioni delle estensioni al di fuori del browser. Vai alla [politica della privacy dell'estensione](/docs/privacy/policies/extension) per ulteriori informazioni.

### Posso informare gli altri dell'esistenza di Scratch Addon sul sito di Scratch?

Non puoi, quindi ti preghiamo di non farlo. C'è una politica di Scratch che proibisce di fare pubblicità sul sito di Scratch a estensioni del browser o userscript [qui](https://scratch.mit.edu/discuss/post/2907564/). Puoi tuttavia usare altri metodi per far sapere ai tuoi amici di Scratch Addon.

### In che modo posso contribuire a Scratch Addon?

Prima di tutto ti ringraziamo per il tuo interesse nel contribuire a Scratch Addon. Apprezziamo il tuo interesse e i tuoi futuri contributi.

Essendo un progetto opensource, qualunque tipo di contributo è il benvenuto. Non devi chiederci il permesso o aver acquisito un qualche livello. Chiunque è il benvenuto. Potresti anche aver già contribuito al progetto senza essertene accorto!

Ma torniamo alla domanda. Puoi contribuire in diversi modi, alcuni davvero molto semplici.

- **Contribuisci del codice**

  Se sai programmare in Javascript, HTML5 e CSS puoi contribuire programmando. Puoi correggere bug, farti carico di qualche richiesta o creare il tuo addon.

  Una volta finito dovrai creare una richiesta di pull. Puoi farlo creando un fork del [repository](https://github.com/ScratchAddons/ScratchAddons/), facendo le tue modifiche e creando poi una richiesta di pull. Se è ritenuto fattibile, verrà inserito nel codice ufficiale.

  Sono disponibili anche altre forme di contributo. Puoi vedere i nostri repository nelle [pagine GitHub dell'organizzazione](https://github.com/ScratchAddons) e aiutarci a costruirli.

- **Suggerisci un'idea**  

  C'è qualcosa che pensi possa essere una buona aggiunta agli Addon di Scratch? [Faccelo sapere!](#i-think-you-missed-a-feature-what-can-i-do)

- **Segnala un bug**

  Hai trovato un bug in uno dei nostri addon, nella pagina delle impostazioni o in un qualunque altro punto della nostra estensione? [Segnala un bug](#what-can-i-do-if-i-find-a-problem).

- **Traduci Scratch Addon**  

  Se parli fluentemente un'altra lingua oltre all'Inglese, puoi aiutarci a tradurre/localizzare Scratch Addon nella tua lingua. Puoi cominciare da [qui](localization/joining-the-localization-team).

- **Scrivi la documentazione**

  Conosci bene Scratch Addon? In questo caso puoi aiutarci a scriverne la documentazione. Documentazione sia su come usarlo che su come funziona. Contattaci nella [nostra pagina di Discussione](https://github.com/ScratchAddons/ScratchAddons/discussions) per ulteriori informazioni.

- **Invia feedback**  

  Puoi inviarci del feedback usando il modulo che trovi alla [pagina del feedback](https://scratchaddons.com/feedback). Il tuo feedback può darci una diversa prospettiva nello sviluppo dell'estensione, ci aiuta a sapere cosa richiede attenzione e a correggere i bug.

- **Pubblica una recensione negli store**

  Puoi lasciare una recensione su Scratch Addon nella [pagina delle estensioni di Chrome](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) o nella [pagina degli addon di Firefox](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/).

- **Dai una stella al nostro repository**

  La stella su GitHub è simile alla stella per i favoriti di Scratch. Puoi farlo andando nel [nostro repository](https://github.com/ScratchAddons/ScratchAddons) e cliccando il pulsante "Stella" nell'angolo in alto a destra.

- **Spargi la voce**

  Puoi far sapere a chiunque di Scratch Addon. Ai tuoi amici, ai tuoi parenti, ai membri della tua famiglia o anche ai tuoi insegnanti se vuoi. Ti chiediamo soltanto di [non farlo sul sito di Scratch](#can-i-tell-people-about-scratch-addons-on-scratch).

### Come posso creare il mio addon?

Trovi ulteriori informazioni su come creare un addon per Scratch Addon [qui](/docs/develop/getting-started).

### Come posso mettere il mio nome alla [pagina di chi ha contribuito](/contributors)?

Leggi e segui le istruzioni [qui](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}) per avere il tuo nome nella pagina.

### Come posso togliere il mio nome dalla [pagina di chi ha contribuito](/contributors)?

Se non vuoi che il tuo nome compaia nella pagina di chi ha contribuito, faccelo sapere creando un issue nel [nostro repository di chi ha contribuito](https://github.com/ScratchAddons/contributors/issues/) o contattaci. Ci scusiamo per l'inconveniente.

### Cosa posso fare se scopro un problema?

Puoi farcelo sapere usando uno di questi metodi.

- Faccelo sapere usando il [nostro modulo del feedback](https://scratchaddons.com/feedback).
- Crea un issue nel [repository](https://github.com/ScratchAddons/ScratchAddons/issues).
- Crea un post nella [nostra pagina delle Discussioni](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Diccelo nel [nostro server Discord](https://discord.gg/R5NBqwMjNc).

### Penso che manchi una funzionalità. Cosa posso fare?

Se pensi che manchi una funzionalità o vuoi suggerire un addon per questa estensione o hai una buona idea, faccelo sapere [seguendo uno dei metodi menzionati qui sopra](#what-can-i-do-if-i-find-a-problem).

### Dove posso discutere di Scratch Addon?

Puoi farlo nella [nostra pagina delle Discussioni](https://github.com/ScratchAddons/ScratchAddons/discussions) o nel [nostro server Discord](https://discord.gg/R5NBqwMjNc). Lì puoi discutere di Scratch Addon e fare domande se hai problemi.

### Penso che Scratch Addon rallenti Scratch. Cosa posso fare?

Prova a disabilitare gli addon che non ti occorrono. Verifica anche le note e gli avvisi degli addon per decidere quali addon dovrebbero essere disabilitati per migliorare le performance. 

### Come posso abilitare l'addon dell'easter egg?

Per far comparire gli'addon easter egg, digita il codice Konami (↑↑↓↓←→←→BA) con la tua tastiera nella pagina delle impostazioni. Fatto questo gli addon easter egg compariranno, permettendoti di abilitarli.

Alcuni dei nostri addon easter egg sono "Correggi le maiuscole di Impostazioni Account" e "glitch del Punto e virgola". Guarda nella [scheda addon](/addons) per una lista completa.

### Ho altre domande!

Se hai altri domande per le quali cerchi risposte, puoi creare un post nella nostra [pagina delle Discussioni](https://github.com/ScratchAddons/ScratchAddons/discussions) o invia un messaggio nel [nostro server Discord](https://discord.gg/R5NBqwMjNc). Qualcuno proverà a risponderti.
