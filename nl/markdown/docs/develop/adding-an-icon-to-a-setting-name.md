---
title: Een Pictogram Toevoegen aan een Instellingsnaam
---
Om een pictogram toe te voegen aan een instellingsnaam zonder [crashes](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54) te [veroorzaken](https://github.com/ScratchAddons/ScratchAddons/pull/1529),

- Zorg ervoor dat de naam van het pictogrambestand geen lage streepjes bevat
- Schrijf `@ICONFILENAME.svg setting name` in `addon.json`
- Voeg `ICONFILENAME.svg` toe in `/images/icons/` als het mist
- Bewerk `/background/load-addon-manifests.js` om `iconfilenameIcon: "@ICONFILENAME.svg",` toe te voegen
- Bewerk `/addons/scratch-notifier/notifier.js` voor Scratch-Berichtgeverinstellingen