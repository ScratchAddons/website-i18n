---
title: Benutzerstile
description: Benutzerstile sind CSS-Regeln, die sich auf Scratch-Seiten auswirken. Sie können Stile auf die bestehende Scratch-Benutzeroberfläche sowie auf Elemente anwenden, die der Seite durch Addons hinzugefügt wurden.
---

Benutzerstile sind CSS-Regeln, die sich auf Scratch-Seiten auswirken. Sie können Stile auf die bestehende Scratch-Benutzeroberfläche sowie auf Elemente anwenden, die der Seite durch Addons hinzugefügt wurden.


## Benutzerstile im Addon-Manifest deklarieren

{{< admonition warning >}}
**Einige Änderungen erfordern eine Erweiterungsneuladung** von `chrome://extensions`, um wirksam zu werden, wie z. B. die Aktualisierung der Addon-Manifestdatei.

Es ist nicht notwendig, die Erweiterung neu zu laden, wenn die Quelle einer bereits vorhandenen CSS-Datei im Benutzerstil geändert wird. In diesen Fällen genügt es, die Seite neu zu laden.
{{< /admonition >}}

Benutzerstile werden in einem "userstyles"-Array deklariert, ähnlich wie Benutzerskripte.

Jedes Element dieses Arrays muss die folgenden Elemente haben:
- `"url"`: die relative URL zu einer CSS-Datei.
- `"matches"`: die Liste der Scratch-Seiten, auf die der Benutzerstil angewendet werden soll. Siehe [matches](/docs/reference/addon-manifest/#matches) für weitere Informationen.
- `if`: eine Liste von Bedingungen, die umschalten können, ob der Benutzerstil aktuell angewendet wird oder nicht. Siehe [userstyle.if](https://scratchaddons.com/docs/reference/addon-manifest/#if) für weitere Informationen.

Beispielsmanifest:
```json
{
  "name": "Scratch-Nachrichten",
  "description": "Bietet einfaches Lesen und Beantworten von Scratch-Nachrichten.",
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
      "name": "Nachrichten-Größe verändern",
      "id": "resize",
      "type": "boolean",
      "default": false
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```


## Dynamisches Umschalten der Benutzerstile nach dem Laden der Seite

In der Regel ist es nicht notwendig, ein JavaScript-Benutzerskript zu verwenden, um dynamisch umzuschalten, ob ein Benutzerstil auf der Seite aktiv ist, wenn der Benutzer die Einstellungen ändert.

- Die Aufnahme von `dynamicEnable: true` in das Addon-Manifest ermöglicht es der Erweiterung, nach dem Laden der Seite dynamisch Benutzerstile einzufügen, wenn das Addon (zum ersten Mal) aktiviert wurde.
- Das Einfügen von `DynamicDisable: true` in das Addon-Manifest ermöglicht es der Erweiterung, dynamisch Benutzerstile zu entfernen oder wieder einzufügen, wenn das Addon umgeschaltet wurde, ohne dass ein Neuladen der Seite erforderlich ist.
- Durch das Einfügen von `updateUserstylesOnSettingsChange: true` in das Addon-Manifest werden "if"-Bedingungen, die von den Benutzereinstellungen abhängen, neu ausgewertet, ohne dass ein Neuladen der Seite erforderlich ist. Die Erweiterung wird die Benutzerstile entsprechend entfernen oder einfügen.


## Zugriff auf Addon-Einstellungen über CSS

Benutzerstile können Farb- und numerische Einstellungen über CSS-Variablen leicht erhalten. Sie können auch auf Einstellungen von anderen aktivierten Addons zugreifen.

Die CSS-Variablen folgen immer dem Format `--addonId-settingId`. Einstellungs-IDs werden immer von Großbuchstaben in Kleinbuchstaben umgewandelt.

Diese CSS-Variablen sind immer für alle aktivierten Addons verfügbar und es ist keine Manifest-Eigenschaft erforderlich, um sie freizugeben. Sie werden auch mit den Benutzereinstellungen synchronisiert, ohne dass ein Neuladen der Seite erforderlich ist.

```css
.sa-progress-bar {
  /* Farb-Einstellung */
  background-color: var(--progressBar-bgColor);

  /* Farbeinstellung mit Fallback */
  border-color: var(--editorDarkMode-border, #fc7c24);
  /* Wenn der Editor-Dunkelmodus deaktiviert ist, wird stattdessen der Fallback-Modus verwendet */

  /* Numerische Einstellung */
  height: calc(1px * var(--progressBar-height));
}
```


## Benutzerdefinierte CSS-Variablen

Wenn ein Benutzerstil zwischen zwei Werten wählen muss, die auf einer Hintergrundfarbe (Textkontrast) oder einer Addon-Einstellung basieren, ist JavaScript nicht notwendig. Diese und andere Bedingungen können im Addon-Manifest über [customCssVariables] (/docs/reference/addon-manifest/#customcssvariables) deklariert werden, und der Benutzerstil kann einfach auf diese CSS-Variable verweisen.


## Anwendung von Stilen nur innerhalb des Editors

Die Erweiterung schaltet automatisch einen Klassennamen auf dem Element `<body>` um, wenn der Benutzer den Projekteditor betritt oder verlässt.

Beispiel: Unterschiedliche Gestaltung von `<input>`-Elementen innerhalb und außerhalb des Editors:
```css
.sa-body-editor input {
  /* Gilt nur, wenn `addon.tab.editorMode` `editor` oder `fullscreen` ist */
}

body:not(.sa-body-editor) input {
  /* Gilt nur, wenn `addon.tab.editorMode` weder `editor` noch `fullscreen` ist */
}
```
