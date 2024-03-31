---
title: Установка
---

## Из магазинов расширений

Scratch Addons is available in these stores.

| Store | Установить | Supported browsers | Системные требования |
| - | - | - | - |
| Chrome Web Store | [![Install for Chrome Web Store](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 96+<br />Microsoft Edge 96+<br />Opera 82+<br />Brave 1.33+<br />Vivaldi 5.0+<br />*Chromium 96+* | Windows 7+<br />OS X / MacOS 10.11+
| Add-ons for Firefox | [![Install for Add-ons for Firefox](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 109+ | Windows 7+<br />OS X / MacOS 10.12+
| Microsoft Edge Add-ons | [![Install for Microsoft Edge Addons](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 96+ | Windows 7+<br />OS X / MacOS 10.11+

## Из исходного кода

### О релизах в GitHub

[Страница релизов](https://github.com/ScratchAddons/ScratchAddons/releases) содержит код и файлы установки для всех сборок Scratch Addons для разработчиков, а также зеркало сборок для магазинов.

### Клонирование репозитории

Это самый рекомендуемый способ для установки Scratch Addons для целей разработки. Для этого нужно установить Git, если у Вас его нет.

Чтобы скачать репозиторий, просто склонируйте `https://github.com/ScratchAddons/ScratchAddons.git`.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
Чтобы обновить Scratch Addons, сначала сделайте `cd` в папку Scratch Addons, а затем запустите следующие команды.

```sh
$ git fetch
$ git pull
```

Это обновит Scratch Addons и подготовит его к редактированию кода. Учтите, что Вам надо посмотреть финальную секцию обновления [здесь](#install-on-google-chrome), если Вы используете Google Chrome.


### Скачивание zipball

Если у Вас нет Git, то Вы можете попробовать этот способ. Обратите внимание, что Вам надо повторять вручную этот процесс каждый раз, когда Вы хотите обновить Scratch Addons.

1. Зайдите в [репозиторию](https://github.com/ScratchAddons/ScratchAddons) и найдите кнопку для скачивания кода.

   ![Скриншот кнопки для скачивания кода](/assets/img/docs/download-code-button.png)

2. Нажмите её и выберите «Download ZIP».

   ![Скриншот кнопки «Download ZIP»](/assets/img/docs/download-zipball-button.png)

3. Разархивируйте архив в папку.

### Installing on Google Chrome or Microsoft Edge

1. Напишите `chrome://extensions` в адресную строку, чтобы открыть страницу управления расширений.

2. Нажмите на переключатель рядом с надписью `Режим разработчика`, чтобы включить режим разработчика. Это позволяет Вам устанавливать расширения из папок или файлов.

   ![Extension Management top bar screenshot](/assets/img/docs/developer-mode-toggle.png)

3. Вы должны увидеть кнопку `Загрузить распакованное расширение`. Нажатие на неё позволяет Вас выбрать папку для загрузки.

   ![Скриншот кнопки «Загрузить распакованное расширение»](/assets/img/docs/load-unpacked-button.png)

4. Выберите распакованную папку.
5. Расширение должно быть сейчас загружено.

Чтобы завершить обновления (предполагая, что Вы выполнили [эти шаги](#cloning-the-repository)), кликните кнопку `Обновить`:

![Скриншот кнопки для обновления](/assets/img/docs/update-button.png)


### Установка на Mozilla Firefox

1. Напишите `about:debugging` в адресную строку браузера, чтобы открыть страницу отладки.

2. Кликните на `Этот Firefox` в левой панели.

   ![Скриншот левого меню](/assets/img/docs/left-hand-menu.png)

4. Кликните `Загрузить временное дополнение...`.

   ![Скриншот кнопки «Загрузить временное дополнение...»](/assets/img/docs/load-addon.png)

6. Выберите файл manifest.json внутри распакованной папки.
7. Расширение должно быть сейчас загружено.

Примечание: Временные дополнения Firefox на самом деле временные. Перезапуск Firefox удалит их, поэтому если Вы хотите использовать версию разработчиков Scratch Addons всё время, то лучше используйте браузер на основе Chromium, например Google Chrome.

