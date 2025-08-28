---
title: Tipps zum Debugging
description: Tipps zum einfachen Debuggen von Benutzerskripten und zu berücksichtigende Edge-Fälle.
---

Tipps zum einfachen Debuggen von Benutzerskripten und zu berücksichtigende Edge-Fälle.

## Tipps

### Es ist nicht immer notwendig, die Erweiterung neu zu laden.

Es ist nicht notwendig, die Erweiterung neu zu laden, indem du auf `chrome://extensions` gehst, um die Quelle einer bereits vorhandenen JavaScript- oder CSS-Datei ändern. In diesen Fällen reicht das erneute Laden der Seite aus.

### Verwende das Addon. * API von der Konsole

Das `addon`-Objekt ist innerhalb der Browserkonsole über die globale Variable `__addon` zugänglich, wenn mindestens ein Addon ausgeführt wird.

### Haltepunkte mit dem Schlüsselwort "Debugger" festlegen

Das Schlüsselwort `debugger;` in JavaScript friert die Seite ein, wenn sie ausgeführt wird, wenn die Entwicklertools geöffnet sind. Das Festlegen von Haltepunkten ist nützlich, um den Wert lokaler Variablen während der Ausführung zu überprüfen.

### Konsolennachrichten nach Addon-ID filtern

Gebe die Addon-ID in die Suchleiste der "Filter"-Konsole ein, um nur Protokolle und Warnungen sowie Fehler anzuzeigen, die mit `console.error()` protokolliert wurden. Denke daran, dass dies alle Ausnahmen ausblenden, es sei denn, Du protokollierst sie explizit in deinen Code.


## Edge-Fälle


### Scratch-Projektseite und Editor


#### Das DOM wird zerstört, nachdem er innerhalb oder außerhalb des Editors gegangen ist

Scratch erstellt jedes Mal alle HTML-Elemente, wenn der Benutzer auf "Schau hinein" oder "Projektseite anzeigen" klickt, und zerstört die alten.
Dies kann normalerweise mit `addon.tab.waitForElement` oder dem `urlChange`-Ereignis behoben werden.

#### Die Scratch-Editor-Sprache kann ohne Neuladen geändert werden

Im Gegensatz zur Scratch-Website wird der Scratch-Editor nicht neu geladen, wenn die Sprache geändert wird. Bei der Auswahl einer anderen Sprache kann Scratch einige HTML-Elemente zerstören und neu erstellen.

#### Andere zu berücksichtigende Situationen

- Der Projekteditor kann auch ohne eine definierte Projekt-ID verwendet werden (z.B. wenn man abgemeldet ist).
- Der Editor kann von LTR zu RTL (oder umgekehrt) wechseln, ohne dass die Seite neu geladen werden muss.


### Scratch-Website

#### scratch-www-Seiten werden nach dem Einloggen nicht neu geladen

Anders als scratchr2-Seiten erzwingen scratch-www-Seiten kein Neuladen der Seite nach dem Einloggen. Wenn du zum Beispiel eine Projektseite aufrufen, während du abgemeldet bist, und dich dann wieder anmeldest, wird die Seite nicht neu geladen. Dies gilt auch für Studios, die Nachrichtenseite usw. 
Im Gegensatz dazu werden alle Scratch-Seiten nach dem Ausloggen neu geladen.

#### Projektseiten geben nie 404er zurück

Auch wenn das Projekt nicht freigegeben ist oder nicht existiert, gibt Scratch einen 200 HTTP-Statuscode zurück. Die Meldung "Unser Server kratzt sich am Kopf" wird von Scratch dynamisch zur Seite hinzugefügt.

#### Andere zu berücksichtigende Situationen

- Jeder der 4 Tabs in den Studios hat unterschiedliche URLs, löst aber keine Browsernavigation aus. Addons, die eine der 4 Seiten betreffen, sollten unabhängig von der ursprünglichen URL ausgeführt werden.
