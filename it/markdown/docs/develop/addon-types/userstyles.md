---
title: Userstyle
description: Gli userstyle permettono di aggiungere dei CSS nel sito di Scratch website - utile per rendere colorati i pulsanti che aggiungi con i tuoi userscript o per personalizzare elementi nativi di Scratch.
---
## Cosa sono?
Gli userstyle permettono di aggiungere dei CSS nel sito di Scratch website - utile per rendere colorati i pulsanti che aggiunti con i tuoi userscript o per personalizzare elementi nativi di Scratch.

## Come si fa ad aggiungere uno userstyle?
**Assicurati di aggiornare Scratch Addon in `chrome://extensions` dopo avere apportato qualunque cambiamento al tuo addon.**  
Vai al manifest del tuo addon (addon.json) e aggiungi una proprietà chiamata `userstyles"`.  
Questa proprietà deve essere un array.  
Ogni elemento dell'array deve avere le seguenti proprietà: `"url"` e `"matches"`.  
`"url"` deve essere un URL relativo ad un file CSS.  
`"matches"` deve essere un array di URL a cui vuoi aggiungere il tuo userstyle. Puoi usare asterischi come caratteri jolly.
Esempio di manifest:
```json
{
  "name": "Scratch Messaging",
  "description": "Provides easy reading and replying to your Scratch messages.",
  "userstyles": [
    {
      "url": "userstyle.css",
      "matches": ["https://scratch.mit.edu/*"]
    },
    {
      "url": "second_userstyle.css",
      "matches": ["https://scratch.mit.edu/projects/*", "https://scratch.mit.edu/users/*"]
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```

## Debug degli userstyle
**Assicurati di aggiornare Scratch Addon in `chrome://extensions` dopo avere apportato qualunque cambiamento al tuo addon.** 
Se vedi che i tuoi userstyle non funzionano assicurati che il tuo addon sia abilitato. 
Se riscontri ancora problemi, crea una segnalazione in questo repository.
