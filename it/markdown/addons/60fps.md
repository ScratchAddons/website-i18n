---
---

**Higher project framerate mode** is an addon that allows customization of the project's run speed to be faster.

Scratch normally iterates loops 30 times per second, resulting in a screen refresh rate of 30 frames per second (FPS). This addon can increase the iteration rate, thereby changing the framerate. This has the effect of making the project animate smoother but also run faster, relative to the custom FPS value; therefore, the default value of 60 FPS will essentially make the project run twice as fast.

Some projects adapt to framerate increases with techniques such as [delta time](https://en.wikipedia.org/wiki/Delta_timing), to run properly while maintaining smooth animations.

The feature can be toggled on/off by holding `alt` and clicking the green flag. The flag will turn blue and a yellow fast-forward icon will appear over it, indicating that the project is running at a faster speed.

## Funzionalità

- The addon's functionality is only enabled when the user activates it by holding `alt` and clicking the green flag. The addon's functionality is turned off every time the page is opened/refreshed.
- L'addon funziona sia nella pagina dei progetti che nell'editor.
- By default, the addon (when activated) sets the project's framerate to 60 FPS. This value can be changed in the addon's settings to a whole number ranging from 31 to 240.

## Impostazioni

### FPS predefinito

Definisce il valore del framerate quando l'addon è attivato.

## Sviluppi futuri

- L'addon potrebbe essere segnalato come a rischio di rallentare i progetti che lo richiedono quando vengono eseguiti sul sito di Scratch. [#6860](https://github.com/ScratchAddons/ScratchAddons/issues/6860) 
- Because enabling the addon requires holding the `alt` key, it is not compatible with touchscreen devices. A proposed solution is to add a context menu to the green flag for this addon and several others. [#7230](https://github.com/ScratchAddons/ScratchAddons/issues/7230)

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
