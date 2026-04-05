---
title: Пользовательские стили
description: Пользовательские стили — это правила CSS, которые влияют на страницы Scratch. Они могут применять стили к существующему пользовательскуму интерфейсу, а также к элементам, добавленным дополнениями.
---

Пользовательские стили — это правила CSS, которые влияют на страницы Scratch. Они могут применять стили к существующему пользовательскуму интерфейсу, а также к элементам, добавленным дополнениями.


## Объявления пользовательских стилей в манифесте дополнения

{{< admonition warning >}}
**Некоторые изменения требуют перезагрузки расширения** со страницы `chrome://extensions` для применения, включая обновление файла манифеста дополнения.

Не обязательно перезагружать расширение при изменении исходного кода уже существующего файла CSS пользовательского стиля. В тех случаях достаточно перезагрузки страницы.
{{< /admonition >}}

Пользовательские стили объявлены в массиве "userstyles", схоже пользовательским сценариям.

Каждый предмет массива должен иметь следующие свойства:
- `"url"`: относительная гиперссылка к файлу CSS.
- `"matches"`: список страниц Scratch, где пользовательские стили будут применены. Смотрите [совпадения](/docs/reference/addon-manifest/#matches) для исчерпывающей информации.
- `if`: список условий, которые могут переключать активность пользовательского стиля. Читайте [пользовательский стиль.если](https://scratchaddons.com/docs/reference/addon-manifest/#if) для большего объяснения.

Примерный манифест:
```json
{
  "name": "Scratch Messaging",
  "description": "Provides easy reading and replying to your Scratch messages.",
  "userstyles": [
    {
      "url": "styles.css",
      "matches": ["projects", "https://scratch.mit.edu/", "profiles"]
    },
    {
      "url": "resize.css",
      "matches": ["projects"],
      "if": {
        "settings": {
          "resize": true
        }
      }
    },
  ],
  "settings": [
    {
      "name": "Resize messages",
      "id": "resize",
      "type": "boolean",
      "default": false
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```


## Динамическое переключение пользовательских стилей после полной загрузки страницы

Обычно не нужно использовать пользовательский сценарий JavaScript для динамического переключения активности пользовательского стиля в ответ изменения человеком настроек.

- Включение `dynamicEnable: true` в манифесте дополнения разрешит расширению динамически внедрять пользовательские стили если дополнение было включено (в первый раз) после загрузки страницы.
- Including `dynamicDisable: true` in the addon manifest will allow the extension to dynamically remove or reinject userstyles if the addon has been toggled, without requiring a page reload.
- Including `updateUserstylesOnSettingsChange: true` in the addon manifest will re-evaluate "if" conditions that depend on user settings without requiring a page reload. The extension will remove or inject userstyles accordingly.


## Accessing addon settings from CSS

Userstyles can easily obtain color and numerical settings through CSS variables. They can also access settings from other enabled addons.

The CSS variables always follow the `--addonId-settingId` format. Setting IDs are always converted from kebab-case to camelCase.

These CSS variables are always available for all enabled addons and no manifest property is necessary to expose them. They are also synchronized with user settings without requiring a page reload.

```css
.sa-progress-bar {
  /* Color setting */
  background-color: var(--progressBar-bgColor);

  /* Color setting with fallback */
  border-color: var(--editorDarkMode-border, #fc7c24);
  /* If editor-dark-mode is disabled, the fallback will be used instead */

  /* Numerical setting */
  height: calc(1px * var(--progressBar-height));
}
```


## Custom CSS variables

If a userstyle needs to choose between one of two values based on a background color (text contrast) or an addon setting, JavaScript isn't necessary. These conditions, among others, can be declared in the addon manifest through [customCssVariables](/docs/reference/addon-manifest/#customcssvariables), and the userstyle can simply reference that CSS variable.


## Applying styles based on the editor mode

The extension automatically toggles a class name on the `<html>` element when the user enters or exits the project editor.

For example, styling `<input>` elements inside and outside the editor differently:
```css
.sa-editor input {
  /* Only applies if `addon.tab.editorMode` is `editor` or `fullscreen` */
}

:root:not(.sa-editor) input {
  /* Only applies if `addon.tab.editorMode` is NOT `editor` nor `fullscreen` */
}
```

Similarly, the `.sa-fullscreen` class is added to the `<html>` element when the project is in full screen mode:
```css
.sa-fullscreen [class*="green-flag_green-flag_"] {
  /* Only applies if `addon.tab.editorMode` is `fullscreen` */
}

:root:not(.sa-fullscreen) [class*="green-flag_green-flag_"] {
  /* Only applies if `addon.tab.editorMode` is NOT `fullscreen` */
}
```
