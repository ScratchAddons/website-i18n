---
title: Häufig Gestellte Fragen
description: Diese Seite listet häufig gestellte Fragen über Scratch Addons auf.
---

Diese Seite listet häufig gestellte Fragen über Scratch Addons auf.

### Was ist Scratch Addons?

Scratch Addons ist eine "All-in-One"-Browsererweiterung für die Scratch-Website und den Projekteditor. Es bietet Funktionen und Designs (intern Addons genannt) sowohl für die Scratch-Website als auch für den Projektideditor. Die Mission von Scratch Addons besteht darin, alle vorhandenen Scratch-Erweiterungen, Userscripts und Userstyles, die von mehreren Mitgliedern der Scratch-Community entwickelt wurden, in einem einzigen, leicht zugänglichen Ort zu kombinieren und den Benutzern weiterhin die Auswahl der zu aktivierenden Erweiterungen zu ermöglichen.

### Was ist ein "Addon" genau?

Ein Addon ähnelt einer Erweiterung oder einem Userscript, verwendet jedoch spezielle APIs, die von der Erweiterung Scratch Addons bereitgestellt werden. Mit diesen APIs können Addons Skripte auf einer Scratch-Seite ausführen (Userscripts), Skripte im Hintergrund ausführen (persistente Skripte) oder Stile auf die Scratch-Website (Userstyles) anwenden.

Userscripts und persistente Skripte können das `Addon*` verwenden. JavaScript-APIs, mit denen sie Scratch-bezogene Informationen abrufen (z. B. den aktuell angemeldeten Benutzer) und Erweiterungs-APIs verwenden können (z. B. Benachrichtigungen senden).

### Wenn alles ein Addon ist, was macht Scratch Addons dann?

Allein ist Scratch Addons nur ein Addon-Lader. Seine Hauptaufgaben sind:

- Erlaubt es Nutzern, Addons zu deaktivieren und zu konfigurieren.
- Addons ausführen und APIs dafür bereitzustellen.
- Den Addons globalen Status geben (z. B. die API addon.auth).
- Erstellen von Prototypen zur Verwendung durch Addon-Userscripts.
- Methoden zum Zugreifen und Bearbeiten des Redux-Status bereitstellen.
- Vermeiden, dass sich Addons untereinander behindern.
- Doppelte Arbeit von verschiedenen Addons vermeiden.

### Ist Scratch Addons sicher?

Ja. Scratch Addons sollte in der neuesten Version keine Sicherheitsprobleme aufweisen. Scratch Addons ist ein Open-Source-Projekt, daher wird der Code ständig von Scratch Addons-Mitwirkenden sowie von Rezensenten aus dem Chrome Web Store und Add-ons für Firefox überprüft.

### Wie kann ich eine Sicherheitsschwäche melden?

Wenn du zufällig eine Sicherheitsanfälligkeit finden solltest, wende dich bitte privat an World_Languages, indem du eine E-Mail an `worldxlanguages (at) gmail.com` sendest. Wenn du innerhalb von 48 Stunden keine Antwort erhaltest, erstelle bitte ein Issue [hier](https://github.com/ScratchAddons/ScratchAddons/issues/), in dem erwähnt wird, dass du eine E-Mail gesendet hast.

Du kannst auch [unsere Sicherheitserklärung lesen](https://github.com/ScratchAddons/ScratchAddons/security/policy), oder [die Warnungen, die wir veröffentlicht haben, prüfen](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### Ist mein Konto sicher, wenn ich Scratch Addons verwende?

Scratch Addons verwendet deine Kontoanmeldeinformationen nicht, um im Wesentlichen zu funktionieren. Tatsächlich kannst du dich von Scratch abmelden, und Scratch Addons funktioniert weiterhin. Scratch Addons sendet nur Anfragen basierend auf den  vorhandenen Cookies, die vom Browser für jede Anforderung bereitgestellt werden. Einige Addons wie Scratch Messaging funktionieren also nicht, während du dich anmeldest, haben jedoch keine Auswirkungen auf andere Teile der Erweiterung .

Addons auf Scratch Addons wurden auch von mehreren Mitwirkenden im Repository geprüft, sodass niemand nur böswilligen Code unter unsere Augen schieben kann.

Wir senden niemals Scratch-Kontoinformationen oder Erweiterungseinstellungen außerhalb deines Browsers. Weitere Informationen findest du unter der [Datenschutzrichtlinie für Erweiterungen] (/docs/privacy/policies/extension).

### Kann ich anderen Leuten auf Scratch über Scratch Addons erzählen?

Nein, und bitte tu es nicht. Es gibt eine Richtlinie, die die Werbung für Browsererweiterungen/Usercripts [hier](https://scratch.mit.edu/discuss/post/2907564/) verbietet. Du kannst jedoch verschiedene Methoden anwenden, um deinen Freunden von Scratch Addons zu erzählen.

### Wie kann ich bei Scratch Addons mitwirken?

Erstens, danke für dein Interesse, bei Scratch Addons mitzuwirken. Wir sind dankbar für deine künftigen Beiträge.

Als Open-Source-Projekt begrüßen wir jede Art von Beiträgen. Du musst uns nicht einmal fragen oder einen bestimmten Rang haben. Jeder ist willkommen. Es besteht sogar die Möglichkeit, dass du nicht einmal feststellst, dass du zum Projekt beigetragen hast!

Jedensfalls, zurück zum Punkt. DU kannst auf viele Arten Mitwirlen, und manche sind echt leicht.

- **Code beitragen**

  Wenn du in JavaScript, HTML5 und CSS programmieren kannst, kannst du beitragen, indem du etwas programmierst. Du kannst Fehler beheben, manche Anfragen angehen oder dein eigenes Addon entwickeln.

  Danach musst du eine Pull-Anfrage erstellen. Du kannst dies tun, indem du [das Repository](https://github.com/ScratchAddons/ScratchAddons/) forkst, deine nötigen Änderungen machst, und eine Pull-Anfrage erstellst. Falls es als machbar erachtet ist, werden wir es hinzufügen.

  Wir sind auch für andere Aspekte von Beiträgen offen. Du kannst unsere Repositorys auf  [unserer Organisationsseite auf GitHub](https://github.com/ScratchAddons) ansehen und uns dort helfen.

- **Eine Idee vorschlagen**

  Du glaubst, du hast etwas, was Scratch Addons gut ergänzen würde? [Sag es uns!](#i-think-you-missed-a-feature-what-can-i-do)

- **Einen Fehler melden**

  Du hast einen Fehler in einem unserer Addons, der Einstellungenseite oder etwas anderem in unserer Erweiterung gefunden? [Sende uns eine Fehlermeldung](#what-can-i-do-if-i-find-a-problem).

- **Scratch Addons übersetzen**

  Wenn du eine andere Sprache als Englisch flüssig sprechen kannst, kannst du beim Übersetzen von Scratch Addons in deiner Sprache mithelfen. Du kannst [hier](/docs/localization/joining-the-localization-team) beginnen.

- **Die Dokumentation schreiben**

  Du kennst dich gut mit Scratch Addons aus? Falls das so ist, kannst du die Dokumentation dafür schreiben. Die Dokumentation kann seine Verwendung oder Funktionsweise enthalten. Bitte kontaktiere uns auf  [unserem Diskussions-Tab](https://github.com/ScratchAddons/ScratchAddons/discussions) für weitere Informationen.

- **Feedback senden**

  Du kannst uns deine Meinung in [unserem Feedback-Formular](https://scratchaddons.com/feedback) sagen. Dein Feedback könnte uns eine andere Perspektive in der Entwicklung verleihen und uns helfen, Ideen und Probleme kennenzulernen.

- **Eine Bewertung in den Stores hinterlassen**

  Du kannst uns eine Bewertung zu Scratch Addons auf [der Chrome-Erweiterungsseite](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) oder [der Firefox-Addon-Seite](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) zukommen lassen.

- **Unser Repository starren**

  Grundsätzlich ähnelt der GitHub-Stern dem Scratch-Stern/Favoriten. Du kannst dies tun, indem du zu [unserem Repository](https://github.com/ScratchAddons/ScratchAddons) gehst und oben rechts auf die Schaltfläche "Star" klickst.

- **Andere einweihen**

  Du kannst jedem von Scratch Addons erzählen, wie deinen Freunden, deinen Verwandten, deinen Familienmitgliedern oder sogar deinem Lehrer, wenn du möchtest. Wir bitten dich nur, [dies auf der Scratch-Website nicht zu tun](#can-i-tell-people-about-scratch-addons-on-scratch).

### Wie kann ich mein eigenes Addon erstellen?

Erfahre mehr über das Erstellen von Addons für Scratch Addons [hier](/docs/develop/getting-started).

### Wie bekomme ich meinen Namen auf der [Entwicklerliste](/contributors)?

Bitte lies und folge den Anleitungen auf [diesem Issue](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}), um deinen Namen auf besagter Seite zu haben.

### Wie entferne ich meinen Namen von der [Entwicklerseite](/contributors)?

Wenn du nicht willst, dass dein Name auf der Seite sichtbar ist, bitte sag es uns, indem du ein Issue auf [unserem Entwickler-Repository](https://github.com/ScratchAddons/contributors/issues/) erstellst, oder indem du einen Entwickler kontaktierst. Es tut uns leid für die Unannehmlichkeit.

### Was kann ich tun, wenn ich ein Problem finde?

Du kannst uns mit einer der folgenden Methoden kontaktieren.

- Sende es uns mittles [unserem Feedback-Formular](https://scratchaddons.com/feedback).
- Erstelle ein Issue auf [dem Repository](https://github.com/ScratchAddons/ScratchAddons/issues).
- Erstelle ein Post auf [unserem Diskussions-Tab](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Sag es uns auf [unserem Discord-Server](https://discord.gg/R5NBqwMjNc).

### Ich denke, ihr habt eine Funktion übersehen. Was kann ich tun?

Wenn du denkst, dass eine Funktion fehlt, oder wenn du ein neues Addon vorschlagen willst, oder wenn du eine gute Idee hast, verwende [eine der oben erwähnten Methoden](#what-can-i-do-if-i-find-a-problem).

### Wo kann ich mit anderen über Scratch Addons diskutieren?

Du kannst es auf [unserem Diskussions-Tab](https://github.com/ScratchAddons/ScratchAddons/discussions) oder [unserem Discord-Server](https://discord.gg/R5NBqwMjNc) tun. Dort kannst du darüber diskutieren und Fragen ste.len, wenn du Schwierigkeiten hast.

### Ich denke, dass Scratch Addons Scratch verlangsamt. Was kann ich tun?

Versuche Addons, die du nicht oder selten brauchst, auszuschalten. Prüfe zusätzlich die Warnungen der Addons, um zu sehen, welche Addons du für bessere Leistung deaktivieren solltest.

### Wie kann ich die Easter-Egg-Addons aktivieren?

Um die Easter-Egg-Addons zu enthüllen, mache den Konami-Code (↑↑↓↓←→←→BA) mit deiner Tastatur auf der Einstellungenseite. Danach werden die Easter-Egg-Addons sichtbar sein, um dir den Zugriff darauf zu erlauben.

Manche unserer Easter-Egg-Addons sind "Katzenblöcke" und "Semikolonfehler". Im [Addons-Tab](/addons) findest du die vollständige Liste.

### Ich habe noch Fragen!

Falls du noch Fragen hast, erstelle einen Post in [unserem Diskussions-Tab](https://github.com/ScratchAddons/ScratchAddons/discussions) oder sende eine Nachricht [auf unserem Discord-Server](https://discord.gg/R5NBqwMjNc). Jemand wird versuchen, dir eine Antwort zu geben.
