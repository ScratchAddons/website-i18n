---
title: Creació d'un Addon
---
Programari necessari: editor de text, Chrome.
Si és possible, desactiva l'extensió Scratch Addons que has baixat de la botiga abans de continuar per evitar problemes.

## Pas 1: llegeix les [fons bàsiques dels complements](/docs/develop/getting-started/addon-basics/)
Assegura't de llegir aquest article per familiaritzar-te amb la terminologia.

## Step 2: Fork/clone the [repo](https://github.com/ScratchAddons/ScratchAddons)
Follow [these instructions](/docs/getting-started/installing/#from-source) to download the source code locally.

## Pas 3: Carrega l'extensió al Chrome
*Note: Chrome is recommended for working on addons. Nevertheless, addons are expected to work on Firefox and Edge.*  
Now that you have the extension in your filesystem, go to `chrome://extensions` and toggle "developer mode".  
Click "load unpacked", then select the folder where Scratch Addons is located. If you're having issues with this, make sure to be selecting the folder where `manifest.json` is located.  
That's it, you loaded the extension! It should look similar to this:  
![image](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)  
Note: you can safely ignore it says "errors". That's just a warning for an unrecognized manifest key that's required by Firefox.

## Pas 4: De què tracta el teu addon?
Ara ve la part divertida!
Què farà el teu complement? Pensa en un ID d'addon autodescriptiu (sense espais ni caràcters especials, excepte guions).
Ho tens llest?

## Pas 5: Crea la carpeta per l'addon
Amb un explorador de arxius, vés a la carpeta on es troba Scratch Addons al vostre sistema de fitxers. Troba la carpeta `addons`.
A continuació, crea una carpeta nova amb el teu èpic ID de addon com a nom.

## Pas 6: Afegeix un manifest de addon
El manifest del complement indica al Scratch Addons com funciona el teu addon. Assegura't de fer-ho bé per evitar mals de cap.
Dins de la carpeta que acabes de crear, crea un fitxer `addon.json`.
Aquesta és una base que pots utilitzar per començar a programar, assegura't canviar-la en el futur:
```json
{
  "name": "Espai en blanc èpic per posar el nom del Espai en blanc èpic per posar el nom del complement",
  "description": "Hola món! Seria molt intel·ligent substituir aquest espai en blanc per una descripció.",
  "tags": ["community"],
  "enabledByDefault": false
}
```
Per obtenir més informació sobre què pots declarar al manifest, consulta [aquest article](/docs/reference/addon-manifest/).


## Pas 7: Indica a Scratch Addons quin és l'identificador del vostre addon
Scratch Addons no pot trobar carpetes noves per si sól, de manera que has d'afegir el nom a un fitxer especial.
Vés a `scratchAddonsFolder/addons/addons.json` i afegeix l'ID del vostre addon a l'array.

## Pas 8: Hola món
El teu addon no fa res de moment, així que és hora de comprovar si tot el que hem fet anteriorment ha funcionat.
Vés a `chrome://extensions` i torna a carregar Scratch Addons fent clic al símbol d'actualització de la targeta.
Ara, fes clic amb el botó dret a la icona del Scratch Addons i fes clic a "Opcions".
Hauríes de veure el vostre complement a la llista! Un cop el trobis, activa'l i configura qualsevol configuració que pugui tenir.

## Pas 9: La part divertida, el codi!
*Abans de continuar, assegura't de llegir l'article de la wiki enllaçat al pas 1.* 

Aquí ve la part divertida: crea els teus propis fitxers JS o CSS!
Consell de pro: després de fer qualsevol canvi al vostre complement, assegura't d'actualitzar l'extensió de Scratch Addons com vas fer al pas 8.

Depenent del que vulguis que faci el teu addon, ara hauríes de comprovar aquestes pàgines de la wiki:
- [Userscripts](/docs/develop/addon-types/userscripts)
- [Userstyles](/docs/develop/addon-types/userstyles)

## Pas 10: Fes que el teu addon sigui personalitzable
Si vols, pots personalitzar el teu addon!
Els usuaris del teu addon podran canviar la configuració, introduir números i molt més!
Per començar, veu [com declarar la configuració al manifest del addon](/docs/reference/addon-manifest/#settings-object).
A continuació, vés a la [addon.settings documentation](/docs/reference/addon-api/addon.settings) per saber com accedir a les opcions d'usuari des dels scripts d'usuari.

## Pas 11: Abans de publicar el teu addon
Ara que el teu addon funciona, assegurem-nos que el podem afegir a la biblioteca d'addons.
Assegura't que el manifest del teu addon sigui adequat, [més informació aquí](/docs/reference/addon-manifest). Mantingues molta atenció al nom, la descripció i les etiquetes del teu addon Assegura't d'establir `"enabledByDefault"` com a `false` o suprimiu-lo.
Assegura't que el teu addon no trenqui altres addons.
Assegura't que el teu codi sigui comprensible; tenir comentaris innecessaris és millor que no fer comentaris.

## Pas 12: Envian's una sol·licitud!
Follow the steps on our [contributing guidelines](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md). Simply put, fork the repo if you haven't already, commit your new addon and send a PR!  
Keep in mind we might request you to make some changes, however, we will probably accept your addon as long as it's minimally suitable.
