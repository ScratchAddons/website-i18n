---
title: Ajout d'une icône à un nom de paramètre
---
Pour ajouter une icône à un nom de paramètre sans [causer](https://github.com/ScratchAddons/ScratchAddons/pull/1529) [planter](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54),

- Assurez-vous que le nom du fichier d'icône ne contient pas de tirets
- Écrivez `@ICONFILENAME.svg nom du paramètre` sur `addon.json`
- Ajouter `ICONFILENAME.svg` à `/images/icons/` si manquant
- Modifiez `/background/load-addon-manifests.js` pour ajouter `iconfilenameIcon : "@ICONFILENAME.svg",`
- Éditer manuellement `/addons/scratch-notifier/notifier.js` pour personnaliser les paramètres des notification Scratch