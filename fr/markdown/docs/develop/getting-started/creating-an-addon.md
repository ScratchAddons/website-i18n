---
title: Créer un Addon
---
Logiciels requirent : éditeur de texte, Chrome.
Si possible, désactivez l'extension Scratch Addons que vous avez téléchargée de la boutique avant de procéder pour éviter des problèmes.

## Étape 1 : Lisez les [bases des addons](/docs/develop/getting-started/addon-basics/)
Assurez-vous de lire cet article pour vous familiariser avec la terminologie.

## Étape 2 : Fork/clonez le repo
Ou téléchargez en ZIP, si vous préférez. En d'autres termes, téléchargez juste le code source localement.

## Étape 3 : Chargez l'extension dans Chrome
*Note : Chrome est recommandé pour travailler sur des addons. Néanmoins, les addons devraient fonctionner sur Firefox et Edge.*
Maintenant que vous avez l'extension dans votre système de fichiers, allez sur `chrome://extensions` et activer le "mode développeur".
Cliquez sur "charger l'extension non empaquetée", puis sélectionnez le fichier de l'extension Scratch Addons. Si vous rencontrez des problèmes à ce niveau, soyez sûrs de sélectionner le dossier dans lequel le fichier `manifest.json` se trouve.
C'est tout, vous avez chargé l'extension ! Ça devrait ressembler à cela : ![image](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)
Note : il n'y a pas de risques à l'ignorer si il y a marqué "erreurs". C'est juste un avertissement pour une clé manifeste non-reconnue requise par Firefox.

## Étape 4 : À propos de quoi est votre addon ?
Maintenant vient la partie drôle !
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
  "name": "Epic placeholder text in place of addon name",
  "description": "Hello World! It would be really smart to replace this placeholder text with a description.",
  "tags": ["community"],
  "enabledByDefault": false
}
```
For more information on what you can declare in the manifest, check [this article](/docs/reference/addon-manifest/).


## Step 7: Tell Scratch Addons what your addon's ID is
Scratch Addons can't find new folders by itself, so you have to add the name to a special file.  
Go to `scratchAddonsFolder/addons/addons.json` and add the ID of your addon to the array.

## Step 8: Hello world
Your addon does nothing at the moment, so it's a good time to check if everything we made previously worked.  
Go to `chrome://extensions` and reload Scratch Addons by clicking the refresh symbol on its card.  
Now, right-click the Scratch Addons icon, and click "options".  
You should see your addon on the list! Once you find it, enable it, and set any settings that you may have.

## Step 9: The fun part, code!
*Before proceeding, make sure you read the wiki article linked in step 1.*  

Here comes the fun part: create your own JS or CSS files!  
Protip: after making any change to your addon, make sure to refresh the Scratch Addons extension like you did in step 8.  

Depending on what you want your addon to do, you should now check these wiki pages:
- [Userscripts](/docs/develop/addon-types/userscripts)
- [Styles utilisateur](/docs/develop/addon-types/userstyles)

## Step 10: Make your addon customizable
If you want, you can make your addon customizable!  
Users of your addon will be able to toggle settings, enter numbers, and more!  
To get started, see [how to declare settings in the addon manifest](/docs/reference/addon-manifest/#settings-object).  
Then, head to the [addon.settings documentation](/docs/reference/addon-api/addon.settings) to learn how to access user choices from userscripts.

## Step 11: Before publishing your addon
Now that your addon works, let's make sure we can add it to the addon library.  
Make sure your addon's manifest is suitable, [more info here](/docs/reference/addon-manifest). Keep close attention to the name, description and tags of your addon. Make sure to set `"enabledByDefault"` to `false` or remove it.  
Make sure your addon doesn't break other addons.  
Make sure your code is understandable; having unnecessary comments is better than no comments.

## Step 12: Send a pull request!
Follow the steps on our [contributing guidelines](https://github.com/ScratchAddons/ScratchAddons/blob/master/CONTRIBUTING.md). Simply put, fork the repo if you haven't already, commit your new addon and send a PR!  
Keep in mind we might request you to make some changes, however, we will probably accept your addon as long as it's minimally suitable.
