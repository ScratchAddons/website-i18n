---
title: Styles utilisateur
description: Les styles utilisateur vous permettent d’injecter du CSS sur le site Web Scratch - utile pour rendre les boutons que vous ajoutez avec des scripts utilisateur colorés, ou pour personnaliser l’élément Scratch natif.
---
## De quoi s’agit-il ? 
Les styles utilisateur vous permettent d’injecter du CSS sur le site Web Scratch - utile pour rendre les boutons que vous ajoutez avec des scripts utilisateur colorés, ou pour personnaliser l’élément Scratch natif.

## Comment ajouter un style utilisateur ? 
 **Assurez-vous d’actualiser scratch Addons à partir de `chrome://extensions` après avoir apporté des modifications à votre addon.**  
Accédez au manifeste de votre addon (addon.json) et ajoutez une propriété appelée `''userstyles''`.  
Cette propriété doit être un tableau.  Chaque élément du tableau doit avoir les propriétés suivantes : `"url"` et `''matches''`. 
 `"url"` doit être une URL relative à un fichier CSS.  
`''matches''` doit être un tableau d’URL dans lequel vous souhaitez que le style utilisateur soit injecté. Vous pouvez utiliser des astérisques. Exemple de manifeste :
```json
{
  "name": "Scratch Messaging",
  "description": "Fournit une lecture et une réponse faciles à vos messages Scratch.",
  "userstyles": [
    {
      "url": "userstyle.css",
      "matches": ["https://scratch.mit.edu/*"]
    },
    {
      "url": "second_userstyle.css",
      "matches": ["https://scratch.mit.edu/projects/*", "https://scratch.mit.edu/users/*"]
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```

## Débuguer des styles utilisateur
**Assurez-vous d'actualiser Scratch Addons à partir de `chrome://extensions` après avoir apporté des modifications à votre addon.** 
Si vous ne voyez pas votre style utilisateur fonctionner, vérifiez que votre addon est activé. 
Si vous rencontrez toujours des problèmes, veuillez créer un problème dans ce dépôt.
