---
title: Installation
---

## Depuis le magasin d'extension

Srcratch Addons est disponible dans ces boutiques.

| Boutique | Installer | Navigateurs pris en charge | Prérequis système |
| - | - | - | - |
| Boutique Chrome | [![Installer pour Chrome Web Store](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 80+<br />Microsoft Edge 80+<br />Opera 67+<br />Brave 1.3+<br />Vivaldi 2.11+<br />*Chromium 80+* | Windows 7+<br />OS X / MacOS 10.11+<br />Chromebooks vieux d'au plus ~6 ans
| Add-ons pour Firefox | [![Installer for Add-ons pour Firefox](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 86+ | Windows 7+<br />OS X / MacOS 10.12+
| Microsoft Edge Add-ons | [![Install for Microsoft Edge Addons](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 80+ | Windows 7+<br />OS X / MacOS 10.11+

## Depuis la source

### About GitHub releases

[La page des versions](https://github.com/ScratchAddons/ScratchAddons/releases) contient le code et les fichiers d’installation pour toutes les versions de développement de Scratch Addons, ainsi que le miroir des versions du magasin.

### Clonage du répertoire

Ceci est la manière recommandée d'installer Scratch Addons pour des fins de développement. Ceci est basé sur le fait que vous avez installez Git.

Pour télécharger le référentiel, clonez simplement `https://github.com/ScratchAddons/ScratchAddons.git`.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
Pour mettre à jour Scratch Addons, commencez par `cd` dans son dossier, puis exécutez les commandes suivantes.

```sh
$ git fetch
$ git pull
```

Cela mettra à jour Scratch Addons et le préparera pour l’édition de code. Notez que vous aurez besoin de voir la section de mise à jour de finition [ici](#install-on-google-chrome) si vous utilisez Google Chrome.


### Téléchargement de la zipball

Si Git n’est pas installé, vous pouvez essayer cette méthode à la place. Notez que vous devrez répéter ce processus manuellement chaque fois que vous souhaitez mettre à jour Scratch Addons.

1. Allez dans le [repository] (https://github.com/ScratchAddons/ScratchAddons) et trouvez le bouton de téléchargement de code.

   ![Capture d’écran du bouton Télécharger le code](/assets/img/docs/download-code-button.png)

2. Cliquez et selectionnez ”Télécharger le ZIP”

   ![Télécharger la capture d’écran du bouton ZIP](/assets/img/docs/download-zipball-button.png)

3. Extraire l’archive dans un dossier.

### Installation sur Google Chrome ou Microsoft Edge

1. Tapez `chrome://extensions` dans votre barre d'adresse pour ouvrir la page de gestion des extensions.

2. Cliquez sur le bouton à bascule à côté du `mode développeur` pour activer le mode développeur, ce qui vous permet d’installer des extensions à partir d’un dossier ou d’un fichier.

   ![Capture d’écran de la barre supérieure de gestion des extensions](/assets/img/docs/developer-mode-toggle.png)

3. Le bouton  `Load unpacked` devrait s’afficher. Cliquez dessus pour sélectionner un dossier à télécharger.

   ![Chargement de la capture d’écran du bouton décompressé](/assets/img/docs/load-unpacked-button.png)

4. Sélectionnez le fichier extrait.
5. L'extension devrait maintenant être chargée.

Pour terminer la mise à jour (en supposant que vous ayez suivi les étapes de mise à jour [ici](#cloning-the-repository)), cliquez sur le bouton `Mettre à jour`:

![Capture d’écran du bouton de mise à jour](/assets/img/docs/update-button.png)


### Installation sur Mozilla Firefox

1. Tapez `about:debugging` dans votre barre d'adresse pour ouvrir la page de débogage.

2. Cliquez sur `This Firefox` dans le menu de gauche.

   ![Capture d’écran du menu de gauche](/assets/img/docs/left-hand-menu.png)

4. Cliquez sur `Charger le module complémentaire temporaire...`.

   ![Chargement de la capture d’écran du bouton d’ajout temporaire](/assets/img/docs/load-addon.png)

6. Sélectionnez le fichier manifest.json dans le dossier extrait.
7. L'extension devrait maintenant être chargée.

Remarque : les modules complémentaires temporaires de Firefox sont en fait temporaires. Le redémarrage de Firefox les supprimera, donc si vous souhaitez utiliser la version de développement de Scratch Addons tout le temps, il est recommandé d'utiliser un navigateur basé sur Chromium comme Google Chrome.
 

