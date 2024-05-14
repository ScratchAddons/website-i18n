---
title: Informazioni di Base sugli Addon
---

## What is an addon?
An addon is a userscript, userstyle, or combination of both that runs on the Scratch website or project editor when enabled. For example, the "Editor find bar" addon has a userscript that adds a find box to the editor, and a userstyle that styles that box.

## What is a userscript?
A [userscript](/docs/develop/userscripts) is a JavaScript file that is executed every time the user loads a Scratch page. They can modify the document’s HTML, add new buttons, customize Scratch editor behavior, and so much more.

## What is a userstyle?
A [userstyle](/docs/develop/userstyles) is similar to a userscript; you can specify URL patterns for them. However, userstyles inject CSS instead of JavaScript. They are often used along userscripts to style elements added by them, but they can also be used to style native Scratch elements. When that's the case, we usually call them "themes".

## What should be an addon?

<!-- TODO: Expand this section into its own page -->
You might wonder if it's a better idea to create a new addon, or modify an existing one.
If two addons share some of these, they should probably be merged.
- Entrambi necessitano, o non necessitano, di permessi che richiedono l'interazione dell'utente (come avviene ad esempio per le notifiche).
- Condividono una buona parte del codice.
- L'utente si aspetterebbe da quell'addon entrambe le funzionalità.
- If being separated, they would interfere with each other.

Remember addons are customizable by the user - adding new functionality should not affect existing users of the addon, unless we intentionally decide to do so.
