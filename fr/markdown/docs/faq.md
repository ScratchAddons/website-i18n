---
title: Foire Aux Questions
description: Cette page liste toute les questions posées fréquemment sur l'extension et le projet Scratch Addon.
---

Cette page liste toute les questions posées fréquemment sur l'extension et le projet Scratch Addon.

### Qu'est-ce que Scratch Addons ?

Scratch Addons est une extension de navigateur tout-en-un pour le site web Scratch et l'éditeur de projet. Il fournis des fonctionnalités et des thèmes (appelé addons en interne), autant que pour le site Scratch que pour l'éditeur de projet. La mission de Scratch Addons est de combiner toute les extensions de Scratch,  les scripts et les styles d'utilisateur, développé pas plusieurs membre de la communauté Scratch, vers un seul et même endroit facile d'accès, out en laissant les utilisateurs choisir ceux à activer.

### Qu'est-ce qu'un "Addon" exactement ?

Un addon est similaire à une extension ou à un userscript, mais ils utilisent des API spéciales fournies par l'extension Scratch Addons. Ces API permettent aux addons d'exécuter des scripts sur une page Scratch (userscripts) ou d'appliquer des styles au site Web Scratch (userstyles).

Les scripts utilisateur peuvent utiliser les API JavaScript `addon.*`, qui leur permettent d'obtenir des informations relatives à Scratch (par exemple, obtenir l'utilisateur actuellement connecté) et également d'utiliser des API d'extension (comme l'envoi de notifications).

### Si tout est un addon, alors que fait Scratch Addons ? 

En soi, Scratch Addons n’est qu’un chargeur d’addons. Ses principales tâches sont :

- Autorise l'utilisateur d'activer, de désactiver ou de configurer les addons. 
- Exécutez des addons et fournissez-leur des API. 
- Fournir des statistiques globale aux addons (par exemple, addon.auth API) 
- Polluer les prototypes pour une utilisation par des scripts d'utilisateur de l'addon. 
- Fournissez des moyens d’accéder à l’état Redux et de le modifier. 
- Évitez aux addons d’interférer les uns avec les autres. 
- Évitez de dupliquer le travail de différents addons. 

### Scratch Addons est-il sûr ?

Oui. Scratch Addons n’a aucun problème de sécurité dans la version la plus récente. Scratch Addons est un projet open source, de sorte que le code est constamment vérifié par les contributeurs Scratch Addons, ainsi que par les réviseurs du Chrome Web Store et add-ons pour Firefox. 

### Comment puis-je signaler une faille de sécurité ?

Si vous trouvez une faille de sécurité, veuillez contacter World_Languages ​​en privé en envoyant un e-mail à `worldxlanguages ​​(at) gmail.com`. Si vous ne recevez pas de réponse dans les 48 heures, veuillez créer un problème [ici](https://github.com/ScratchAddons/ScratchAddons/issues/) en mentionnant que vous avez envoyé un e-mail.

Vous pouvez soit [lire notre politique de sécurité](https://github.com/ScratchAddons/ScratchAddons/security/policy), soit [consulter nos avis que nous avons publiés](https://github.com/ScratchAddons/ScratchAddons/ security/advisories?state=published).

### Mon compte sera-t-il en sécurité lorsque j'utilise Scratch Addons ?

Scratch Addons n'utilise pas les informations d'identification de votre compte pour fonctionner essentiellement. En fait, vous pouvez être déconnecté de Scratch et les addons Scratch fonctionneront toujours. Scratch Addons n'enverra que des demandes basées sur les cookies que vous avez, qui sont fournis par le navigateur pour chaque demande, donc certains addons comme Scratch Messaging ne fonctionneront pas lorsque vous vous connecterez, mais cela n'affectera pas les autres parties de l'extension.

Addons sur Scratch Les addons ont également été audités par plusieurs contributeurs sur le référentiel, donc personne ne peut simplement glisser du code malveillant sous nos yeux.

We never send Scratch account information or extension settings outside of your browser. See [the extension privacy policy](/docs/privacy/policies/extension) for more information.

### Puis-je parler aux gens de Scratch Addons sur Scratch ?

You can't, and please don't. There is a policy that forbids advertising browser extensions/userscripts [here](https://scratch.mit.edu/discuss/post/2907564/). You may, however, use different methods to tell your friends about Scratch Addons.

### Comment puis-je contribuer à Scratch Addons ?

Tout d'abord, merci de votre intérêt à contribuer à Scratch Addons. Nous apprécions votre intérêt et vos contributions ultérieures.

En tant que projet open source, nous accueillons tout type de contributions. Vous n'avez même pas besoin de nous demander ou d'avoir un certain rang. Tout le monde est le bienvenu. Il est même possible que vous ne réalisiez même pas que vous avez contribué au projet !

Anyway, back to the point. You can contribute in many ways, and some of it is really easy

- **Contribute some code**

  If you can code on JavaScript, HTML5, and CSS, you can contribute by doing some coding/programming. You can fix bugs, tackle some requests, or create your own addon.

  After that, you need to create a pull request. You can do so by forking [the repository](https://github.com/ScratchAddons/ScratchAddons/), do your necessary changes, and create a pull request. If it is deemed feasible, we will merge it.

  We're also open for contributions of other aspects than the extension. You can view our repositories on [our GitHub organization page](https://github.com/ScratchAddons) and help us build them.

- **Suggérer une idée** 

  Have something that you think would be a good addition to Scratch Addons? [Tell us!](#i-think-you-missed-a-feature-what-can-i-do)

- **Report a bug**

  Found a bug in one of our addon, the settings page, or anything else on our extension? [Send us a bug report](#what-can-i-do-if-i-find-a-problem).

- **Translate Scratch Addons**  

  If you can speak another language than English fluently, you can help translate/localize Scratch Addons to your language. You can start from [here](/docs/localization/joining-the-localization-team).

- **Write the documentation**

  Are you familiar with Scratch Addons? If so, you can write the documentation for it. The documentation can include how to use it, or how it works. Please contact us on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) for further information.

- **Send feedback**  

  You can send feedback on our form, located at [the feedback page](https://scratchaddons.com/feedback). Your feedback may give us a different perspective in the extension development and help us know things needed attention and fix bugs.

- **Leave a review on the stores**

  You can leave us a review about Scratch Addons on [the Chrome extension page](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) or [the Firefox addon page](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/).

- **Star our repository**

  Basically, the GitHub star is similar to the Scratch star/favorite. You can do this by going to [our repository](https://github.com/ScratchAddons/ScratchAddons) and click the "Star" button on the top-right corner.

- **Spread the word**

  You can tell anyone about Scratch Addons, like your friends, your relatives, your family members, or even your teacher, if you want. We're just asking you to [not do this on the Scratch website](#can-i-tell-people-about-scratch-addons-on-scratch).

### How can I create my own addon?

Read more about how to create an addon on Scratch Addons [here](/docs/develop/getting-started).

### How can I put my name on the [contributors page](/contributors)?

Please read and follow the instruction of [this issue](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}) in order to have your name on said page.

### How can I remove my name from the [contributors page](/contributors)?

If you don't want your name to be on the page, please tell us by creating an issue on [our contributors repository](https://github.com/ScratchAddons/contributors/issues/), or by other means of contact. We're sorry for the inconvenience.

### What can I do if I find a problem?

You can tell us using one of these methods.

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

### How can you activate the easter egg addons?

To reveal the easter egg addons, do the Konami Code (↑↑↓↓←→←→BA) with your keyboard on the settings page. After that, the easter egg addons will be shown, letting you to activate them.

Some of our easter egg addons are "Fix capitalization of Account Settings" and "Semicolon glitch". Check out [the addons tab](/addons) for a complete list.

### I have more questions!

If you have more questions that need answers, you can create a post on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) or send a message [on our Discord server](https://discord.gg/R5NBqwMjNc). Someone will try to answer it for you.