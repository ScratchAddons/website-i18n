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
- Includeer `updateUserstylesOnSettingsChange: true` in de addonmanifest om de "if"-condities die afhangen van gebruikersinstellingen opnieuw te laten evalueren. De extensie zal userstyles overeenkomstig weghalen of erin zetten.


## Toegang krijgen tot addoninstellingen van CSS

Userstyles kunnen makkelijk kleur- en numerieke instellingen bekijken door CSS-variabelen. Ze kunnen ook toegang krijgen tot instellingen van andere ingeschakelde addons.

De CSS-variabelen volgen altijd het `--addonId-settingId`-formaat. Setting ID's worden altijd omgezet van kebab-case naar camelCase.

Deze CSS-variabelen zijn altijd beschikbaar voor alle ingeschakelde addons en geen manifest-eigenschap is nodig om ze te exposen. Ze zijn ook gesynchroniseerd met gebruikersinstellingen zonder de pagina te moeten herladen.

```css
.sa-progress-bar {
  /* Kleurinstelling */
  background-color: var(--progressBar-bgColor);

  /* Kleurinstelling met terugval */
  border-color: var(--editorDarkMode-border, #fc7c24);
  /* Als editor-dark-mode uitgeschakeld is, wordt de terugvalkleur gebruikt */

  /* Numerieke instelling */
  height: calc(1px * var(--progressBar-height));
}
```


## Aangepaste CSS-variabelen

JavaScript is niet nodig als een userstyle tussen één van twee waarden moet kiezen met een achtergrondkleur (tekstcontrast) of een addoninstelling. Deze condities, inclusief anderen, kunnen worden gedeclareerd in de addonmanifest door [customCssVariables](/docs/reference/addon-manifest/#customcssvariables), en de userstyle kan simpelweg naar die CSS-variabele verwijzen.


## Stijlen alleen in de editor toepassen

De extensie schakelt automatisch een class-naam op het `<body>`-element wanneer de gebruiker de projecteditor in- of uitgaat.

Bijvoorbeeld, de `<input>`-elementen binnen en buiten de editor een andere stijl geven:
```css
.sa-body-editor input {
  /* Past alleen toe als `addon.tab.editorMode` `editor` of `fullscreen` is */
}

body:not(.sa-body-editor) input {
  /* Past alleen toe als `addon.tab.editorMode` NIET `editor` noch `fullscreen` is */
}
```
