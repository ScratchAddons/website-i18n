---
title: Aggiungere un'icona a una particolare Impostazione
---
Per aggiungere un'icona ad una particolare impostazione senza [causare](https://github.com/ScratchAddons/ScratchAddons/pull/1529) [crash](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54),

- Assicurati che il nome del file dell'icona non contenga trattini
- Scrivi `@NOMEFILEICONA.svg nome impostazione` in `addon.json`
- Aggiungi `NOMEFILEICONA.svg` a `/images/icons/` se manca
- Modifica `/background/load-addon-manifests.js` aggiungendo `iconfilenameIcon: "@NOMEFILEICONA.svg",`
- Modifica `/addons/scratch-notifier/background.js` per le impostazioni delle Notifiche di Scratch