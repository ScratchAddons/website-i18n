---
title: Podstawy Dodatków
---

## Czym tak naprawdę jest Dodatki?
Właściwie dodatek to nic innego jak skrypt użytkownika, styl użytkownika lub kombinacja tych dwóch elementów. Jeśli któreś z nich są ze sobą powiązane, to czynimy je częścią tego samego dodatku, pod jedną nazwą. Na przykład, dodatek "Scratch 3 Developer Tools" ma skrypt użytkownika odpowiedzialny za dodanie pola wyszukiwania do edytora oraz styl użytkownika, który dodaje CSS do tego pola.

## Co to userscript (skrypt użytkownika)?
A userscript is a piece of JavaScript code that runs together with a Scratch tab. You can specify where that userscript will run, for example, only project pages. Userscripts are similar to content scripts on browser extensions, and if you've ever used a userscript manager, you'll notice these are basically the same.  
Userscripts are useful to change the behavior of the Scratch website, for example, adding or removing buttons to the navbar.

## What's a userstyle?
A userstyle is similar to a userscript; you can also specify URL patterns for them. However, userstyles inject CSS instead of JavaScript. They are often used along userscripts to style elements added by them, but they can also be used to style native Scratch elements. When that's the case, we usually call them "themes".

## Conceptually, what should be an addon?
You might wonder if it's a better idea to create a new addon, or modify an existing one.  
If 2 addons share some of these, they should probably be merged. 
- Both need, or don't need, permissions that require user interaction (like notifications).
- They share lots of code.
- The user would expect that addon to offer both features.
- If being separated, they would interfere with each other.  

Remember addons are customizable by the user - adding new functionality does not affect old users of the addon, unless we intentionally make it do so.