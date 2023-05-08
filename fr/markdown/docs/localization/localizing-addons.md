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
  "ADDONID/cats": "{nombre, pluriel, un {1 chat} autre {# chats}}",
  "ADDONID/eat": "J'ai envie de manger {nourriture}!",
  "ADDONID/salmon": "salmon",
  "ADDONID/sardine": "sardine",
  "ADDONID/move-steps": {
  "string": "bouger {nombre} pas",
  "developer_comment": "Veuillez traduire ceci pour qu'il corresponde à la traduction officielle de  Scratch pour le bloc."
}
}
```

### Espaces réservés
Parfois, les messages doivent contenir des éléments générés dynamiquement. Par exemple, le nombre de chats ou l'entrée. Pour gérer cela, vous pouvez utiliser des espaces réservés comme `{nom de l'espace réservé}`. Le nom de l'espace réservé ne doit contenir que des lettres (pas de chiffres).

### Pluriels
Et si l'espace réservé est un nombre ? Nous pouvons utiliser des pluriels comme `{placeholderName, plural, one {quand il y a une chose} other {quand il y a # choses}}`. Si l'espace réservé est 1, il s'affichera "quand il y a une chose", sinon il dira "quand il y a des choses (de l'espace réservé)". 

### Commentaires développeurs

Transifex affichera le commentaire du développeur lorsqu'un traducteur aura sélectionné la chaîne spécifiée. Ces commentaires sont généralement utilisés pour demander une traduction particulière de la chaîne ou pour fournir des informations supplémentaires pour les langues qui ne font pas la différence entre les caractères majuscules et minuscules.
 

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
