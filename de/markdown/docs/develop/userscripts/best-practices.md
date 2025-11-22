---
title: Empfohlene Vorgehensweisen
description: Wenn du Code für Userscripts schreibst oder überprüfst, folge diesen empfohlenen Vorgehensweisen.
---

Wenn du Code für Userscripts schreibst oder überprüfst, folge diesen empfohlenen Vorgehensweisen.


## Manipulation der DOM


### Benutze addEventListener anstatt von "onevent"

Nutze "onevent"-Werte bei HTML-Elementen, wie `onclick`, lieber nicht. Nutze stattdessen `addEventListener`. Das erlaubt es, mehreren Addons das gleiche Ereignis zu registrieren ohne Konflikte zu haben.
Man kann immer noch "onevent" nutzen, aber nur für Elemente, die von demselben Addon erstellt wurde, das das Ereignis erstellt.
Nutze auf jeden Fall keine "onevent" HTML-Attribute, zum Beispiel:
`element.setAttribute("onclick", "mache das nicht")`

{{< admonition error >}}
```js
// Mache das nicht:
document.querySelector(".remix-button").onclick = () => {
  prompt("Bist du dir sicher, dass du remixen willst?");
}
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Mache das stattdessen:
document.querySelector(".remix-button").addEventListener("click", () => {
  prompt("Bist du dir sicher, dass du remixen willst?");
});
```
{{< /admonition >}}

### Nutze innerHTML nicht

Nutze `innerHTML` lieber nicht. Stattdessen, nutze `innerText` oder `textContent`.
Andere APIs die möglicherweise zu XSS-Schwachstellen führen können sollten auch nicht genutzt werden, wie zum Beispiel `insertAdjacentHTML`, `outerHTML`, `document.write()`, usw.

{{< admonition error >}}
```js
// Mache das nicht:
document.querySelector(".sa-remix-button").innerHTML = `<span>${projectTitle} remizen</span>`;
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Mache das stattdessen:
const span = document.createElement("span");
span.textContent = `${projectTitle} remixen`;
document.querySelector(".sa-remix-button").append(span);
```
{{< /admonition >}}

### Vermeide die Verwendung von mousemove

Vermeiden die Verwendung von `mousemove` und ähnlichen DOM-Ereignissen, die sehr häufig ausgelöst werden, da sie sich negativ auf die Leistung auswirken, insbesondere wenn sie für den Body verwendet werden. Verwende stattdessen, wann immer möglich, ein alternatives Ereignis für ein untergeordnetes Element.

{{< admonition error >}}
```js // Tun Sie dies nicht: body.addEventListener("mousemove", (event) => { // ... }); ```
{{< /admonition >}}

### Verstecke Elemente, anstelle sie zu entfernen

Nutze die Funktion `.remove()` bei HTML-Elemente nicht, da sie bei Extremfällen die Projektseite zum Abstürzen bringen kann.
Addons können sie nur für Elemente, die sie selber erstellt haben, in speziellen Situationen nutzen.

{{< admonition error >}}
```js
// Mache das nicht:
document.querySelector(".remix-button").remove();
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Mache das stattdessen
document.querySelector(".remix-button").style.display = "none";

// Oder das, mithilfe eines Userstyles:
document.querySelector(".remix-button").classList.add("sa-remix-button-hidden");
```
{{< /admonition >}}

### Nur waitForElement nutzen, wenn nötig

Nutze die `addon.tab.waitForElement`-API nur, wenn das Element garantiert existiert. Es wird immernoch funktionieren, und die Performance wird stark beeinflusst werden, aber es könnte andere Entwickler verwirren, die den Code lesen. waitForElement sollte bedeuten, dass es zumindest 1 Szenario gibt, an dem das Element nicht existiert, wenn der Code ausgeführt wird.
Zum Beispiel ist es nicht wichtig, waitForElement zu nutzen, wenn man nach Forumposts sucht, außer wenn das Userscript mit `"runAtComplete": false` deklariert wurde. In diesen Fällen kann man einfach `document.querySelectorAll()` normal ausführen.

### element.closest() verwenden, anstatt parentElement zu missbrauchen

Vermeide die übermäßige Verwendung von parentElement, wenn du die Vorfahren eines Elements durchsuchst. Verwende stattdessen `element.closest()`, das sehr ähnlich wie `element.querySelector()` funktioniert.

{{< admonition error >}}
```js
// Mach dies Nicht:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.parentElement.parentElement.parentElement.parentElement;
})
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Tu stattdessen Folgendes:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.closest(".comment");
})
```
{{< /admonition >}}


## Bewährte JavaScript-Verfahren


### Verwenden Sie modernes JavaScript

- Bevorzuge neuere APIs, wie z.B. `fetch()` gegenüber `XMLHttpRequest`.
- Verwende niemals `==` für Vergleiche. Verwende stattdessen `===`.
- Beim Abhören von Tastaturereignissen ist der Zugriff auf `event.key` der bevorzugte Weg, um zu erfahren, welche Taste gedrückt wurde. Im Allgemeinen sollte `event.code` und `event.keyCode` vermieden werden.
- Verwende die optionale Verkettung, wenn ein Objekt manchmal `null` sein kann.
Zum Beispiel: `document.querySelector(".remix-button")?.textContent`.
- Verwende `for ... of`-Schleifen oder `.forEach()`.
Vermeide Schleifen im C-Stil wie `for (let i = 0; i < arr.length; i++)`.

### Verwende "let" statt "const" nur, wenn die Variable neu zugewiesen werden kann.

{{< admonition info >}}
Wir verwenden normalerweise `camelCase`, um Variablen zu benennen, egal ob sie mit "let" oder "const" deklariert sind. 
Für konstante Zeichenketten oder Zahlen verwenden wir normalerweise `SNAKE_CASE`.

Hier ist ein Beispiel:
```js
let actionCounter = 0;
actionCounter++;

const remixButton = document.querySelector(".remix-button");

const DEFAULT_ZOOM = 1.20;
```
{{< /admonition >}}

Wer deinen Code liest, könnte annehmen, dass eine Variable, die mit dem Schlüsselwort "let" deklariert wurde, an einer anderen Stelle des Skripts neu zugewiesen werden könnte. Wenn das nicht der Fall ist, verwende stattdessen das Schlüsselwort "const". 
Erinnere dich daran, dass in JavaScript die Deklaration eines Objekts oder eines Arrays als "const" nicht bedeutet, dass seine Werte eingefroren sind. Die Werte des Objekts können immer noch geändert werden, auch wenn die Variable selbst nicht neu zugewiesen werden kann.

### Keine globalen Variablen setzen

Vermeide es, Eigenschaften für das globale `Fenster`-Objekt zu setzen, es sei denn, du verschmutzt eine globale Funktion wie `fetch()`. 
Wenn mehrere Addons Informationen oder Funktionen untereinander austauschen müssen, erstelle eine JS-Moduldatei und importiere sie aus beiden Benutzerskripten.

{{< admonition error >}}
```js
// Tu das nicht:
window.isDarkMode = true;
```
{{< /admonition >}}

### Deklariere keine Funktionen außerhalb des Standard-Exports.

Es gibt keinen Grund, Funktionen außerhalb der Funktion `export default async function(){}` zu deklarieren. JavaScript erlaubt es, Funktionen innerhalb anderer Funktionen zu deklarieren.

Du kannst Funktionen in separate JS-Moduldateien verschieben (die nicht als Benutzerskripte im Addon-Manifest deklariert sind), wenn dies angebracht ist, aber bedenke, dass diese importierten Dateien keinen Zugriff auf das `Addon`-Objekt haben, es sei denn, du stellst eine Setup-Funktion bereit, die es als Argument akzeptiert, und rufst die Funktion im Benutzerskript-Einstiegspunkt auf.

### Funktionen nicht entlasten

Es kann vorkommen, dass mehrere Addons dieselbe Funktion verschmutzen wollen, wie z.B. Scratch VM Methoden, `XMLHttpRequest`, `fetch()` oder `FileReader()`. 
In diesen Fällen wird eines der Benutzerskripte die eigentliche Funktion verschmutzen, während die anderen Funktionen verschmutzen werden, die bereits selbst verschmutzt wurden. Wenn zum Beispiel das erste Benutzerskript, das die Funktion verschmutzt hat, beschließt, die Verschmutzung rückgängig zu machen (zum Beispiel durch `window.fetch = realFetch`), dann gehen alle anderen Funktionen in der "Verschmutzungskette" ebenfalls verloren, was unerwartet ist. 
Aus diesem Grund sollten Funktionen nicht unpolluted werden. Übergeben Sie stattdessen die Argumente an die ursprüngliche Funktion.

{{< admonition error >}}
```js
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  // ...
}

addon.self.addEventListener("disabled", () => {
  // Tu das nicht:
  vm.deleteSprite = oldDeleteSprite;
});
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Tu stattdessen Folgendes:
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  if (addon.self.disabled) return oldDeleteSprite.apply(this, args);
  // ...
};
```
{{< /admonition >}}

## Internationalisierung

### addon.tab.scratchMessage() verwenden

Wenn eine Zeichenkette bereits von Scratch übersetzt wurde, verwende [addon.tab.scratchMessage](/docs/reference/addon-api/addon.tab/#addontabscratchmessage), anstatt eine neue Nachricht hinzuzufügen.

{{< admonition error >}}
```js
// Tu das nicht:
doneButton.innerText = msg("done");
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Tu stattdessen Folgendes:
doneButton.innerText = addon.tab.scratchMessage("general.done");
```
{{< /admonition >}}
