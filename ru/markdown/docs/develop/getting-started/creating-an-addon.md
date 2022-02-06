---
title: Создание аддона
---
Нужное программное обеспечение: текстовый редактор, Chrome.  
Если возможно, отключите расширение Scratch Addons, которое Вы скачали с магазина до продолжения, чтобы избежать проблемы.

## Шаг 1: Прочитайте о [основах аддона](addon-basics)
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
  "name": "Аааааааааа мой аддон",
  "description": "Привет, мир!",
  "tags": ["community"],
  "enabledByDefault": false
}
```
Для больше информации о том, что Вы можете написать в манифесте, см. [эту статью](/docs/developing/the-addon-manifest-(addon.json)).


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
- [Постоянные скрипты](/docs/develop/addon-types/persistent-scripts)
- [Юзерскрипты](/docs/develop/addon-types/userscripts)
- [Юзерстили](/docs/develop/addon-types/userstyles)

## Шаг 10: Сделайте свой аддон настраиваемым
Вы можете сделать свой аддон настраиваемым!  
Пользователи Вашего аддона смогут переключать настройки, вводить цифры и многое другое!  
См. [как объявить настройки в манифесте аддона](/docs/reference/addon-manifest/#settings-object).  
Затем, зайдите в [документацию addon.settings](/docs/reference/addon-api/addon.settings) чтобы узнать, как получить выбор пользователей с юзерскриптов и постоянных скриптов.

## Шаг 11: До публикования аддона
Теперь когда Ваш аддон работает, давайте убедимся в том, что мы можем его добавить в библиотеку аддонов.  
Убедитесь в том, что манифест Вашего аддона подходящий, [больше информации находится здесь](/docs/reference/addon-manifest). Обращайте внимание на имя, описание и тэги аддона. Не забудьте поставить `"enabledByDefault"` значение `false` или удалить этот ключ.  
Убедитесь в том, что Ваш аддон не ломает другие.  
Убедитесь, что Ваш код понятен; необязательные комментарии лучше, чем никаких комментариев.

## Шаг 12: Отправьте pull запрос!
Сделайте fork репозитории, если не сделали, зафиксируйте свой новый аддон и отправьте pull request!  
Мы можем Вас попросить сделать некоторые изменения, однако мы скорее всего подтвердим Ваш аддон, если он хотя бы минимально подходящий.