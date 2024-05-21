---
title: Conseils de débogage
description: Conseils pour déboguer facilement les scripts utilisateur, et les cas limites à considérer.
---

Conseils pour déboguer facilement les scripts utilisateur, et les cas limites à considérer.

## Conseils

### Il n'est pas toujours nécessaire de recharger l'extension

Il n'est pas nécessaire de recharger l'extension en accédant à `chrome://extensions` lors du changement de source d'un fichier JavaScript ou CSS déjà existant. Dans ces cas, il suffit de recharger la page.

### Utiliser l'API addon.* depuis la console

The `addon` object is accessible within the browser console through the `__addon` global variable when at least one addon is running.

### Définissez des points d'arrêt avec le mot-clé "debugger"

Le mot clé `debugger;` en JavaScript gèlera la page lors de son exécution, si les outils de développement sont ouverts. La définition de points d'arrêt est utile pour inspecter la valeur des variables locales lors de l'exécution.
 

### Filtrer les messages de la console par ID d’addon

Saisissez l’ID supplémentaire dans la barre de recherche de la console "filtre" pour afficher uniquement les journaux et les avertissements, ainsi que les erreurs enregistrées avec `console.error()`. Gardez à l’esprit que cela va masquer toutes les exceptions, sauf si vous les enregistrez explicitement dans votre code.


## cas limites


### Page projet scratch et éditeur


#### Le DOM est détruit après être allé à l’intérieur ou à l’extérieur de l’éditeur

Scratch crée tous les éléments HTML chaque fois que l'utilisateur clique sur "voir à l'intérieur" ou "voir la page du projet", et détruit les anciens.
Cela peut généralement être résolu en utilisant `addon.tab.waitForElement` ou l'événement `urlChange`.

#### Le langage de l’éditeur Scratch peut être modifié sans rechargement

Contrairement au site Web Scratch, l’éditeur Scratch ne se recharge pas lorsque vous modifiez la langue. Lors de la sélection d’un langage différent, Scratch peut détruire et recréer certains éléments HTML.

#### Autres situations à considérer

- L’éditeur de projet peut être utilisé sans un ID de projet défini (par exemple, lorsqu’il est déconnecté).
- L’éditeur peut passer de LTR à RTL (ou vice versa) sans avoir besoin de recharger une page.


### Le site web scratch

#### scratch-www pages ne se rechargent pas après s’être connecté

Contrairement aux pages scratchr2, les pages scratch-www ne forcent pas le rechargement d’une page après la connexion. Par exemple, si vous accédez à une page de projet alors que vous êtes déconnecté, puis connectez-vous, la page ne se rechargera pas. Cela affecte également les studios, la page des messages, etc. 
En revanche, toutes les pages Scratch se rechargent après la déconnexion.

#### Les pages de projet ne renvoient rien (404)

Même si le projet n'est pas partagé ou n'existe pas, Scratch renvoie un code d'état HTTP 200. Le message "notre serveur se gratte la tête" est ajouté dynamiquement à la page par Scratch.

#### Autres situations à considérer

- Chacun des 4 onglets à l’intérieur des studios ont des URL différentes, mais ne déclenchent pas une navigation navigateur. Les addons qui affectent l’une des 4 pages doivent s’exécuter, peu importe l’URL initiale.
