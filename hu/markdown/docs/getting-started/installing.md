---
title: Telepítés
---

## Bővítményáruházakból

A Scratch Addons elérhető a Chrome Webáruházban és a Firefox kiegészítői között is.

- Chrome Webáruház (Google Chromehoz, Operához, Bravehez, Vivaldihoz, >79 Microsoft Edgehez és egyéb Chromium-alapú webböngészőkhöz)
  https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco

- Firefox Kiegészítők (Mozilla Firefoxhoz)
  https://addons.mozilla.org/hu/firefox/addon/scratch-messaging-extension/

- Microsoft Edge Kiegészítők (Microsoft Edge >79)
  https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj

## From source

### A GitHub megjelentetésekről

[A kiadások oldala](https://github.com/ScratchAddons/ScratchAddons/releases) tartalmazza a kódot és a letöltési fájlokat is a Scratch Addons minden fejlesztői szerkezetéhez ugyanúgy, mint az áruházi szerkezetek másolatát is.

### A repository másolása

Ez az ajánlott módja a Scratch Addons letöltésének fejlesztői célokhoz. Ez persze felételezi, hogy már letöltötte a Gitet.

A repository letöltéséhez szimplán klónozza le a `https://github.com/ScratchAddons/ScratchAddons.git` -et.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
A Scratch Addons frissítéséhez először `cd`-zen bele a mappájába, majd futtassa a következő parancsot:

```sh
$ git fetch
$ git pull
```

Ez frissíteni fogja a Scratch Addons-t, és előkészíti a kódja másításához. Jegyezze meg, hogy látnia kell a frissítés befejezése részleget [itt](#install-on-google-chrome), ha Google Chrome-ot használ.


### A zipball letöltése

If you don't have Git installed, you can try this method instead. Note that you will need to manually repeat this process every time you want to update Scratch Addons.

1. Go to the [repository](https://github.com/ScratchAddons/ScratchAddons) and find the download code button.

   ![Download code button screenshot](/assets/img/docs/download-code-button.png)

2. Click it and select "Download ZIP".

   ![Download ZIP button screenshot](/assets/img/docs/download-zipball-button.png)

3. Extract the archive into a folder.

### Installing on Google Chrome

1. Type `chrome://extensions` into your address bar to open the Extension Management page.

2. Click the toggle next to `Developer mode` to turn on the Developer Mode. This allows you to install extensions from a folder or file.

   ![Extension Managment top bar screenshot](/assets/img/docs/developer-mode-toggle.png)

3. You should see the `Load unpacked` button appear. Clicking it will allow you to select a folder to upload.

   ![Load unpacked button screenshot](/assets/img/docs/load-unpacked-button.png)

4. Select the extracted folder.
5. The extension should now be loaded.

To finish updating (assuming you followed the updating steps [here](#cloning-the-repository)), click the `Update` button:

![Update button screenshot](/assets/img/docs/update-button.png)


### Installing on Mozilla Firefox

1. Type `about:debugging` into your address bar to open the debugging page.

2. Click `This Firefox` on the left-hand menu.

   ![Left-hand menu screenshot](/assets/img/docs/left-hand-menu.png)

4. Click `Load Temporary Add-on...`.

   ![Load Temporary Add-on button screenshot](/assets/img/docs/load-addon.png)

6. Select the manifest.json file inside the extracted folder.
7. The extension should now be loaded.

Note: Firefox temporary add-ons are actually temporary. Restarting Firefox will remove them, so if you want to use the development version of Scratch Addons all the time, it is recommended that you use a Chromium-based browser like Google Chrome.

