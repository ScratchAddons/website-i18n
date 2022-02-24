---
title: Создание аддона
---
Нужное программное обеспечение: текстовый редактор, Chrome.  
Если возможно, отключите расширение Scratch Addons, которое Вы скачали с магазина до продолжения, чтобы избежать проблемы.

## Step 1: Read about [addon basics](/docs/develop/getting-started/addon-basics/)
Не забудьте прочитать эту статью, чтобы знать терминологию.

## Шаг 2: Сделайте fork/клон репозитории
Или скачайте как ZIP, если хотите. Иными словами, просто скачайте исходный код локально.

## Шаг 3: Загрузите расширение в Chrome
*Примечание: рекомендуется Chrome для работы с аддонами. Всё же, аддоны также должны работать на Firefox.*  
Теперь, когда у Вас есть расширение на Вашей файловой системе, зайдите на `chrome://extensions` и включите «режим разработчика».  
Кликните на «загрузить распакованное расширение», затем выберите папку, где находится Scratch Addons. Если у Вас есть проблемы с этим, убедитесь, что Вы выбираете папку, где есть файл `manifest.json`.  
Готово, Вы загрузили расширение! Это должно выглядеть по типу этого:  
![изображение](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)  
Примечание: Вы можете проигнорировать «ошибки». Это просто предупреждение о неизвестном ключе манифеста, который нужен браузеру Firefox.

## Шаг 4: О чём Ваш аддон?
Теперь самое интересное!  
Что будет делать Ваш аддон? Подумайте о само-описывающем ID аддона (англ. символы, без пробелов или специальных символов кроме дефисов).  
Подумали?

## Шан 5: Сделайте папку для аддона
Используя файловый менеджер, зайдите в папку, где находится Scratch Addons на Вашей файловой системе. Войдите в папку `addons`.  
Затем создайте папку с Вашим эпичным ID аддона как название.

## Шаг 6: Добавьте манифест аддона
Манифест аддона говорит Scratch Addons о том, как Ваш аддон работает. Убедитесь, чтобы Вы сделали это правильно, чтобы избежать головной боли.  
Внутри папки, которую Вы создали, создайте файл `addon.json`.  
Это основа, на которой Вы можете начать программировать, не забудьте её поменять в будущем:
```json
{
  "name": "Epic placeholder text in place of addon name",
  "description": "Hello World! It would be really smart to replace this placeholder text with a description.",
  "tags": ["community"],
  "enabledByDefault": false
}
```
For more information on what you can declare in the manifest, check [this article](/docs/reference/addon-manifest/).


## Шаг 7: Скажите Scratch Addons, какой ID у Вашего аддона
Scratch Addons не может найти новые папки самому, поэтому Вам нужно добавить имя папки в специальный файл.  
Зайдите в `папкаScratchAddons/addons/addons.json` и добавьте ID Вашего аддона в массив.

## Шаг 8: Привет, мир
Ваш аддон пока что ничего не делает, поэтому сейчас хорошее время проверить, работает ли всё, что мы только что сделали.  
Зайдите на `chrome://extensions` и перезапустите Scratch Addons с помощью символа перезагрузки на её карточке.  
Теперь нажмите ПКМ по значку Scratch Addons и нажмите «настройки».  
Вы должны увидеть свой аддон в списке! Когда Вы его найдёте, включите его и задайте настройки аддона, если они есть.

## Шаг 9: Самая интересная часть, код!
*Перед продолжением, убедитесь, что Вы прочитали статью в вики, ссылка на которую есть в 1-ом шаге.*  

Теперь самая интересная часть: создайте свои JS или CSS файлы!  
Важно: после изменения Вашего аддона, не забудьте перезагрузить расширение Scratch Addons так, как Вы сделали в 8-ом шагу.  

В зависимости от того, что будет делать Ваш аддон, Вы можете посмотреть эти вики статьи:
- [Userscripts](/docs/develop/addon-types/userscripts)
- [Userstyles](/docs/develop/addon-types/userstyles)

## Step 10: Make your addon customizable
If you want, you can make your addon customizable!  
Users of your addon will be able to toggle settings, enter numbers, and more!  
To get started, see [how to declare settings in the addon manifest](/docs/reference/addon-manifest/#settings-object).  
Then, head to the [addon.settings documentation](/docs/reference/addon-api/addon.settings) to learn how to access user choices from userscripts.

## Step 11: Before publishing your addon
Now that your addon works, let's make sure we can add it to the addon library.  
Make sure your addon's manifest is suitable, [more info here](/docs/reference/addon-manifest). Keep close attention to the name, description and tags of your addon. Make sure to set `"enabledByDefault"` to `false` or remove it.  
Make sure your addon doesn't break other addons.  
Make sure your code is understandable; having unnecessary comments is better than no comments.

## Step 12: Send a pull request!
Fork the repo if you haven't already, commit your new addon and send a PR!  
Keep in mind we might request you to make some changes, however, we will probably accept your addon as long as it's minimally suitable.
