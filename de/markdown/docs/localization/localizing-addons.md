---
title: Addons übersetzen
description: Addons zu übersetzen ist einfach.
---
Addons zu übersetzen ist einfach.

## Nachrichten hinzufügen
Erstelle eine Datei namens `ADDONID.json`, wobei ADDONID die ID des Addons ist (der Ordnername), unter `addons-l10n/en`. Schreibe die Nachrichten, die du übersetzen willst, hier:

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

### Platzhalter
Manchmal müssen Nachrichten dynamisch generierte Teile haben, z.B. Anzahl Katzen, oder Benutzereingabe. Um das zu machen, kannst du Platzhalter wie `{platzhalterName}` nutzen. Der Platzhaltername sollte nur Buchstaben enthalten (keine Zahlen).

### Mehrzahl
Was, wenn der Platzhalter eine Zahl ist? Wir können Mehrzahlen, wie `{platzhalterName, plural, one {wenn es eine Sache gibt} other {wenn es # Sachen gibt}}`. Wenn der Platzhalter 1 ist, wird "wenn es eine Sache gibt" angezeigt, sonst wird "wenn es (Platzhalter) Sachen gibt" angezeigt.

### Developer comments

Transifex will display the developer comment when a translator has selected the specified string. These comments are usually used to ask for a particular translation of the string or to provide additional information for languages that do not differentiate between uppercase and lowercase characters.

## Die Übersetzungen verwenden
Ändere die erste Zeile deines Userscripts von etwas wie:
```
export default async function ({ addon, console }) {
```

zu:
```
export default async function ({ addon, console, msg }) {
```

Das hinzugefügte `msg` ist die Funktion, die du nutzt, um Übersetzungen zu bekommen. Zum Beispiel, `text = "Miau"` kann jetzt `text = msg("meow")` sein. Die Addon-ID und der Slash wird nicht genutzt.

### Platzhalter
Du kannst Platzhalterwerte vergeben:
```js
cat = msg("cats", {number: 1}) // zeigt "1 cat"
cats = msg("cats", {number: 3}) // zeigt "3 cats"
hungry = msg("eat", {food: "cod"}) // zeigt "I want to eat cod!"
```

Du kannst Nachrichten auch "verschachteln":
```js
hungry2 = msg("eat", {food: msg("salmon")}) // zeigt "I want to eat salmon!"
```

### Sicherheit
Wenn du HTML schreibst,sollte `msg` mit dem sichererem `safeMsg` ersetzt werden.
