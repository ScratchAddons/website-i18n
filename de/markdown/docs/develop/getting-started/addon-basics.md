---
title: Addon-Basics
---

## Was ist ein Addon?
Ein Addon ist ein Benutzerskript, ein Benutzerstil oder eine Kombination aus beidem, die auf der Scratch-Website oder dem Projekteditor ausgeführt wird, wenn dies aktiviert ist. Zum Beispiel hat das Addon "Editor Suchleiste" ein Benutzerskript, das dem Editor ein Suchfeld hinzufügt, und einen Benutzerstil, der dieses Feld gestaltet.

## Was ist ein Benutzerskript?
Ein [Benutzerskript](/docs/develop/userscripts) ist eine JavaScript-Datei, das jedes Mal ausgeführt wird, wenn der Benutzer eine Scratch-Seite lädt. Du kannst den HTML-Code des Dokuments ändern, neue Schaltflächen hinzufügen, das Verhalten des Scratch-Editors anpassen und vieles mehr.

## Was ist ein Benutzerstil?
Ein [Benutzerstil](/docs/develop/userstyles) ähnelt einem Benutzerskript; du kannst URL-Muster für sie angeben. Benutzerstile injizieren jedoch CSS anstelle von JavaScript. Sie werden oft zusammen mit Benutzerskripten verwendet, um von ihnen hinzugefügte Elemente zu gestalten, aber sie können auch verwendet werden, um native Scratch-Elemente zu gestalten. Wenn das der Fall ist, nennen wir sie normalerweise "Themen".

## Was sollte ein Addon sein?

<!-- TODO: Erweitere diesen Abschnitt zu einer eigenen Seite -->
Du fragst dich vielleicht, ob es eine bessere Idee ist, ein neues Addon zu erstellen oder ein bestehendes zu ändern.
Wenn sich zwei Addons einige davon teilen, sollten sie wahrscheinlich zusammengeführt werden.
- Beide benötigen oder benötigen keine Berechtigungen, die Benutzerinteraktion erfordern (z. B. Benachrichtigungen).
- Sie teilen sehr viel Code.
- Der Benutzer wird beide Features vom Addon erwarten.
- Wenn sie getrennt wären, würden sie sich gegenseitig stören.

Denke daran, dass Addons vom Benutzer anpassbar sind - das Hinzufügen neuer Funktionen sollte sich nicht auf bestehende Benutzer des Addons auswirken, es sei denn, wir entscheiden uns absichtlich dafür.
