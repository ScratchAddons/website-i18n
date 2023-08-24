---
title: Userstyle'lar
description: Userstyle'lar, Scratch sayfalarını etkileyen CSS kurallarıdır. Bunlar, stilleri mevcut Scratch kullanıcı arayüzüne ve eklentiler tarafından sayfaya eklenen öğelere uygulayabilirler.
---

Userstyle'lar, Scratch sayfalarını etkileyen CSS kurallarıdır. Bunlar, stilleri mevcut Scratch kullanıcı arayüzüne ve eklentiler tarafından sayfaya eklenen öğelere uygulayabilirler.


## Eklenti manifest dosyasında userstyle'ları tanımlamak

{{< admonition warning >}}
Eklenti manifest dosyasının güncellenmesi gibi **bazı değişikliklerin etkili olması için uzantının `chrome://extensions` adresinden yeniden yüklenmesi gerekir**.

Hâlihazırda var olan bir userstyle CSS dosyasının kaynağını değiştirdiğinizde uzantıyı yeniden yüklemenize gerek yoktur. Bu tür durumlarda, sayfayı yenilemek yeterlidir.
{{< /admonition >}}

Userstyle'lar, userscript'lere benzer şekilde bir "userstyles" dizisi (array'i) içerisinde tanımlanır.

Dizinin her ögesi aşağıdaki özelliklere sahip olmalıdır:
- `"url"`: bir CSS dosyasına ilişkin URL.
- `"matches"`: userstyle'ların uygulanacağı Scratch sayfalarının listesi. Daha fazla bilgi için [matches](/docs/reference/addon-manifest/#matches) sayfasına bakın.
- `if`: userstyle'ın şu anda uygulanıp uygulanmıyor olduğunu değiştirebilecek koşulların listesi. Daha fazla bilgi için [userstyle.if](https://scratchaddons.com/docs/reference/addon-manifest/#if)'e bakın.

Örnek manifest:
```json
{
  "name": "Scratch Mesajlaşma",
  "description": "Scratch mesajlarınızı kolayca okumanızı ve yanıtlamanızı sağlar.",
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
      "name": "Mesajları yeniden boyutlandır",
      "id": "resize",
      "type": "boolean",
      "default": false
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```


## Sayfa yüklendikten sonra userstyle'ları dinamik olarak değiştirmek

It is usually unnecessary to use a JavaScript userscript to dynamically toggle whether a userstyle is active on the page in response to the user changing settings.

- Including `dynamicEnable: true` in the addon manifest will allow the extension to dynamically inject userstyles if the addon has been enabled (for the first time) after loading the page.
- Including `dynamicDisable: true` in the addon manifest will allow the extension to dynamically remove or reinject userstyles if the addon has been toggled, without requiring a page reload.
- Including `updateUserstylesOnSettingsChange: true` in the addon manifest will re-evaluate "if" conditions that depend on user settings without requiring a page reload. The extension will remove or inject userstyles accordingly.


## Eklenti ayarlarına CSS üzerinden erişmek

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


## Özelleştirilmiş CSS değişkenleri

If a userstyle needs to choose between one of two values based on a background color (text contrast) or an addon setting, JavaScript isn't necessary. These conditions, among others, can be declared in the addon manifest through [customCssVariables](/docs/reference/addon-manifest/#customcssvariables), and the userstyle can simply reference that CSS variable.


## Stilleri yalnızca düzenleyicinin içinde uygulamak

The extension automatically toggles a class name on the `<body>` element when the user enters or exits the project editor.

For example, styling `<input>` elements inside and outside the editor differently:
```css
.sa-body-editor input {
  /* Yalnızca `addon.tab.editorMode` `editor` ya da `fullscreen` ise uygulanır */
}

body:not(.sa-body-editor) input {
  /* Yalnızca `addon.tab.editorMode` ne `editor`, ne de `fullscreen` ise uygulanır */
}
```
