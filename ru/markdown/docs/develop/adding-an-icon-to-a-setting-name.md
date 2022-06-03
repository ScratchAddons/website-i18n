---
title: Добавление иконки к названию настройки
---
Для добавления иконки к настройке без [вызываний](https://github.com/ScratchAddons/ScratchAddons/pull/1529) [краша](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54),

- Убедитесь в том, что имя файла с иконкой не содержит дефисы
- Напишите `@ИМЯФАЙЛАИКОНКИ.svg название настройки` в `addon.json`
- Добавьте `ИМЯФАЙЛАИКОНКИ.svg` в `/images/icons/`, если нет
- Отредактируйте `/background/load-addon-manifests.js` с добавлением `iconfilenameIcon: "@ИМЯФАЙЛАИКОНКИ.svg",`
- Отредактируйте `/addons/scratch-notifier/notifier.js` для настроек уведомителя Scratch