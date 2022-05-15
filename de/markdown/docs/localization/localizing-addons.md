---
title: Addons übersetzen
description: Addons zu übersetzen ist einfach.
---
Addons zu übersetzen ist einfach.

## Nachrichten hinzufügen
Under `addons-l10n/en/`, make a file named `ADDONID.json`, where ADDONID is the addon's ID (the folder name). Write your messages that you want to translate there:

```json
{
  "ADDONID/miau": "Miau",
  "ADDONID/Katzen": "{Nummer, plural, eine {1 Katze} viele {# Katzen}}",
  "ADDONID/essen": "Ich will {Nahrung} essen!",
  "ADDONID/Lachs": "Lachs",
  "ADDONID/Sardine": "Sardine"
}
```

### Platzhalter
Sometimes messages need to have things that are dynamically generated. For example, number of cats, or input. To handle this, you can use placeholders like `{placeholderName}`. Placeholder name should only contain letters (no numbers).

### Mehrzahl
What if the placeholder is a number? We can use plurals like `{placeholderName, plural, one {when there is one thing} other {when there are # things}}`. If the placeholder is 1, it will show "when there is one thing", otherwise it says "when there are (placeholder) things".

## Die Übersetzungen verwenden
Change your userscript's first line from something like:
```
export default async function ({ addon, console }) {
```

zu:
```
export default async function ({ addon, console, msg }) {
```

The `msg` added is the function you use to get translations. For example, `text = "Meow"` can now be `text = msg("meow")`. The addon ID and the slash is omitted.

### Platzhalter
Du kannst Platzhalterwerte vergeben:
```js
cat = msg("cats", {number: 1}) // shows "1 cat"
cats = msg("cats", {number: 3}) // shows "3 cats"
hungry = msg("eat", {food: "cod"}) // shows "I want to eat cod!"
```

You can also "nest" messages:
```js
hungry2 = msg("eat", {food: msg("salmon")}) // shows "I want to eat salmon!"
```

### Sicherheit
If you are writing raw HTML, `msg` should be replaced with safer version of `safeMsg`.
