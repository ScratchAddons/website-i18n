---
---

**Modalità alto framerate** è un addon che permette di personalizzare la velocità di esecuzione dei progetti perché sia maggiore del valore predefinito di 30 FPS. L'effetto è che l'esecuzione del progetto appare più fluida e veloce rispetto al valore FPS predefinito; quindi il valore di 60FPS farà eseguire il progetto al doppio della velocità.

La funzionalità può essere velocimente attivata/disattivata tenendo premuto `alt` mentre si clicca la bandiera verde. La bandierà diventerà blu e comparirà sopra un'icona gialla di avanzamento veloce, ad indicare che il progetto è in esecuzione ad una velocità maggiore.

## Funzionalità

- La funzionalità dell'addon è attivata quando l'utente clicca la bandiera verde mentre tiene premuto il tasto `alt`. E' invece disattivata ogni volta che la pagina viene aperta/aggiornata.
- L'addon funziona sia nella pagina dei progetti che nell'editor.
- Per impostazione predefinita, l'addon (quando attivato) porta il framerate del progetto a 60 FPS. Questo valore può essere portato nelle impostazioni dell'addon ad un valore compreso tra 31 e 240.

## Impostazioni

### FPS predefinito

Definisce il valore del framerate quando l'addon è attivato.

## Sviluppi futuri

- L'addon potrebbe essere segnalato come a rischio di rallentare i progetti che lo richiedono quando vengono eseguiti sul sito di Scratch. [#6860](https://github.com/ScratchAddons/ScratchAddons/issues/6860) 
- Siccome l'attivazione dell'addon richiede di mantenere premuto il tasto `alt`, l'addon non è compatibile con i dispositivi touch. Una possibile soluzione potrebbe essere quella di aggiungere un menu contestuale alla bandiera verde per questo e altri addon. [#7230](https://github.com/ScratchAddons/ScratchAddons/issues/7230) 

## Crediti

Jeffalo ha creatol'addon originale che porta il player a 60 FPS. TheColaber ha aggiunto la personalizzazione degli FPS e ha eliminato alcuni bug. L'icona della bandiera verde accessibile è stata creata da JoanRiosiPla ed è poi stata rivista da WorldLanguages.

## Changelog

- **v1.1.0** L'addon **60FPS Player Mode** è stato creato.
- **v1.3.0** L'addon viene ora attivato per impostazione predefinita per tutti gli utenti e ha ricevuto l'etichetta Raccomandato.
- **v1.7.0** Aggiunta opzione per personalizzare gli FPS, inizialmente fissati a 60.
- **v1.11.0** L'addon viene rinominato **Modalità player Alt+Bandiera Verde 60FPS**, e viene aggiunto un breve riquadro di informazioni. Viene importato un limite al valore personalizzato di FPS, che ora può variare tra 31 e 240.
- **v1.13.0** Viene miglioarata la rilevazione della combinazione`Alt` + bandiera verde. L'addon può essere ora attivato e disattivato dinamicamente.
- **v1.14.0** Viene assegnata all'addon l'etichetta Player dei Progetti.
- **v1.18.0** L'addon viene rinominato **Modalità player progetti 60FPS**. L'addon può ora essere attivato anche in progetti inclusi.
- **v1.24.0** Correzione bug: L'addon non perde più traccia dello stato quando si passa dalla pagina dei progetti all'editori.
- **v1.26.0** Correzione bug: L'addon non causa più il non aggiornamento visuale delle variabili in alcuni casi.
- **v1.30.0** L'addon non viene più attivato per impostazione predefinita per tutti gli utenti.
- **v1.34.0** Un'icona gialla di avanzamento veloce è aggiunta alla bandiera verde quando l'addon è attivo. Il contenuto del riquadro informazioni è stato riscritto per chiarire che alcuni progetti potrebbero non compartarsi correttamente quando l'addon è attivo.
- **v1.26.0** L'addon viene rinominato **Modalità framerate superiore**. La descrizione dell'addon e il contenuto del box informazioni viene riscritto per renderlo più chiaro.
- **v1.37.0** Un secondo riquadro informazioni viee aggiunto per spiegare i problemi che si possono riscontrare con la modalità riasparmio di energia dei dispositivi degli utenti.

## Trivia

- Sebbene gli Addon di Turbowarp non includano questo addon, le impostazioni avanzate dei progetti di Turbowarp permettono di personalizzare il framerate in un modo simile.
- A dispetto del fatto che la personalizzazione degli FPS è limitata a valori tra 31 e 240, il player di progetti di Scratch funziona perfettamente sia con valori inferiori che superiori! Ci sono alcuni modi di superare questo limite, in quanto soltanto le caselle delle impostazioni dell'addon impongono queste restrizioni.
- Jeffalo ha aggiunto l'addon perché "è dannatamente fico"[^1]
- C'è un metodo per i progetti Scratch di rilevare approssimativamente un FPS personalizzato, il che può indicare che l'addon è attivo.[^2]

## Galleria

{{< docs/stub-section >}}

## Correlati

{{< docs/stub-section >}}

[^1]: https://github.com/ScratchAddons/ScratchAddons/pull/383#issue-714126835
[^2]: https://en.scratch-wiki.info/wiki/Making_an_FPS_Counter