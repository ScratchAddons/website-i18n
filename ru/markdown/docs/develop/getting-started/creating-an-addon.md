---
title: Создание аддона
---
Нужное программное обеспечение: текстовый редактор, Chrome.  
Если возможно, отключите расширение Scratch Addons, которое Вы скачали с магазина до продолжения, чтобы избежать проблемы.


{{< admonition info >}}
If you plan to submit the addon you are developing as a pull request to our GitHub repository, please read our [contributing guidelines](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md) first. 

In case there is no existing GitHub issue in that repository related to your new addon idea, please [create one](https://github.com/ScratchAddons/ScratchAddons/issues/new/choose). However, if there is already an issue related to your feature idea, we suggest that you leave a comment on it stating your intention to develop the addon. This will enable other contributors to provide feedback on whether the addon could be accepted, or if further discussion is required.

However, if you are creating an addon for personal use, you may proceed with this guide.
{{< /admonition >}}

## Шаг 1: Прочитайте о [основах аддона](/ru/docs/develop/getting-started/addon-basics/)
Не забудьте прочитать эту статью, чтобы знать терминологию.

## Step 2: Fork/clone the [repo](https://github.com/ScratchAddons/ScratchAddons)
Follow [these instructions](/docs/getting-started/installing/#from-source) to download the source code locally.

## Шаг 3: Загрузите расширение в Chrome
*Note: Chrome is recommended for working on addons. Nevertheless, addons are expected to work on Firefox and Edge.*  
Now that you have the extension in your filesystem, go to `chrome://extensions` and toggle "developer mode".  
Click "load unpacked", then select the folder where Scratch Addons is located. If you're having issues with this, make sure to be selecting the folder where `manifest.json` is located.  
That's it, you loaded the extension! It should look similar to this:  
![image](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)  
Note: you can safely ignore it says "errors". That's just a warning for an unrecognized manifest key that's required by Firefox.

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
  "name": "Эпичный текст-заполнитель в месте названия аддона",
  "description": "Привет, мир! Было бы умно заменить этот текст-заполнитель описанием.",
  "tags": ["community"],
  "enabledByDefault": false
}
```
Для большей информацией о том, что Вы можете указать в манифесте, посмотрите [эту статью](/ru/docs/reference/addon-manifest/).


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
- [Userscripts](/docs/develop/userscripts)
- [Userstyles](/docs/develop/userstyles)

## Шаг 10: Сделайте свой аддон настраиваемым
If you want, you can make your addon customizable!  
Users of your addon will be able to toggle settings, enter numbers, and more!  
To get started, see [how to declare settings in the addon manifest](/docs/reference/addon-manifest/#settings-object).  
Then, head to the [addon.settings documentation](/docs/reference/addon-api/addon.settings) to learn how to access user choices from userscripts.

## Шаг 11: До публикования аддона
Теперь когда Ваш аддон работает, давайте убедимся в том, что мы можем его добавить в библиотеку аддонов.  
Убедитесь в том, что манифест Вашего аддона подходящий, [больше информации находится здесь](/docs/reference/addon-manifest). Обращайте внимание на имя, описание и тэги аддона. Не забудьте поставить `"enabledByDefault"` значение `false` или удалить этот ключ.  
Убедитесь в том, что Ваш аддон не ломает другие.  
Убедитесь, что Ваш код понятен; необязательные комментарии лучше, чем никаких комментариев.
Также не забудьте поменять название и описание на английское.

## Шаг 12: Отправьте pull запрос!
Follow the steps on our [contributing guidelines](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md). Simply put, fork the repo if you haven't already, commit your new addon and send a PR!  
Keep in mind we might request you to make some changes, however, we will probably accept your addon as long as it's minimally suitable.
