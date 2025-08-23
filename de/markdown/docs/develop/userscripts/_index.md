---
title: Benutzerskripte (Userscripts)
description: Userscripts sind Javascript-Dateien, die jedes Mal, wenn der Benutzer eine Scratchseite öffnet, ausgeführt werden. Sie können das HTML des Dokumentes verändern, neue Schaltflächen hinzufügen, das Verhalten des Scratcheditors verändern, und so viel mehr.
---

Userscripts sind Javascript-Dateien, die jedes Mal, wenn der Benutzer eine Scratchseite öffnet, ausgeführt werden. Sie können das HTML des Dokumentes verändern, neue Schaltflächen hinzufügen, das Verhalten des Scratcheditors verändern, und so viel mehr.

Userscripts für Scratch Addons sind, ähnlich wie Userscripts die du vielleicht für Userscriptmanager wie Tampermonkey oder Greasemonkey runterlädst, JavaScript-Programme, die in dem selben Kontext wie der Javascript-Code von Scratch ausgeführt werden. In Browsererweiterungsworten wird dieser Kontext oft "Hauptwelt" genannt.

Obwohl Scratch Addons-Userscripts Teil einer Browsererweiterung sind, können sie keine `chrome.*`- oder `browser.*`-APIs aufrufen. Stattdessen gibt Scratch Addons eine [`addon.*`-API](/docs/reference/addon-api) vor.


## Userscripts im Addon-Manifest deklarieren

{{< admonition warning >}}
**Einige Änderungen erfordern eine Erweiterungsneuladung** von `chrome://extensions`, um wirksam zu werden, wie z. B. die Aktualisierung der Addon-Manifestdatei.

Es ist nicht nötig, die Erweiterung neu zu laden, wenn man den Code einer schon existierenden Javascriptdatei ändern. In diesem Fall kannst du einfach die Seite neu laden.
{{< /admonition >}}

Userscripts werden in einem "userscripts"-Array deklariert.

Jedes Element dieses Arrays muss die folgenden Elemente haben:
- `"url"`: die relative URL zu einer Javascript-Datei
- `"matches"`: Die Liste von Scratchseiten, wo das Userscript ausgeführt wird. Siehe [matches](/docs/reference/addon-manifest/#matches) für mehr Informationen.

Beispielsmanifest:
```json
{
  "name": "Copy link to comment button",
  "description": "Adds a \"Copy Link\" button to all comments on the website, next to the \"Report\" button.",
  "userscripts": [
    {
      "url": "userscript.js",
      "matches": ["projects", "https://scratch.mit.edu/", "profiles", "studios"]
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```

## Erstellen deines ersten Benutzerskripts

Im Gegensatz zu Erweiterungsinhaltsskripten und Tampermonkey-Benutzerskripten musst du deinen gesamten Code in einem Standardexportmodul einschließen:
```js
// Beispiel-Benutzerskript
export default async function ({ addon, console }) {
  console.log("Hallo, " + await addon.auth.fetchUsername());
  console.log("Wie geht es dir heute?");
}
```

Denke daran, dass JavaScript es erlaubt, Funktionen innerhalb anderer Funktionen zu deklarieren, zum Beispiel:
```js
export default async function ({ addon, console }) {
  async function sayHelloToUser() {
    console.log("Hallo, " + await addon.auth.fetchUsername());
  }

  await sayHelloToUser();
  console.log("Wie geht es dir heute?");
}
```

{{< admonition info >}}
Du kannst auf viele `Addons*` zugreifen. API-Dienstprogramme aus Benutzerskripten. Du kannst beispielsweise den aktuellen Benutzernamen abrufen, warten, bis ein Element auf der Seite vorhanden ist, oder einen Verweis auf das Scratch VM-Objekt abrufen.

Weitere Informationen findest du unter der [API-Referenz](/docs/reference/addon-api/).
{{< /admonition >}}


## Ändern des Dokuments HTML

Verwende [Browser-DOM-APIs](https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API), um den HTML-Code der Seite anzupassen.

Hier ist ein Beispiel:
```js
const myButton = document.createElement("Button");
myButton.textContent = "Klicke auf mich!";
myButton.classList.add("button");
myButton.setAttribute("title", "Du hoverst über einen Button");

const myContainer = document.querySelector(".container");
myContainer.append(myButton);
```

## Lokalisierung von Benutzerskripten

Addon-Benutzerskripte müssen manchmal auf englische Wörter oder Sätze verweisen. Stelle sicher, dass du sie nicht fest programmieren, damit sie Teil des Übersetzungsprozesses sein können.

{{< admonition error >}}
```js
// Tu dies nicht:
document.querySelector(".sa-find-bar").placeholder = "Find blocks";
```
{{< /admonition >}}

Um eine übersetzbare Zeichenfolge zu erstellen, gehe folgendermaßen vor:
1. Erstelle eine Datei mit dem Namen `addon-id.json` im Ordner `/addon-l10n/en`.
2. Gebe für jede Zeichenfolge eine ID an:
```json
{
  "addon-id/find": "Find blocks"
}
```
3. Stelle sicher, dass die Funktion `msg()` in dem Benutzerskript importiert wird. Die erste Zeile des Benutzerskripts sollte wie folgt aussehen:
```js
export default async function ({ addon, console, msg  }) {
                                              // ^^^
```
4. Verwende die Funktion `msg()` in Ihrem Code anstelle einer fest codierten Zeichenfolge:
```js
document.querySelector(".sa-find-bar").placeholder = msg("find");
```

{{< admonition info >}}
Weitere Informationen zur Lokalisierung von Benutzerskripten findest du unter [dieser Seite](/docs/localization/localizing-addons/).
{{</admonition >}}


## Technische Details

Jede Benutzerskriptdatei ist ein JavaScript-Modul, das eine Funktion exportiert. Scratch Addons importiert das Modul nur bei Bedarf und führt es aus, nachdem die Seite vollständig geladen wurde.

Userscripts sind JavaScript-Module, daher laufen sie immer im ["strict mode"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode). Dies bedeutet auch, dass Benutzerskripte [Top-Level-Imports](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) verwenden können, um andere JavaScript-Dateien zu importieren.

The order in which userscripts run may vary on each page load. After page load, the user might dynamically enable some addons in a custom order, so order of execution is never guaranteed. Some APIs like [`addon.tab.appendToSharedSpace`](/docs/reference/addon-api/addon.tab/addon.tab.appendtosharedspace/) attempt to fix any potential race conditions and unexpected behavior when dynamically enabling addons.

### runAtComplete

Userscripts may opt-in into being executed before the page has fully loaded by specifying `"runAtComplete": false` in the addon manifest, once for each userscript.

As of now, only `document.head` is guaranteed to exist when running a userscript early. In the future, `document.body` will also be guaranteed to exist, so no userscripts will ever run before the HTML document loaded enough to reach `</head> <body>`.
