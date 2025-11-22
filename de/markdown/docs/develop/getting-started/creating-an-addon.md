---
title: Ein Addon entwickeln
---

Diese Seite beschreibt die Grundlagen zum Erstellen eines Addons für Scratch Addons. Bevor du fortfährst, lies bitte die [Addon-Grundlagen](../addon-basics/) und deaktiviere alle anderen Instanzen von Scratch-Addons, um Konflikte zu vermeiden.

{{< admonition info >}}
Wenn du vorhast, das Addon, das du entwickelst, als Pull-Request an unser GitHub-Repository zu senden, lies bitte zuerst unsere [Beitragsrichtlinien](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md).
{{< /admonition >}}

## Anforderungen
Scratch Addons erfordert keine Software für die Entwicklung, außer einem Texteditor und einem Chromium-basierten Browser (121+), aber wir empfehlen auch, [Git](https://git-scm.com/), [Firefox](https://www.firefox.com/) (121+) und [Visual Studio Code](https://code.visualstudio.com/) installiert zu haben.

## Installation
Informationen zur Installation der Erweiterung für die Entwicklung findest du unter [von der Quelle installieren](/docs/getting-started/installing/#from-source).

## Erstellen des Addon-Ordners
Jedes Addon hat seine eigene interne ID, die von der Erweiterung und anderen Addons verwendet wird. Addon-IDs sollten außer Bindestrichen keine Leerzeichen oder Sonderzeichen enthalten und sollten selbstbeschreibend, aber nicht zu lang sein.

Neue Addons sollten keine ID verwenden, die in einer stabilen Version der Erweiterung enthalten war, aber später entfernt wurde. Dazu gehören:

- `a11y`
- `data-category-tweaks`
- `featured-dangos`
- `fix-buttons`
- `forum-time-zones`
- `image-uploader`
- `redirect-mobile-forums`
- `scratchstats`
- `tutorials-button`

Öffne die Datei `addons.json` im Ordner `addons`, füge eine neue Addon-ID über der Zeile `// NEW ADDONS ABOVE THIS ↑↑` in der Nähe des unteren Endes der Datei ein und erstelle dann einen Unterordner mit demselben Namen.

## Das Addon-Manifest
Jedes Addon hat sein eigenes [Manifest](/docs/reference/addon-manifest/), das damit umgeht, wie es auf der Einstellungsseite angezeigt wird, alle Einstellungen, die das Addon haben kann, welche Benutzerskripte oder Benutzerstile ausgeführt werden sollen und wo sie ausgeführt werden sollen.

Addon-Manifeste befinden sich im Ordner jedes Addons und heißen `addon.json`.
Hier ist ein minimales Addon-Manifest:
```json
{
  "name": "My addon",
  "description": "TODO",
  "tags": ["community"]
}
```

Weitere Informationen darüber, was im Manifest deklariert werden kann, findest du unter [die Addon-Manifest-Referenz](/docs/reference/addon-manifest/).

Das Addon tut noch nichts, aber es sollte auf der Popup- und Einstellungsseite erscheinen, nachdem die Erweiterung neu geladen wurde.

## Benutzerskripte und Benutzerstile
[Benutzerskripte](/docs/develop/userscripts/) und [Benutzerstile](/docs/develop/userstyles/) sind es, die das Addon zum Laufen bringen. Benutzerskripte führen JavaScript-Code aus und Benutzerstile injizieren CSS-Stile. Addons können eine Kombination aus Benutzerstilen und Benutzerskripten haben.

Benutzerskripte haben Zugriff auf [Addon-APIs](/docs/reference/addon-api/), um Scratch-spezifische Aufgaben wie das Abrufen des derzeit angemeldeten Benutzers zu erleichtern.

Wenn du ein Benutzerskript oder einen Benutzerstil zum Ordner des Addons hinzufügst, muss es im Addon-Manifest deklariert werden, da es sonst nicht ausgeführt wird.

## Addon-Einstellungen
Das [Einstellungs-Objekt](/docs/reference/addon-manifest/#settings-object) im Addon-Manifest ermöglicht das Hinzufügen von Optionen wie Umschalter, Textfeldern oder Farbwählern zu Ihrem Addon auf der Einstellungsseite, um es von Benutzern anpassbar zu machen.

Siehe die [addon.settings](/docs/reference/addon-api/addon.settings) Dokumentation zum Zugriff auf Benutzerauswahl von Benutzerskripten und Benutzerstilen.

## Vor dem Beitragen
{{< admonition info >}}
Falls es in diesem Repository kein bestehendes GitHub-Problem im Zusammenhang mit deiner neuen Addon-Idee gibt, erstelle bitte eines. Wenn es jedoch bereits ein Problem im Zusammenhang mit Ihrer Feature-Idee gibt, empfehlen wir, einen Kommentar zu hinterlassen, in dem di deine Absicht angibst, das Addon zu entwickeln. Dies wird es anderen Mitwirkenden ermöglichen, Feedback zu geben, ob das Addon akzeptiert werden kann oder ob weitere Diskussionen erforderlich sind.

Beachte auch, dass die Nutzungsbedingungen von GitHub verlangen, dass Benutzer 13+ sein müssen, um ein Konto bei ihnen zu erstellen.
{{< /admonition >}}

Wenn du dein Addon im GitHub-Repository von Scratch Addons einreichen möchten, damit es der Addon-Bibliothek hinzugefügt werden kann, stelle sicher, dass das Addon wie erwartet funktioniert, mit und ohne andere Addons aktiviert und dass es andere Addons nicht bricht. Das Manifest des Addons sollte einen guten Namen und eine gute Beschreibung haben, `versionAdded` sollte auf die nächste Version der Erweiterung gesetzt werden und das Addon sollte standardmäßig nicht aktiviert sein. Addons sollten dynamische Aktivierung und Deaktivierung unterstützen, ist aber nicht erforderlich.
Stelle sicher, dass der Code verständlich ist; unnötige Kommentare sind besser als keine Kommentare.

## Senden einer Pull-Anfrage
Befolge die Schritte in unseren [Richtlinien für Beiträge] (https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md). Einfach ausgedrückt, forke das Repository, wenn es noch nicht getan haben, bestätige dein neues Addon und sende eine Pull-Anfrage.

Wenn dein Addon noch nicht fertig ist oder du Hilfe bei etwas benötigen, erstelle einen Pull-Entwurf.

Denke daran, dass wir dich möglicherweise auffordern, einige Änderungen vorzunehmen, und der Überprüfungsprozess kann langsam sein, aber wir werden Ihr Addon wahrscheinlich akzeptieren, solange es minimal geeignet und Scratch-spezifisch ist.
