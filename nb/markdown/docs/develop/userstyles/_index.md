---
title: Brukerstyler
description: Brukerstyler er CSS-regler som påvirker Scratch-sider. De kan bruke stiler på eksisterende Scratch UI, samt på elementer som ble lagt til på siden av tillegg.
---

Brukerstyler er CSS-regler som påvirker Scratch-sider. De kan bruke stiler på eksisterende Scratch UI, samt på elementer som ble lagt til på siden av tillegg.


## Deklarering av brukerstiler i tilleggsmanifestet

{{< admonition warning >}}
**Noen endringer krever en omstart av utvidelsen** fra `chrome://extensions` for å tre i kraft, for eksempel oppdatering av tilleggets manifestfil.

Det er ikke nødvendig å laste inn utvidelsen på nytt når du endrer kilden til en allerede eksisterende brukerstil CSS-fil. I slike tilfeller er det tilstrekkelig å laste inn siden på nytt. 
{{< /admonition >}}

Brukerstiler er deklarert inni en "brukerstiler" array, på samme måte som brukerskript.

Hvert element i arrayen må ha følgende egenskaper:
- `"url"`: den relative URL-en til en CSS-fil.
- `"matches"`: listen over Scratch-sider der brukerstilen vil bli brukt. Se [matches](/docs/reference/addon-manifest/#matches) for mer informasjon.
- `if`: en liste med betingelser som kan veksle om brukerstilen er aktivert eller ikke. Se [userstyle.if](https://scratchaddons.com/docs/reference/addon-manifest/#if) for mer informasjon.

Eksempel manifest:
```json
{
  "name": "Scratch Meldinger",
  "description": "Gir enkel lesing og svar på dine Scratch-meldinger.",
  "userstyles": [
    {
      "url": "styles.css",
      "matches": ["prosjekter", "https://scratch.mit.edu/", "profiler"]
    },
    {
      "url": "resize.css",
      "matches": ["prosjekter"],
      "if": {
        "settings": {
          "resize": true
        }
      }
    },
  ],
  "settings": [
    {
      "name": "Endre størrelse på meldinger",
      "id": "resize",
      "type": "boolean",
      "default": false
    }
  ],
  "tags": ["fellesskap"],
  "enabledByDefault": false
}
```


## Dynamisk veksling av brukerstiler etter sideinnlasting

Det er vanligvis unødvendig å bruke et JavaScript brukerscript for å dynamisk bytte om en brukerstil er aktiv på siden som respons på at brukeren endrer innstillinger.

- Inkludering av `dynamicEnable: true` i tilleggets manifest vil tillate utvidelsen å dynamisk injisere brukerstiler hvis tillegget har blitt aktivert (for første gang) etter at siden ble lastet.
- Inkludering av `dynamicDisable: true` i tilleggets manifest vil tillate utvidelsen å dynamisk fjerne eller gjeninnsatte brukerstiler hvis tillegget har blitt vekslet, uten å kreve en sideoppdatering.
- Inkludering av `updateUserstylesOnSettingsChange: true` i tilleggets manifest vil gjenevaluere "if" betingelser som avhenger av brukerinnstillinger uten å kreve en sideoppdatering. Utvidelsen vil fjerne eller injisere brukerstiler i henhold til dette.


## Å få tilgang til tilleggsinnstillinger fra CSS

Brukerstiler kan enkelt få tilgang til farge- og numeriske innstillinger gjennom CSS-variabler. De kan også få tilgang til innstillinger fra andre aktiverte tillegg.

CSS-variablene følger alltid formatet `--addonId-settingId`. Innstilling-ID-er blir alltid konvertert fra kebab-case til camelCase.

Disse CSS-variablene er alltid tilgjengelige for alle aktiverte tillegg, og ingen manifestegenskap er nødvendig for å eksponere dem. De synkroniseres også med brukerinnstillingene uten å kreve en sideoppdatering.

```css
.sa-progress-bar {
  /* Fargeinnstilling */
  background-color: var(--progressBar-bgColor);

  /* Fargeinnstilling med reserveløsning */
  border-color: var(--editorDarkMode-border, #fc7c24);
  /* Hvis editor-mørke-modus er deaktivert, vil reserveløsningen bli brukt i stedet */

  /* Numerisk innstilling */
  height: calc(1px * var(--progressBar-height));
}
```


## Tilpassede CSS-variabler

Hvis en brukerstil trenger å velge mellom to verdier basert på en bakgrunnsfarge (tekstkontrast) eller en tilleggsinnstilling, er ikke JavaScript nødvendig. Disse betingelsene, blant andre, kan deklareres i tilleggets manifest gjennom [customCssVariables](/docs/reference/addon-manifest/#customcssvariables), og brukerstilen kan enkelt referere til den CSS-variabelen.


## Applying styles based on the editor mode

The extension automatically toggles a class name on the `<html>` element when the user enters or exits the project editor.

For eksempel, stil `<input>` elementer inne og utenfor redigeringsverktøyet forskjellig:
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
