---
title: Localizzazione degli Addon
description: Localizzare gli addon è semplice.
---
Localizzare gli addon è semplice.

## Aggiungere messaggi
Nella cartella `addons-l10n/en/`, crea un file chiamato `ADDONID.json`, dove ADDONID è l'ID dell'addon (il nome della cartella). Scrivi lì i messaggi che vuoi tradurre:

```json
{
  "ADDONID/meow": "Meow",
  "ADDONID/cats": "{number, plural, one {1 cat} other {# cats}}",
  "ADDONID/eat": "I want to eat {food}!",
  "ADDONID/salmon": "salmon",
  "ADDONID/sardine": "sardine",
  "ADDONID/move-steps": {
    "string": "move {number} steps",
    "developer_comment": "Please translate this to match Scratch's official translation for the block."
  }
}
```

### Segnaposto
Alcuni messaggi hanno delle parti che sono generate dinamicamente. Ad esempio, il numero di gatti o di input. In questi casi puoi usare dei segnaposto come `{nomeSegnaposto}`. Il nome del segnaposto deve contenere solo lettere (non numeri).

### Plurali
E se il segnaposto è un numero? Possiamo definire i plurali come in `{nomeSegnaposto, plural, one {quando c'è una cosa} other {quando ci sono # cose}}`. Se il segnaposto vale 1, mostrerà "quando c'è una cosa", altrimenti dirà "quando ci sono (segnaposto) cose".

### Commenti dello sviluppatore

Transifex mostrerà il commento dello sviluppatore quando un traduttore seleziona la stringa. Questi commenti vengono solitamente usati per richiedere traduzioni specifiche per la stringa o per fornire ulteriori informazioni per le lingue che non fanno differenza tra caratteri maiuscoli e minuscoli.

## Usare le traduzioni
Cambia la prima linea del tuo userscript da:
```
export default async function ({ addon, console }) {
```

a:
```
export default async function ({ addon, console, msg }) {
```

L'argomento `msg` aggiunto è la funzione che puoi usare per ottenere la traduzione. Ad esempio, `text = "Meow"` diventa ora `text = msg("meow")`. L'ID dell'addon e lo slash vengono omessi.

### Segnaposto
Puoi assegnare valori ai segnaposto:
```js
cat = msg("cats", {number: 1}) // mostra "1 gatto"
cats = msg("cats", {number: 3}) // mostra "3 gatti"
hungry = msg("eat", {food: "cod"}) // mostra "Voglio mangiare merluzzo!"
```

Puoi anche "annidare" i messaggi:
```js
hungry2 = msg("eat", {food: msg("salmon")}) // mostra "Voglio mangiare salmone!"
```

### Sicureza
Se stai scrivendo del semplice HTML, `msg` dovrebbe essere rimpiazzata con la sua versione più sicura `safeMsg`.
