---
title: Styles utilisateur
description: Les styles utilisateur sont des règles CSS qui affectent les pages Scratch. Ils peuvent appliquer des styles à l'interface utilisateur Scratch existante, ainsi qu'aux éléments qui ont été ajoutés à la page par des addons.
---

Les styles utilisateur sont des règles CSS qui affectent les pages Scratch. Ils peuvent appliquer des styles à l'interface utilisateur Scratch existante, ainsi qu'aux éléments qui ont été ajoutés à la page par des addons.


## Déclarer des styles utilisateur dans le manifeste de l'addon

{{< admonition warning >}}
**Certaines modifications nécessitent un rechargement d'extension** à partir de `chrome://extensions` pour prendre effet, comme la mise à jour du fichier manifeste de l'addon.

Il n'est pas nécessaire de recharger l'extension lorsque l'on modifie la source d'un fichier CSS de style utilisateur déjà existant. Dans ce cas, il suffit de recharger la page.
{{< /admonition >}}

Les styles utilisateur sont déclarés dans un array "userstyles", de la même manière que les scripts utilisateur.

Chaque élément de l'array doit avoir les propriétés suivantes :
- `"url"`: l'URL relative d'un fichier CSS.
- `"matches"` : la liste des pages Scratch où le style utilisateur sera appliqué. Voir [matches](/docs/reference/addon-manifest/#matches) pour plus d'informations.
- `if` : une liste de conditions qui peuvent faire que le style utilisateur soit appliqué ou non. Voir [userstyle.if](https://scratchaddons.com/docs/reference/addon-manifest/#if) pour plus d'informations.

Example :
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


## Activer ou désactiver dynamiquement les styles utilisateur après le chargement de la page

Il n'est généralement pas nécessaire d'utiliser un script utilisateur JavaScript pour activer ou désactiver dynamiquement un style utilisateur sur la page lorsque l'utilisateur modifie ses paramètres.

- Inclure `dynamicEnable: true` dans le manifeste de l'addon permettra à l'extension d'injecter dynamiquement des styles utilisateurs si l'addon a été activé (pour la première fois) après le chargement de la page.
- Inclure `dynamicDisable: true` dans le manifeste de l'addon permettra à l'extension de supprimer ou réinjecter dynamiquement les styles utilisateur en fonction de l'état d'activation de l'addon, sans nécessiter un rechargement de la page.
- Inclure `updateUserstylesOnSettingsChange: true` dans le manifeste de l'addon va réévaluer les conditions "if" qui dépendent des paramètres de l'utilisateur sans nécessiter un rechargement de la page. L'extension supprimera ou injectera les styles utilisateur en conséquence.


## Accéder aux paramètres des addons à partir du CSS

Les styles utilisateur peuvent facilement obtenir des paramètres de couleur et des paramètres numériques par le biais de variables CSS. Ils peuvent également accéder aux paramètres d'autres addons activés.

Les variables CSS suivent toujours le format `--addonId-settingId`. Les identifiants des paramètres sont toujours convertis de "kebab-case" en "camelCase".

Ces variables CSS sont toujours disponibles pour tous les addons activés et aucune propriété de manifeste n'est nécessaire pour les exposer. Elles sont également synchronisées avec les paramètres de l'utilisateur sans qu'il soit nécessaire de recharger la page.

```css
.sa-progress-bar {
  /* Paramètres de couleur */
  background-color: var(--progressBar-bgColor);

  /* Paramètres de couleur avec fallback */
  border-color: var(--editorDarkMode-border, #fc7c24);
  /* Si editor-dark-mode est désactivé, le fallback sera utilisé à la place. */

  /* Paramètres numériques */
  height: calc(1px * var(--progressBar-height));
}
```


## Variables CSS personnalisées

Si un style utilisateur doit choisir entre deux valeurs en fonction d'une couleur d'arrière-plan (contraste du texte) ou d'un paramètre de l'addon, JavaScript n'est pas nécessaire. Ces conditions, entre autres, peuvent être déclarées dans le manifeste de l'addon via [customCssVariables](/docs/reference/addon-manifest/#customcssvariables), et le style utilisateur peut simplement faire référence à cette variable CSS.


## Appliquer des styles uniquement dans l'éditeur

L'extension fait automatiquement basculer un nom de classe sur l'élément `<body>` lorsque l'utilisateur entre ou sort de l'éditeur de projet.

Par exemple, le style des éléments `<input>` à l'intérieur et à l'extérieur de l'éditeur est différent :
```css
.sa-body-editor input {
  /* Ne s'applique que si `addon.tab.editorMode` est `editor` ou `fullscreen` */
}

body:not(.sa-body-editor) input {
  /* Ne s'applique que si `addon.tab.editorMode` n'est PAS `editor` ni `fullscreen`. */
}
```
