---
title: Installation
---

## Aus Erweiterungen-Stores

Scratch Addons ist in diesen Stores verfügbar.

| Store | Installieren | Unterstützte Browser | Systemanforderungen |
| - | - | - | - |
| Chrome Web Store | [![Aus Chrome Web Store installieren](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 80+<br />Microsoft Edge 80+<br />Opera 67+<br />Brave 1.3+<br />Vivaldi 2.11+<br />*Chromium 80+* | Windows 7+<br />OS X / MacOS 10.11+<br />höchstens ~6 Jahre alte Chromebooks
| Add-ons für Firefox | [![Aus Add-ons für Firefox installieren](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 86+ | Windows 7+<br />OS X / MacOS 10.12+
| Microsoft Edge Add-ons | [![Aus Microsoft Edge Addons installieren](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 80+ | Windows 7+<br />OS X / MacOS 10.11+

## Aus Quelle

### Über GitHub-Releases

[Release-Seite](https://github.com/ScratchAddons/ScratchAddons/releases) contains the code and installation files for all development builds of Scratch Addons, as well as the mirror of the store builds.

### Repository klonen

Installationsmethode für Entwicklungsziele empfohlen. Dies geht davon aus, dass du Git installiert hast.

Um das Repository herunterzuladen, klone einfach  `https://github.com/ScratchAddons/ScratchAddons.git`.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
Um Scratch Addons zu aktualisieren, `cd` zuerst zu seinem Ordner und führe dann die folgenden Befehle aus.

```sh
$ git fetch
$ git pull
```

Dies wird Scratch Addons aktualisieren und es für das Bearbeiten des Codes bereit machen. Siehe [hier](#install-on-google-chrome), um das Update auf Google Chrome abzuschließen.


### Zipball herunterladen

Falls du Git nicht installiert hast, kannst du stattdessen diese Methode ausprobieren. Du wirst diesen Vorgang jedes Mal, wenn du Scratch Addons aktualisieren willst, wiederholen müssen.

1. Gehe zum [Repository](https://github.com/ScratchAddons/ScratchAddons) und finde den  "Download code"-Knopf.

   ![Screenshot des Download code-Knopfes](/assets/img/docs/download-code-button.png)

2. Klicke ihn an und wähle "Download ZIP".

   ![Screenshot des Download ZIP-Knopfes](/assets/img/docs/download-zipball-button.png)

3. Extrahiere das Archiv in einen Ordner.

### Installation auf Google Chrome oder Microsoft Edge

1. Gib `chrome://extensions` in die Adressenleiste ein, um die Erweiterungenverwaltung zu öffnen.

2. Klicke auf den Schalter neben `Entwicklermodus`, um den Entwicklermodus zu aktivieren. Dies Erlaubt dir das Laden aus einem Ordner bzw. aus einer Datei.

   ![Screenshot der oberen Leiste der Erweiterungsverwaltung](/assets/img/docs/developer-mode-toggle.png)

3. Der `Entpackte laden`-Knopf sollte erscheinen. Klicke es an, um einen Ordner zum Hochladen auszuwählen.

   ![Screenshot für Entpackte laden](/assets/img/docs/load-unpacked-button.png)

4. Wähle den Extrahierten Ordner aus.
5. Die Erweiterung sollte nun geladen sein.

Um das Update abzuschließen (vorausgesetzt, du hast die Schritte [hier](#cloning-the-repository) befolgt), klicke auf `Aktualisieren`:

![Screenshot für Aktualisierungsknopf](/assets/img/docs/update-button.png)


### Auf Mozilla Firefox installieren

1. Tippe `about:debugging` in die Adressleiste, um die Debugging-Seite zu öffnen.

2. Klicke auf `Dieses Firefox` im Menü auf der linken Seite.

   ![Screenshot für linkes Menü](/assets/img/docs/left-hand-menu.png)

4. Klicke auf `Temporäres Add-on laden...`.

   ![Screenshot für Temporäres Add-on laden](/assets/img/docs/load-addon.png)

6. Wähle die manifest.json-Datei im extrahierten Ordner.
7. Die Erweiterung sollte nun geladen sein.

Hinweis: Firefox' Temporären Add-ons sind aktuell nur temporär. Sie werden beim Neustart von Firefox gelöscht, deshalb ist es empfohlen, einen auf Chromium basierenden Browser wie Google Chrome zu verwenden, um die Entwicklungsversion von Scratch Addons die ganze Zeit zu benutzen.

