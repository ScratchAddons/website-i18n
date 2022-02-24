---
title: Localiser des extensions
description: Localiser des extensions est facile.
---
Localiser des extensions est facile.

## Ajouter des messages
En dessous `addons-l10n/en/`, créer un ficher nommé `ADDONID.json`,  ADDONID est l'ID de l'addons (the folder name). Écrivez le message que vous voulez traduire ici:

```json
{
"ADDONID/meow": "Meow",
"ADDONID/cats": "{number, plural, one {1 cat} other {# cats}}",
"ADDONID/eat": "Je veux manger de la {nourriture}!",
"ADDONID/salmon": "salmon",
"ADDONID/sardine": "sardine"
}
```

### Espaces réservés
Parfois, les messages doivent contenir des éléments générés dynamiquement. Par exemple, le nombre de chats ou l'entrée. Pour gérer cela, vous pouvez utiliser des espaces réservés comme `{nom de l'espace réservé}`. Le nom de l'espace réservé ne doit contenir que des lettres (pas de chiffres).

### Pluriels
Et si l'espace réservé est un nombre ? Nous pouvons utiliser des pluriels comme `{placeholderName, plural, one {quand il y a une chose} other {quand il y a # choses}}`. Si l'espace réservé est 1, il s'affichera "quand il y a une chose", sinon il dira "quand il y a des choses (de l'espace réservé)". 

## Utiliser les traductions
Changez la première ligne de votre script utilisateur à partir de quelque chose comme :
```
exporter par défaut async fonction ({ addon, console}) {
```

à:
```
exporter par défaut async fonction ({ addon, console}) {
```

Le `msg` ajouté est la fonction que vous utilisez pour obtenir des traductions. Par exemple, `text = "Meow"` peut maintenant être `text = msg("meow")`. L'ID de l'addon et la barre oblique sont omis.

### Espaces Réservés
Vous pouvez fournir des valeurs d'espace réservé :
```js
cat = msg("cats", {number: 1}) // shows "1 chats"
cats = msg("cats", {number: 3}) // shows "3 chats"
hungry = msg("eat", {food: "cod"}) // shows "Je veux manger!"
```

Vous pouvez également "imbriquer" des messages :
```js
hungry2 = msg("eat", {food: msg("salmon")}) // shows "I want to eat salmon!"
```

### Sécurité
If you are writing raw HTML, `msg` should be replaced with safer version of `safeMsg`.
