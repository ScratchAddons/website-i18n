---
title: Scripts utilisateurs
description: Les scripts utilisateurs sont des fichiers JavaScript qui sont exécutés chaque fois que l’utilisateur charge une page Scratch. Ils peuvent modifier le HTML du document, ajouter de nouveaux boutons, personnaliser le comportement de l’éditeur Scratch, et bien plus encore.

---

Les scripts utilisateurs sont des fichiers JavaScript qui sont exécutés chaque fois que l’utilisateur charge une page Scratch. Ils peuvent modifier le HTML du document, ajouter de nouveaux boutons, personnaliser le comportement de l’éditeur Scratch, et bien plus encore.

De la même manière que les scripts utilisateur que vous pouvez télécharger pour les gestionnaires de scripts utilisateur tels que Tampermonkey ou Greasemonkey, les scripts utilisateur Scratch Addons sont constitués de morceaux de JavaScript qui sont exécutés dans le même contexte d'exécution que le code JavaScript de Scratch lui-même. Dans le vocabulaire des extensions de navigateur, ce contexte d'exécution est souvent appelé le "monde principal".

Même si les scripts utilisateur Scratch Addons font partie d'une extension de navigateur, ils ne peuvent accéder à aucune API `chrome.*` ou `browser.*`. Au lieu de cela, Scratch Addons propose une [`addon.*` API](/docs/reference/addon-api/).


## Déclarer des userscripts dans le manifeste addon

{{< admonition warning >}}
**Certaines modifications nécessitent un rechargement d'extension** à partir de `chrome://extensions` pour prendre effet, comme la mise à jour du fichier manifeste de l'addon.

Il n'est pas nécessaire de recharger l'extension lors de la modification de la source d'un fichier JavaScript userscript déjà existant. Dans ces cas, il suffit de recharger la page.
{{< /admonition >}}

Les scripts utilisateur sont déclarés dans un array "userscripts".

Chaque élément de l'array doit avoir les propriétés suivantes :
- `"url"`:Chaque élément du tableau doit avoir les propriétés suivantes :
- `"matches"` : la liste des pages Scratch où le script utilisateur sera exécuté. Voir [matches](/docs/reference/addon-manifest/#matches) pour plus d'informations.

Example :
```json
{
  "name": "Copier le lien vers le bouton de commentaire",
  "description": "Ajoute un bouton \"Copier le lien\" à tous les commentaires sur le site Web, à côté du bouton \"Signaler\".",
  "scripts utilisateur": [
  {
    "url": "userscript.js",
    "matches": ["projets", "https://scratch.mit.edu/", "profils", "studios"]
  }
],
"tags": ["communauté"],
"enabledByDefault": faux
}
```
 

## Création de votre premier userscript

Contrairement aux scripts de contenu d’extension et aux scripts utilisateur Tampermonkey, vous devez envelopper tout votre code dans une exportation par défaut du module :
```js
// Exemple de script utilisateur
exporter la fonction asynchrone par défaut ({ addon, console }) {
  console.log("Bonjour" + wait addon.auth.fetchUsername());
  console.log("Comment allez-vous aujourd’hui?");
}
```

Rappelez-vous que JavaScript permet de déclarer des fonctions dans d’autres fonctions, par exemple :
```js
exporter la fonction asynchrone par défaut ({ addon, console }) {
fonction asynchrone sayHelloToUser() {
console.log("Bonjour, " + attendre addon.auth.fetchUsername());
}

attendre sayHelloToUser();
console.log("Comment allez-vous aujourd'hui ?");
}
```

{{< admonition info >}}
Vous pouvez accéder à de nombreux utilitaires d'API `addon.*` à partir de scripts utilisateur. Par exemple, vous pouvez obtenir le nom d'utilisateur actuel, attendre qu'un élément existe sur la page ou obtenir une référence à l'objet Scratch VM.
 

Pour plus d'informations, consultez la [référence API](/docs/reference/addon-api/).
 {{< /admonition >}}


## Modification du document HTML

Utilisez [browser DOM APIs](https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API) pour personnaliser le HTML de la page.

Voici un exemple:
```js
const myButton = document.createElement("button");
myButton.textContent = "Click me!";
myButton.classList.add("button");
myButton.setAttribute("title", "You're hovering a button");

const myContainer = document.querySelector(".container");
myContainer.append(myButton);
```

## Localisation des scripts utilisateur

Les scripts utilisateur des modules complémentaires doivent parfois faire référence à des mots ou des phrases en anglais. Assurez-vous de ne pas les coder en dur, afin qu'ils puissent faire partie du processus de traduction.

{{< admonition error >}}
```js
// A ne pas faire:
document.querySelector(".sa-find-bar").placeholder = "Find blocks";
```
{{< /admonition >}}

Pour créer une chaîne traduisible, procédez comme suit :
1. Créez un fichier nommé `addon-id.json` dans le dossier `/addon-l10n/en`.
2. Fournir un ID pour chaque chaîne :
```json
{
  "addon-id/find": "Find blocks"
}
```
3. Assurez-vous d’importer la fonction `msg()` dans votre userscript. La première ligne de votre userscript devrait ressembler à ceci :
```js
export default async function ({ addon, console, msg  }) {
                                              // ^^^
```
4. Utilisez la fonction `msg()` dans votre code, au lieu d'une chaîne codée en dur :
```js
document.querySelector(".sa-find-bar").placeholder = msg("find");
```
 

{{< admonition info >}}
Pour plus d'informations sur la localisation des scripts utilisateur, consultez [cette page](/docs/localization/localizing-addons/).
{{</admonition >}}


## Détails techniques

Chaque fichier userscript est un module JavaScript qui exporte une fonction. Scratch Addons n'importe le module que si nécessaire et l'exécute après le chargement complet de la page.

Les userscripts sont des modules JavaScript, donc ils fonctionnent toujours en ["strict mode"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode). Cela signifie également que les userscripts peuvent utiliser [top-level imports](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) pour importer d’autres fichiers JavaScript.

L'ordre dans lequel les scripts utilisateur s'exécutent peut varier à chaque chargement de page. Après le chargement de la page, l'utilisateur peut activer dynamiquement certains addons dans un ordre personnalisé, de sorte que l'ordre d'exécution n'est jamais garanti. Certaines API comme [`addon.tab.appendToSharedSpace`](/docs/reference/addon-api/addon.tab/addon.tab.appendtosharedspace/) tentent de corriger les conditions de concurrence potentielles et les comportements inattendus lors de l'activation dynamique des addons.

### runAtComplete

Les scripts utilisateur peuvent choisir d'être exécutés avant le chargement complet de la page en spécifiant `"runAtComplete": false` dans le manifeste de l'addon, une fois pour chaque script utilisateur.

À partir de maintenant, seul `document.head` est garanti d'exister lors de l'exécution précoce d'un script utilisateur. À l'avenir, l'existence de `document.body` sera également garantie, de sorte qu'aucun script utilisateur ne sera jamais exécuté avant que le document HTML ne soit suffisamment chargé pour atteindre `</head><body>`.
