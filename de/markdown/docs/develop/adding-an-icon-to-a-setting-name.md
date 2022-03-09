---
title: Ein Symbol zu einem Einstellungennamen hnizufügen
---
So fügen Sie ein Symbol zu einem Einstellungsnamen hinzu, ohne [Abstürze](https://github.com/ScratchAddons/ScratchAddons/pull/1529) [zu verursachen](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54),

- Stellen Sie sicher, dass der Dateiname des Symbols keine Bindestriche enthält.
- Schreibe `@ICONFILENAME.svg Einstellungsname` in `addon.json`
- Falls nicht vorhanden, `ICONFILENAME.svg` unter `/images/icons/` hinzufügen
- Bearbeiten Sie `/background/load-addon-manifests.js` um `iconfilenameIcon: "@ICONFILENAME.svg",` hinzuzufügen
- Bearbeiten Sie `/addons/scratch-notifier/notifier.js` für Scratch Notifier Einstellungen