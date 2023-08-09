---
title: Créer un Addon
---
Logiciels requirent : éditeur de texte, Chrome.
Si possible, désactivez l'extension Scratch Addons que vous avez téléchargée de la boutique avant de procéder pour éviter des problèmes.


{{< admonition info >}}Si vous avez l’intention de soumettre l’extension que vous développez en tant que demande de tirage à notre dépôt GitHub, veuillez d’abord lire nos [directives de contribution] (https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md). 

S'il n'y a pas de problème GitHub existant dans ce référentiel lié à votre nouvelle idée d'addon, veuillez [en créer un](https://github.com/ScratchAddons/ScratchAddons/issues/new/choose). Cependant, s'il existe déjà un problème lié à votre idée de fonctionnalité, nous vous suggérons de laisser un commentaire indiquant votre intention de développer l'addon. Cela permettra aux autres contributeurs de fournir des commentaires sur l'acceptation de l'addon ou sur la nécessité d'une discussion plus approfondie.

Cependant, si vous créez un addon pour un usage personnel, vous pouvez continuer avec ce guide.{{< /admonition >}}

## Étape 1 : Lisez les [bases des addons](/docs/develop/getting-started/addon-basics/)
Assurez-vous de lire cet article pour vous familiariser avec la terminologie.

## Étape 2 : Fourchez/clonez le [repo](https://github.com/ScratchAddons/ScratchAddons)
Suivez [ces instructions](/docs/getting-started/installing/#from-source) pour télécharger le code source localement.

## Étape 3 : Chargez l'extension dans Chrome
*Note : Chrome est recommandé pour travailler sur des addons. Néanmoins, les addons devraient fonctionner sur Firefox et Edge.*
Maintenant que vous avez l'extension dans votre système de fichiers, allez sur `chrome://extensions` et activer le "mode développeur".
Cliquez sur "charger l'extension non empaquetée", puis sélectionnez le fichier de l'extension Scratch Addons. Si vous rencontrez des problèmes à ce niveau, soyez sûrs de sélectionner le dossier dans lequel le fichier `manifest.json` se trouve.
C'est tout, vous avez chargé l'extension ! Ça devrait ressembler à cela : ![image](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)
Note : il n'y a pas de risques à l'ignorer si il y a marqué "erreurs". C'est juste un avertissement pour une clé manifeste non-reconnue requise par Firefox.

## Étape 4 : À propos de quoi est votre addon ?
Maintenant vient la partie amusante !
Qu'est-ce que ton module fait? Pensez à un Identifiant de description (pas d’espaces et des caractères spéciaux, sauf des tirets)
On y va?

## Étape 5 : Créez le dossier pour l'addon
Avec un explorateur de fichiers, allez dans le dossier Scratch Addons sur votre système de fichiers. Trouvez le dossier `addons`.
Maintenant, créez un nouveau dossier nommé avec votre épique ID d'addon.

## Étape 6 : Ajoutez un manifeste d'addon
Le manifeste d'addon dit à Scratch Addons comment votre addon fonctionne. Soyez-sûrs de ne pas faire d'erreurs ici pour éviter les maux de tête.
Dans le dossier que vous venez de créer, créez un fichier `addon.json`.
C'est une base que vous pouvez utiliser pour commencer à coder, soyez sûrs de le changer dans le futur :
```json
{
  "name": "Texte d'espace réservé épique à la place du nom de l'addon",
  "description": "Bonjour tout le monde ! Il serait vraiment judicieux de remplacer ce texte d'espace réservé par une description.",
  "tags": ["communauté"],
  "enabledByDefault": faux
}
```
 
Pour plus d'informations sur ce que vous pouvez déclarer dans le manifeste, consultez [cet article](/docs/reference/addon-manifest/).
 


## Étape 7 : Dites à Scratch Addons quel est l'ID de votre addon
Scratch Addons ne peut pas trouver de nouveaux dossiers par lui-même, vous devez donc ajouter le nom à un fichier spécial.
Allez dans `scratchAddonsFolder/addons/addons.json` et ajoutez l'ID de votre addon à l'array.

## Étape 8 : Bonjour tout le monde
Votre addon ne fait rien pour le moment, c'est donc le bon moment pour vérifier si tout ce que nous avons fait précédemment a fonctionné.
Accédez à `chrome://extensions` et rechargez Scratch Addons en cliquant sur le symbole d'actualisation sur sa carte.
Maintenant, faites un clic droit sur l'icône Scratch Addons et cliquez sur "options".
Vous devriez voir votre addon dans la liste ! Une fois que vous l'avez trouvé, activez-le et définissez tous les paramètres que vous pourriez avoir.

## Étape 9 : La partie fun, coder !
 
*Avant de continuer, assurez-vous de lire l’article wiki lié à l’étape 1.* 

Voici la partie amusante : créez vos propres fichiers JS ou CSS! 
Protip : après avoir modifié votre addon, assurez-vous de rafraîchir l’extension Scratch Addons comme vous l’avez fait à l’étape 8. 

Selon ce que vous voulez que votre addon fasse, vous devriez maintenant vérifier ces pages wiki :
- [Userscripts](/docs/develop/userscripts)
- [Userstyles](/docs/develop/userstyles)

## Étape 10 : Rendez votre addon personnalisable
Si vous le souhaitez, vous pouvez rendre votre addon personnalisable !
Les utilisateurs de votre module complémentaire pourront basculer entre les paramètres, saisir des chiffres et bien plus encore !
Pour commencer, consultez [comment déclarer des paramètres dans le manifeste de l'addon](/docs/reference/addon-manifest/#settings-object).
Ensuite, dirigez-vous vers la [documentation addon.settings](/docs/reference/addon-api/addon.settings) pour savoir comment accéder aux choix de l'utilisateur à partir des scripts utilisateur.
 

## Étape 11 : Avant de publier votre addon
Maintenant que votre addon fonctionne, assurons-nous de pouvoir l'ajouter à la bibliothèque d'addon.
Assurez-vous que le manifeste de votre addon est adapté, [plus d'infos ici](/docs/reference/addon-manifest). Portez une attention particulière au nom, à la description et aux balises de votre addon. Assurez-vous de définir `"enabledByDefault"` sur `false` ou supprimez-le.
Assurez-vous que votre addon ne casse pas les autres addons.
Assurez-vous que votre code est compréhensible ; avoir des commentaires inutiles vaut mieux que pas de commentaires.

## Étape 12 : Envoyez une pull request !
Suivez les étapes de nos [lignes directrices sur les contributions] (https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md). Autrement dit, lancez le repo si vous ne l’avez pas déjà fait, commettez votre nouveau addon et envoyez un PR ! 
Gardez à l’esprit que nous pourrions vous demander d’apporter des changements, cependant, nous accepterons probablement votre addon tant qu’il est minimalement adapté.
