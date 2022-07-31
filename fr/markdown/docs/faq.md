---
title: Foire Aux Questions
description: Cette page liste toute les questions posées fréquemment sur l'extension et le projet Scratch Addon.
---

Cette page liste toute les questions posées fréquemment sur l'extension et le projet Scratch Addon.

### Qu'est-ce que Scratch Addons ?

Scratch Addons est une extension de navigateur "tout-en-un" pour le site web Scratch et son éditeur de projet. Elle fournit des fonctionnalités et des thèmes (appelé addons en interne), autant pour le site Scratch que pour son éditeur de projet. La mission de Scratch Addons est de combiner toute les extensions de Scratch, les scripts et les styles utilisateur développés par plusieurs membres de la communauté Scratch, vers un seul et même endroit facile d'accès, en laissant les utilisateurs choisir ceux à activer.

### Qu'est-ce qu'un "Addon" exactement ?

Un addon est similaire à une extension ou à un script utilisateur, mais il utilise des API spéciales fournies par l'extension Scratch Addons. Ces API permettent aux addons d'exécuter des scripts sur une page Scratch (scripts utilisateur) ou d'appliquer des styles au site Web Scratch (styles utilisateur).

Les scripts utilisateur peuvent utiliser les API JavaScript `addon.*`, qui leur permettent d'obtenir des informations relatives à Scratch (par exemple, obtenir l'utilisateur actuellement connecté) et également d'utiliser des API d'extension (comme l'envoi de notifications).

### Si tout est un addon, alors que fait Scratch Addons ? 

En soi, Scratch Addons n’est qu’un chargeur d’addons. Ses principales tâches sont :

- Autoriser l'utilisateur à activer, désactiver ou configurer les addons. 
- Exécuter des addons et leur fournir des API. 
- Apporter des statistiques globales aux addons (par exemple, l'API addon.auth).
- Permettre aux scripts utilisateur d'insérer ou modifier le code de Scratch sans avoir à remplacer l'ensemble des scripts de la page.
- Fournir des moyens d'accéder et de modifier l'état de Redux.
- Éviter aux addons d’interférer les uns avec les autres. 
- Éviter de dupliquer le travail de différents addons. 

### Scratch Addons est-il sûr ?

Yes. Scratch Addons should not have any security issues in its most recent version. Scratch Addons is an open source project, so the code is constantly being verified by Scratch Addons contributors, as well as by reviewers from the Chrome Web Store, Add-ons for Firefox and Microsoft Edge Add-ons.

### Comment puis-je signaler une faille de sécurité ?

Si vous trouvez une faille de sécurité, veuillez contacter World_Languages ​​en privé en envoyant un e-mail à `worldxlanguages@gmail.com`. Si vous ne recevez pas de réponse dans les 48 heures, veuillez créer un problème [ici](https://github.com/ScratchAddons/ScratchAddons/issues/) en mentionnant que vous avez envoyé un e-mail.

Vous pouvez soit [lire notre politique de sécurité](https://github.com/ScratchAddons/ScratchAddons/security/policy), soit [consulter les avis que nous avons publiés](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### Mon compte sera-t-il en sécurité lorsque j'utilise Scratch Addons ?

Scratch Addons n'utilise pas les informations d'identification de votre compte pour fonctionner. En fait, vous pouvez être déconnecté de Scratch, les addons Scratch fonctionneront toujours. Scratch Addons n'enverra que des requêtes basées sur vos cookies, qui sont fournis par le navigateur pour chaque requête, donc certains addons comme la Messagerie Scratch ne fonctionneront pas lorsque vous vous déconnecterez, mais cela n'affectera pas les autres parties de l'extension.

Les addons de Scratch Addons ont également été audités par plusieurs contributeurs sur le dépôt, donc personne ne peut glisser du code malveillant sous nos yeux.

Nous n'envoyons jamais les informations de compte Scratch ou les paramètres d'extension en dehors de votre navigateur. Voir [la politique de confidentialité de l'extension](/docs/privacy/policies/extension) pour plus d'informations.

### Puis-je parler aux gens de Scratch Addons sur Scratch ?

Vous ne pouvez pas, et s'il vous plaît ne le faites pas. Il existe une règle qui interdit de faire de la publicité pour des extensions de navigateur/scripts utilisateur sur Scratch, voir [ici](https://scratch.mit.edu/discuss/post/2907564/). Vous pouvez en revanche utiliser d'autres méthodes pour parler de Scratch Addons autour de vous.

### Comment puis-je contribuer à Scratch Addons ?

Tout d'abord, merci de votre intérêt à contribuer à Scratch Addons. Nous apprécions votre intérêt et vos contributions ultérieures.

En tant que projet open source, nous accueillons tout type de contributions. Vous n'avez même pas besoin de nous demander ou d'avoir un certain rang. Tout le monde est le bienvenu. Il est même possible que vous ne réalisiez même pas que vous avez contribué au projet !

Anyway, back to the point. You can contribute in many ways, and some of it is really easy

- **Contribuez du code**

  Si vous connaissez le JavaScript, HTML5 et CSS, vous pouvez contribuer en programmant. Vous pouvez corriger des bugs, ajouter de nouvelles fonctionnalités ou même créer votre propre addon.

  Après ça, vous pouvez ouvrir une demande de fusion (pull request). Pour cela, créez un fork [du dépôt](https://github.com/ScratchAddons/ScratchAddons/), faites-y vos changements et créez une demande de fusion. Si votre addon s'inscrit dans la lignée de ce que propose Scratch Addons, alors il sera ajouté.

  Nous acceptons aussi des contributions autres que celles concernant l'extension. Vous pouvez consulter nos dépôts sur [la page de notre organisation GitHub](https://github.com/ScratchAddons) et nous aider en y contribuant.

- **Suggérer une idée** 

  Vous pensez avoir une idée qui serait une bonne addition à Scratch Addons ? [Dites-le nous !](#i-think-you-missed-a-feature-what-can-i-do)

- **Rapporter un bug**

  Vous avez trouvé un bug dans un de nos addons, sur la page des paramètres ou concernant notre extension ? [Envoyez-nous un rapport de bug](#what-can-i-do-if-i-find-a-problem).

- **Traduire Scratch Addons**

  Si vous parlez une langue autre que l'anglais couramment, vous pouvez aider à traduire Scratch Addons dans cette langue. Vous pouvez vous renseigner [ici](/docs/localization/joining-the-localization-team).

- **Écrire de la documentation**

  Vous êtes familier avec Scratch Addons ? Si oui, vous pouvez écrire de la documentation sur ce sujet. La documentation peut être entre-autre sur comment utiliser Scratch Addons ou sur comment Scratch Addons fonctionne. Contactez-nous sur [notre page de discussion](https://github.com/ScratchAddons/ScratchAddons/discussions) pour plus d'information.

- **Envoyer des commentaires**

  You can send feedback on our form, located at [the feedback page](https://scratchaddons.com/feedback). Your feedback may give us a different perspective in the extension development and help us know things needed attention and fix bugs.

- **Laissez un avis sur les boutiques**

  You can leave us a review about Scratch Addons on [the Chrome extension page](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco), [the Firefox addon page](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) or the [Microsoft Edge addon page](https://microsoftedge.microsoft.com/addons/detail/scratch-addons/iliepgjnemckemgnledoipfiilhajdjj).

- **Star our repository**

  Basically, the GitHub star is similar to the Scratch star/favorite. You can do this by going to [our repository](https://github.com/ScratchAddons/ScratchAddons) and click the "Star" button on the top-right corner.

- **Spread the word**

  You can tell anyone about Scratch Addons, like your friends, your relatives, your family members, or even your teacher, if you want. We're just asking you to [not do this on the Scratch website](#can-i-tell-people-about-scratch-addons-on-scratch).

### Comment créer mon propre addon?

Read more about how to create an addon on Scratch Addons [here](/docs/develop/getting-started).

### How can I put my name on the [contributors page](/contributors)?

Please read and follow the instruction of [this issue](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}) in order to have your name on said page.

### How can I remove my name from the [contributors page](/contributors)?

If you don't want your name to be on the page, please tell us by creating an issue on [our contributors repository](https://github.com/ScratchAddons/contributors/issues/), or by other means of contact. We're sorry for the inconvenience.

### Qu'est-ce que je peux faire si je trouve un problème ?

Vous pouvez nous en faire part par l'un de ces moyens.

- Send it through [our feedback form](https://scratchaddons.com/feedback).
- Create an issue on [the repository](https://github.com/ScratchAddons/ScratchAddons/issues).
- Create a post on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Tell us on [our Discord server](https://discord.gg/R5NBqwMjNc).

### I think you missed a feature. What can I do?

If you think a feature is missing, or you want to suggest an addon to the extension, or you have a good idea, tell us by [following one of the methods mentioned above](#what-can-i-do-if-i-find-a-problem).

### Where can I discuss about Scratch Addons?

You can do it on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) or [our Discord server](https://discord.gg/R5NBqwMjNc). There, you can discuss about it and ask questions if you're having trouble.

### I think Scratch Addons slows down Scratch. What can I do?

Try to turn off addons that you don't need. Also, check addon notices and warnings to decide which addons should be turned off for better performance. 

### Comment activer l'ajout easter egg ?

To reveal the easter egg addons, do the Konami Code (↑↑↓↓←→←→BA) with your keyboard on the settings page. After that, the easter egg addons will be shown, letting you to activate them.

Some of our easter egg addons are "Fix capitalization of Account Settings" and "Semicolon glitch". Check out [the addons tab](/addons) for a complete list.

### J'ai plus de question!

If you have more questions that need answers, you can create a post on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) or send a message [on our Discord server](https://discord.gg/R5NBqwMjNc). Someone will try to answer it for you.
