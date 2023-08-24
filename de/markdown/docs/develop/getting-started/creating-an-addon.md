---
title: Ein Addon entwickeln
---
Benötigte Software: Texteditor, Chrome.
Schalte, wenn möglich, die Scratch-Addons-Erweiterung die du von den Stores runtergeladen hast, bevor du weiter machst, um Fehler zu vermeiden.


{{< admonition info >}}
Wenn du vor hast, das Addon, das du erstellst, als Pull Request auf unserer GitHub-Repository zu senden, lese zuerst bitte unsere [Beitragsrichtlinien](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md). 

Wenn es kein existierendes GitHub-Issue in dieser Repository über deine Addon-Idee gibt,  [erstell bitte eins](https://github.com/ScratchAddons/ScratchAddons/issues/new/choose). Wenn es allerdings schon ein Issue über deine Idee gibt, empfehlen wir dir, darauf zu kommentieren, dass du das Addon erstellen willst. Das wird es anderen Mitwirkenden erlauben, Feedback zu geben, ob das Addon akzeptiert wird, oder ob weitere Diskussionen nötig wären.

Wenn du dieses Addon allerdings für persönlichen Nutzen erstellen willst, kannst du hier weiter machen.
{{< /admonition >}}

## Schritt 1: Lese die [Addongrundlagen](/docs/develop/getting-started/addon-basics/).
Lese den Artikel, um dich mit den Begriffen vertraut zu machen.

## Schritt 2: Forke/klone die [Repository](https://github.com/ScratchAddons/ScratchAddons).
Folge [diesen Anleitungen](/docs/getting-started/installing/#from-source) um den Source Code lokal runterzuladen.

## Schritt 3: Lade die Erweiterung in Chrome
*Hinweis: Chrome ist beim Arbeiten an Addons empfohlen. Addons sollten trotzdem auf Firefox und Edge funktionieren.*
Wenn du die Erweiterung jetzt in deinem Dateisystem hast, gehe zu `chrome://extensions` und schalte "Entwicklermodus" ein.
Klicke auf "Entpackte Dateien laden', dann wähle den Ordner, in dem Scratch Addons ist. Wenn du Probleme damit hast, stelle sicher, dass du den Ordner wählst, wo `manifest.json` enthalten ist.
Das ist alles, du hast die Erweiterung geladen! Es sollte etwa so aussehen:
![Bild](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)
Hinweis: Du kannst ignorieren, dass "Fehler" angezeigt wird. Das ist eine Warnung für ein unerkannter Manifestkey, der von Firefox benötigt wird.

## Schritt 4: Worum geht es bei deinem Addon?
Jetzt kommt der spaßige Teil!
Was wird dein Addon machen? Denke dir eine selbstbeschreibende Addon-ID (ohne Leertasten oder Sonderzeichen, außer Bindestriche)
Hast du sie?

## Schritt 5: Erstelle den Ordner des Addons
Gehe mithilfe eines Dateimanagers zu dem Ordner, wo Scratch Addons sich befindet. Gehe zu dem `addons`-Ordner.
Erstelle dann einen neuen Ordner mit deiner epischen Addon-ID als Name.

## Schritt 6: Füge ein Addon-Manifest hinzu
Das Addon-Manifest sagt Scratch Addons, wie dein Addon funktioniert. Das solltest du richtig machen, um weitere Probleme zu vermeiden.
Erstelle eine `addon.json`-Datei in dem Ordner, den du gerade erstellt hast.
Das ist eine Basis, die du nutzen kannst, um anzufangen, ändere es später aber:
```json
{
  "name": "Epic placeholder text in place of addon name",
  "description": "Hello World! It would be really smart to replace this placeholder text with a description.",
  "tags": ["community"],
  "enabledByDefault": false
}
```
Siehe [diesen Artikel](/docs/reference/addon-manifest/) für mehr Informationen, über was du in das Manifest tuen kannst.


## Schritt 7: Sage Scratch Addons, was die ID deines Addons ist
Scratch Addons kann neue Ordner nicht automatisch finden, also solltest du den Namen in eine besondere Datei hinzufügen.
Gehe zu `scratchAddonsOrdner/addons/addons.json` und füge die ID deines Addons zu der Liste hinzu.

## Schritt 8: Hallo Welt
Dein Addon macht momentan nichts, also ist es eine gute Zeit, zu überprüfen, ob alles funktioniert hat.
Gehe zu `chrome://extensions` und lade Scratch Addons neu, indem du auf das "Neu laden"-Symbol auf der Karte der Erweiterung klickst.
Mache nun einen Rechtsklick auf das Scratch Addons-Icon, und klicke auf "Optionen".
Dein Addon sollte in der Liste sein! Schalte es ein, wenn du es gefunden hast, und setze Einstellungen, die du haben könntest.

## Schritt 9: Der tolle Teil, programmiere!
*Bevor du weitermachst, stelle sicher, dass du den Artikel, der in Schritt 1 verlinkt war, gelesen hast.*

Hier kommt der tolle Teil: erstelle deine eigenen JS- oder CSS-Dateien!
Pro-Tip: Nachdem du eine Änderung zu deinem Addon vollführt hast, lade die Scratch Addons-Erweiterung wie in Schritt 8 neu.

Je nachdem was dein Addon tuen sollst, solltest du dir diese Wikiseiten ansehen:
- [Userscripts](/docs/develop/userscripts)
- [Userstyles](/docs/develop/userstyles)

## Schritt 10: Mache dein Addon veränderbar
Wenn du willst, kannst du dein Addon veränderbar machen!
Nutzer deines Addons werden Einstellungen verändern können, Zahlen eingeben können, und mehr!
Um anzufangen, schaue dir an, [wie man Einstellungen im Addon-Manifest deklariert](/docs/reference/addon-manifest/#settings-object).
Dann, gehe zu der [addon.settings-Dokumentation](/docs/reference/addon-api/addon.settings), um zu lernen, wie man von Userscripts aus die Auswahlen der Nutzer bekommen kann.

## Schritt 11: Bevor dein Addon veröffentlicht wird
Jetzt, da dein Addon funktioniert, stellen wir sicher, dass dein Addon in die Addonbibliothek passt.
Stelle sicher, dass dein Addonmanifest passend ist, [mehr Infos hier](/docs/reference/addon-manifest). Achte vor allem auf den Namen, die Beschreibung und die Tags deines Addons. Stelle sicher, `"enabledByDefault"` entweder auf `false` zu setzen oder gleich zu entfernen.
Stelle sicher, dass dein Addon mit anderen Addons gut funktioniert.
Stelle sicher, dass dein Code verständlich ist; unnötige Kommentare sind besser als keine Kommentare.

## Schritt 12: Sende ein Pull Request!
Folge den Schritten in unseren [Beitragsrichtlinien](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md). Einfach gesagt, forke die Repository wenn nicht schon geschehen, commite dein neues Addon und sende ein PR!
Wir werden dich vielleicht nach Änderungen fragen, aber wir werden dein Addon vermutlich akzeptieren wenn es einigermaßen passend ist.
