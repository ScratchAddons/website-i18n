---
title: Dodawanie ikony do nazwy ustawień
---
Aby dodać ikonę do nazwy ustawienia bez [powodowania](https://github.com/ScratchAddons/ScratchAddons/pull/1529) [awari](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54), 

- Upewnij się, że nazwa pliku ikony nie zawiera myślników 
- Napisz `@ICONFILENAME.svg` jako ustawienie w pliku `addon.json`
- Dodaj plik `@ICONFILENAME.svg` w folderze `/images/icons/`
- Edytuj plik  `/background/load-addon-manifests.js`, aby dodać `nazwaplikuikonyIcon: "@ICONFILENAME.svg",`
- Edytuj `/addons/scratch-notifier/notifier.js`, aby edytować ustawienia powiadomień.