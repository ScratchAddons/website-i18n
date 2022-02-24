---
title: Namestitev
---

## Iz trgovin z razširitvami

Scratch Addons je na voljo v Spletni trgovini Chrome in v Dodatkih za Firefox.

- Spletna trgovina Chrome (za Google Chrome, Opera, Brave, Vivaldi, Microsoft Edge (>79), in druge brskalnike, narejene na osnovi Chromium)  
  https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco  
- Dodatki za Firefox (za brskalnik Mozilla Firefox)  
  https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/  


## Z izvirno kodo

### About GitHub releases

[The releases page](https://github.com/ScratchAddons/ScratchAddons/releases) contains the code and installation files for all development builds of Scratch Addons, as well as the mirror of the store builds.

### Podvajanje kode

This is the recommended way to install Scratch Addons for development purposes. This assumes you have Git installed.

To download the repository, simply clone `https://github.com/ScratchAddons/ScratchAddons.git`.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
To update Scratch Addons, first `cd` into its folder, and then run the following commands.

```sh
$ git fetch
$ git pull
```

This will update Scratch Addons and get it ready for code editing. Note that you will need to see the finish updating section [here](#install-on-google-chrome) if you are using Google Chrome.


### Prenos datoteke .zip

If you don't have Git installed, you can try this method instead. Note that you will need to manually repeat this process every time you want to update Scratch Addons.

1. Go to the [repository](https://github.com/ScratchAddons/ScratchAddons) and find the download code button.

   ![Download code button screenshot](/assets/img/docs/download-code-button.png)

2. Click it and select "Download ZIP".

   ![Download ZIP button screenshot](/assets/img/docs/download-zipball-button.png)

3. Extract the archive into a folder.

### Namestitev v brskalniku Google Chrome

1. V naslovno vrstico vnesite `chrome://extensions`, da odprete stran za upravljanje razširitev.

2. Kliknite stikalo `Način za razvijalce`, da vključite način za razvijalce. To omogoča nameščanje razširitev iz map ali datotek.

   ![Posnetek zaslona orodne vrstice na strani z razširitvami](/assets/img/docs/developer-mode-toggle.png)

3. Prikazati bi se moral gumb `Naloži razpakirano`. Ko ga kliknite, lahko izberete mapo.

   ![Posnetek zaslona z gumbom Naloži razpakirano](/assets/img/docs/load-unpacked-button.png)

4. Select the extracted folder.
5. Razširitev bi zdaj morala biti naložena.

To finish updating (assuming you followed the updating steps [here](#cloning-the-repository)), click the `Update` button:

![Update button screenshot](/assets/img/docs/update-button.png)


### Namestitev v brskalniku Mozilla Firefox

1. V naslovno vrstico vnesite `about:debugging`, da odprete stran za razhroščevanje.

2. Click `This Firefox` on the left-hand menu.

   ![Posnetek zaslona menija na levi strani](/assets/img/docs/left-hand-menu.png)

4. Kliknite `Naloži začasen dodatek...`.

   ![Load Temporary Add-on button screenshot](/assets/img/docs/load-addon.png)

6. Select the manifest.json file inside the extracted folder.
7. The extension should now be loaded.

Note: Firefox temporary add-ons are actually temporary. Restarting Firefox will remove them, so if you want to use the development version of Scratch Addons all the time, it is recommended that you use a Chromium-based browser like Google Chrome.

