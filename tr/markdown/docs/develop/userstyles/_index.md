---
title: Userstyle'lar
description: Userstyle'lar, Scratch sayfalarını etkileyen CSS kurallarıdır. Bunlar, stilleri mevcut Scratch kullanıcı arayüzüne ve eklentiler tarafından sayfaya eklenen ögelere uygulayabilirler.
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

Kullanıcının ayarları değiştirmesine yanıt olarak sayfada bir userstyle'ın etkin olup olmadığını dinamik olarak açıp kapamak için bir JavaScript userscript kullanmak genellikle gereksizdir.

- Eklenti manifest dosyasına `dynamicEnable: true` ifadesinin eklenmesi, eklentinin sayfa yüklendikten sonra (ilk kez) etkinleştirilmesi durumunda uzantının dinamik olarak userstyle'lar eklemesine olanak tanır.
- Eklenti manifest dosyasına `dynamicDisable: true` ifadesinin eklenmesi, eklentinin değiştirilmesi durumunda sayfanın yenilenmesine gerek kalmadan uzantının userstyle'larını dinamik olarak kaldırmasına veya yeniden eklemesine olanak tanır.
- Eklenti manifest dosyasına `updateUserstylesOnSettingsChange: true` ifadesinin eklenmesi, sayfanın yenilenmesine gerek kalmadan kullanıcı ayarlarına bağlı "if" koşullarını yeniden değerlendirecektir. Uzantı, buna göre userstyle'ları kaldıracak veya yerleştirecektir.


## Eklenti ayarlarına CSS üzerinden erişmek

Userstyle'lar renk ve sayısal ayarlara CSS değişkenleri aracılığıyla kolaylıkla erişebilir. Ayrıca diğer aktif eklentilerin ayarlarına da erişebilirler.

CSS değişkenleri her zaman `--addonId-settingId` yapısını takip eder. Ayar ID'leri her zaman kebab-case'ten camelCase'e dönüştürülür.

Bu CSS değişkenleri etkin olan tüm eklentiler için her zaman mevcuttur ve bunları kullanıma sokmak için herhangi bir manifest özelliği gerekli değildir. Ayrıca sayfanın yeniden yüklenmesine gerek kalmadan kullanıcı ayarlarıyla da senkronize çalışırlar.

```css
.sa-progress-bar {
  /* Renk ayarı */
  background-color: var(--progressBar-bgColor);

  /* Fallback'li renk ayarı */
  border-color: var(--editorDarkMode-border, #fc7c24);
  /* Düzenleyici karanlık modu devre dışı bırakılırsa bunun yerine fallback kullanılacaktır */

  /* Sayısal ayar */
  height: calc(1px * var(--progressBar-height));
}
```


## Özelleştirilmiş CSS değişkenleri

Eğer bir userstyle bir arka plan rengine (metin kontrastı) veya bir eklenti ayarına göre iki değerden birini seçmesi gerekiyorsa, JavaScript gerekli değildir. Bu koşullar, diğerlerinin yanı sıra [customCssVariables](/docs/reference/addon-manifest/#customcssvariables) üzerinden eklenti manifest'inden tanımlanabilir ve userstyle kolaylıkla bu CSS değişkenine referans verebilir.


## Stilleri yalnızca düzenleyicinin içinde uygulamak

Uzantı, kullanıcı proje düzenleyicisine girdiğinde veya çıktığında `<body>` ögesinde sınıf adını otomatik olarak değiştirir.

Örneğin `<input>` elementleri, düzenleyicinin içinde ve dışında farklı stilize edilir:
```css
.sa-body-editor input {
  /* Yalnızca `addon.tab.editorMode` `editor` ya da `fullscreen` ise uygulanır */
}

body:not(.sa-body-editor) input {
  /* Yalnızca `addon.tab.editorMode` ne `editor`, ne de `fullscreen` ise uygulanır */
}
```
