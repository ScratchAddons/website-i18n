---
title: Dodajanje ikone k imenu nastavitve
---
Da v ime nastavitve dodate ikono, ne da bi to [povzročilo](https://github.com/ScratchAddons/ScratchAddons/pull/1529) [težave](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54),

- Prepričajte se, da ime datoteke z ikono ne vsebuje vezajev
- Spremenite ime nastavitve v datoteki `addon.json` v `@IMEIKONE.svg ime nastavitve`
- Dodajte datoteko `IMEIKONE.svg` v mapo `/images/icons/`, če je tam še ni
- Dodajte `imeikoneIcon: "@IMEIKONE.svg",` v `/background/load-addon-manifests.js`
- Če gre za nastavitev dodatka Scratch Notifier, uredite še datoteko `/addons/scratch-notifier/backgroud.js`