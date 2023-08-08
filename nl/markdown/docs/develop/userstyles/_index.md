---
title: Userstyles
description: Userstyles zijn CSS-regels die Scratch-pagina's beïnvloeden. Ze kunnen stijlen toepassen op bestaande Scratch UI, net zoals elementen die door addons zijn toegevoegd.
---

Userstyles zijn CSS-regels die Scratch-pagina's beïnvloeden. Ze kunnen stijlen toepassen op bestaande Scratch UI, net zoals elementen die door addons zijn toegevoegd.


## Userstyles declareren in de addonmanifest

{{< admonition warning >}}
**Sommige veranderingen vereisen dat je de extensie herlaadt** van `chrome://extensions` om effect te hebben, zoals het addonmanifest-bestand updaten.

Het is niet nodig om de extensie te herladen wanneer je de bron van een al bestaand userstyle CSS-bestand verandert. In die gevallen is de pagina herladen genoeg.
{{< /admonition >}}

Userstyles worden gedeclareerd in een "userstyles"-array, vergelijkbaar met userscripts.

Elk item van de array moet de volgende eigenschappen hebben:
- `"url"`: de relatieve URL tot een CSS-bestand.
- `"matches"`: de lijst van Scratch-pagina's waar de userstyle van kracht is. Lees [matches](/docs/reference/addon-manifest/#matches) voor meer informatie.
- `if`: een lijst van voorwaarden die bepalen of de userstyle op dit moment toegepast moet worden of niet. Lees [userstyle.if](https://scratchaddons.com/docs/reference/addon-manifest/#if) voor meer informatie.

Voorbeeldmanifest:
```json
{
  "name": "Scratch Berichten",
  "description": "Laat je makkelijker je Scratchberichten lezen en erop antwoorden.",
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
      "name": "Berichtgrootte aanpassen",
      "id": "resize",
      "type": "boolean",
      "default": false
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```


## Userstyles dynamisch schakelen nadat pagina is geladen

Het is normaal gesproken onnodig om een JavaScript-userscipt te gebruiken om dynamisch te schakelen of een userstyle actief is op de pagina als reactie op de gebruiker die instellingen verandert.

- Includeer `dynamicEnable: true` in de addonmanifest om de extensie userstyles dynamisch in de pagina te laten zetten als de addon (voor de eerste keer) ingeschakeld wordt nadat de pagina is geladen.
- Includeer `dynamicDisable: true` in de addonmanifest om de extensie userstyles dynamisch weg te laten halen uit de pagina of juist er weer in te zetten als de addon wordt geschakeld, zonder dat de pagina moet herladen.
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


## Applying styles only inside the editor

The extension automatically toggles a class name on the `<body>` element when the user enters or exits the project editor.

For example, styling `<input>` elements inside and outside the editor differently:
```css
.sa-body-editor input {
  /* Only applies if `addon.tab.editorMode` is `editor` or `fullscreen` */
}

body:not(.sa-body-editor) input {
  /* Only applies if `addon.tab.editorMode` is NOT `editor` nor `fullscreen` */
}
```
