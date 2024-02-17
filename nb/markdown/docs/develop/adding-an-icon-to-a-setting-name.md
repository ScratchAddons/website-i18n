---
title: Legge til et ikon på et innstillingsnavn
---
For å legge til et ikon til et innstillingsnavn uten å [forårsake] (https://github.com/ScratchAddons/ScratchAddons/pull/1529) [krasj] (https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54),

- Pass på at ikonfilnavnet ikke inneholder bindestreker.
- Skriv `@ICONFILENAME.svg` innstilling navn på `addon.json`
- Legg til `ICONFILENAME.svg` på `/images/icons/` hvis det mangler.
- Rediger `/background/load-addon-manifests.js` for å legge til `iconfilenameIcon: "@ICONFILENAME.svg",`
- Rediger `/addons/scratch-notifier/notifier.js` for innstillinger for Scratch Notifier.