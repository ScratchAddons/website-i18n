---
title: Instal·lació
---

## De botigues d'extensions

Scratch Addons està disponible tant al Chrome Web Store com a Complements per al Firefox.

- Chrome Web Store (per a Google Chrome, Opera, Brave, Vivaldi, Microsoft Edge >79 i altres exploradors basats en el codi de Chromium)
  https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco

- Complements per al Firefox (per a Mozilla Firefox)
  https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/

- Microsoft Edge Add-ons (per a Microsoft Edge > 79)
  https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj

## Desde la font

### Sobre les versions de GitHub

[La pàgina de versions](https://github.com/ScratchAddons/ScratchAddons/releases) conté el codi i els fitxers d'instal·lació per totes les compilacions del desenvolupament del Scratch Addons, així com el portal de les compilacions de les botigues de complements.

### Clonació del repositori

Aquesta és la forma recomanada d'instal·lar Scratch Addons amb fins de desenvolupament. Això suposant que tens Git instal·lat.

Per baixar el repositori, només has de clonar `https://github.com/ScratchAddons/ScratchAddons.git`.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
Per actualitzar els complements de Scratch, primer `cd` a la seva carpeta i, a continuació, executa les ordres següents.

```sh
$ git fetch
$ git pull
```

Això actualitzarà el Scratch Addons i el prepararà per a l'edició de codi. Tingues en compte que haurás de veure la secció d'acabament d'actualització [aquí](#install-on-google-chrome) si fas servir el Google Chrome.


### Descàrrega del zipball

Si no tens el Git instal·lat, pots provar aquest altre mètode. Tingues en compte que haurás de repetir aquest procediment manualment cada vegada que vulguis actualitzar el Scratch Addons.

1. Vés al [repositori](https://github.com/ScratchAddons/ScratchAddons) i cerca el botó de descàrrega del codi.

   ![Descarrega la captura de pantalla del botó del codi](/assets/img/docs/download-code-button.png)

2. Fes-hi clic i selecciona "Download ZIP.

   ![Descarrega la captura de pantalla del botó ZIP](/assets/img/docs/download-zipball-button.png)

3. Extreu l'arxiu a una carpeta.

### Instal·lació a Google Chrome

1. Escriu `chrome://extensions` a la barra d'adreces per obrir la pàgina de gestió d'extensions.

2. Fes clic al lliscador del costat de `Mode de desenvolupador` per activar el mode de desenvolupador. Això permet instal·lar extensions des d'una carpeta o arxiu.

   ![Captura de pantalla de la barra superior del gestor d'extensions](/assets/img/docs/developer-mode-toggle.png)

3. Hauríes de veure que apareix el botó `Carrega una extensió desempaquetada`. Si fas clic, podrás seleccionar una carpeta per carregar.

   ![Captura de pantalla del botó de carregar una extensió desempaquetada](/assets/img/docs/load-unpacked-button.png)

4. Selecciona la carpeta extreta.
5. Ara s'hauria de carregar l'extensió.

Per acabar d'actualitzar (suposant que s'han seguit els passos d'actualització d' [aquí](#cloning-the-repository)), fes clic al botó de `Actualitza`:

![Captura de pantalla del botó d'actualitzar](/assets/img/docs/update-button.png)


### Instal·lació a Mozilla Firefox

1. Escriu `about:debugging` a la barra d'adreces per obrir la pàgina de depuració.

2. Feu clic a `Aquest Firefox` al menú de l'esquerra.

   ![Captura de pantalla del menú de l'esquerra](/assets/img/docs/left-hand-menu.png)

4. Fes clic a `Carrega un complement temporal...`.

   ![Captura de pantalla del botó de Carrega un complement temporal](/assets/img/docs/load-addon.png)

6. Selecciona el fitxer manifest.json dins de la carpeta extreta.
7. Ara s'hauria de carregar l'extensió.

Nota: Els complements temporals del Firefox són realment temporals. Si reinicieu Firefox, es suprimiràn, de manera que si vols utilitzar la versió de desenvolupament de Scratch Addons tot el que vulgis, et recomanem que utilitzis un navegador basat en Chromium com el Google Chrome.

