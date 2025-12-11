---
title: Userstyle
description: Gli userstyle sono regole CSS che vengono applicate alle pagine di Scratch. Possono applicare stili alla attuale IU di Scratch oppure ad elementi che sono stati aggiunti alla pagina da un addon.
---

Gli userstyle sono regole CSS che vengono applicate alle pagine di Scratch. Possono applicare stili alla attuale IU di Scratch oppure ad elementi che sono stati aggiunti alla pagina da un addon.


## Dichiarazione di userstyle nel file manifest dell'addon

{{< admonition warning >}}
Per avere effetto, **alcune modifiche richiedono di ricaricare l'estensione** da `chrome://extensions`. Ad esempio è necessario quando si modifica il file manifest dell'addon.

Quando cambi il sorgente di un file JavaScript o CSS che esiste già non è necessario ricaricare l'estensione. In questi casi è sufficiente ricaricare la pagina.
{{< /admonition >}}

Gli userstyle sono dichiarati dentro un array "userstyles", in modo simile a quanto accade per gli userscript.

Ogni element dell'array deve avere le seguenti proprietà:
- `"url"`: l'URL relativo di un file CSS.
- `"matches"`: la lista di pagine Scratch a cui lo userstyle verrà applicato. Per ulteriori informazioni vai a [matches](/docs/reference/addon-manifest/#matches).
- `if`: una lista di condizioni che possono cambiare quando lo userstyle è in uso o no. Per ulteriori informazioni vai a [userstyle.if](https://scratchaddons.com/docs/reference/addon-manifest/#if).

Esempio di manifest:
```json
{
  "name": "Scratch Messaging",
  "description": "Provides easy reading and replying to your Scratch messages.",
  "userstyles": [
    {
      "url": "styles.css",
      "matches": ["projects", "https://scratch.mit.edu/", "profiles"]
    },
    {
      "url": "resize.css",
      "matches": ["projects"],
      "if": {
        "settings": {
          "resize": true
        }
      }
    },
  ],
  "settings": [
    {
      "name": "Resize messages",
      "id": "resize",
      "type": "boolean",
      "default": false
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```


## Abilitare e disabilitare dinamicamente gli userstyle dopo che la pagina è stata caricata

Solitamente non è necessario usare uno userscript JavaScript per abilitare o disabilitare dinamicamente uno userstyle della pagina, in risposta alle modifiche delle impostazioni effettuate dall'utente.

- Includendo `dynamicEnable: true` nel file manifest dell'addon si permetterà all'estensione di aggiungere dinamicamente lo userstyle alla pagina anche se l'addon è stato abilitato (per la prima volta) solo dopo aver caricato la pagina.
- Includendo `dynamicEnable: true` nel file manifest dell'addon si permetterà all'estensione di rimouvere o riaggiungere dinamicamente lo userstyle alla pagina se l'addon è stato abilitato o disabilitato, senza richiedere che la pagina venga ricaricata.
- Includendo `updateUserstylesOnSettingsChange: true` nel file manifest dell'addon verranoo rivalutate le condizioni "if" che dipendono dalle impostazioni dell'utente senza richidere che la pagina venga ricaricata. L'estensione rimuovere o aggiornerà lo userstyles in accordo a quanto richiesto dall'utente.


## Accedere le impostazioni dell'addon dal CSS

Gli userstyle possono ottenere facilmente impostazioni come colori e valori numerici attraverso le variabili CSS. Possono anche accedere alle impostazioni degli altri addon abilitati.

Le variabili CSS seguono sempre il formato `--addonId-settingId`. Gli ID delle impostazioni vengono sempre convertiti dal formato kebab-case al formato camelCase.

Questa variabili CSS sono sempre disponibili per tutti gli addon abilitati e non è necessario usare proprietà del file manifest per renderle visibili agli altri addon. Sono anche sincronizzate con le impostazioni utente senza che sia necessario ricaricare la pagina. 

```css
.sa-progress-bar {
  /* Impostazioni colore */
  background-color: var(--progressBar-bgColor);

  /* Impostazioni colore con fallback */
  border-color: var(--editorDarkMode-border, #fc7c24);
  /* Se l'addon editor-dark-mode è disabilitato, verrà usato il fallback  */

  /* Impostazioni numeriche */
  height: calc(1px * var(--progressBar-height));
}
```


## Variabili CSS personalizzate

Se uno userstyle deve scegliere tra uno di due valori basandosi su un colore dello sfondo (o il contrasto del desto) o un'impostazione di un addon, non è necessario usare JavaScript. Queste condizioni, tra le altre, possono essere dichiarate nel manifesto dell'addon usando [customCssVariables](/docs/reference/addon-manifest/#customcssvariables) e lo userstyle può semplicemente fare riferimento a quella variabile CSS.


## Applying styles based on the editor mode

The extension automatically toggles a class name on the `<html>` element when the user enters or exits the project editor.

Ad esempio, dando un diverso stile agli elementi `<input>` fuori e dentro l'editor:
```css
.sa-editor input {
  /* Only applies if `addon.tab.editorMode` is `editor` or `fullscreen` */
}

:root:not(.sa-editor) input {
  /* Only applies if `addon.tab.editorMode` is NOT `editor` nor `fullscreen` */
}
```

Similarly, the `.sa-fullscreen` class is added to the `<html>` element when the project is in full screen mode:
```css
.sa-fullscreen [class*="green-flag_green-flag_"] {
  /* Only applies if `addon.tab.editorMode` is `fullscreen` */
}

:root:not(.sa-fullscreen) [class*="green-flag_green-flag_"] {
  /* Only applies if `addon.tab.editorMode` is NOT `fullscreen` */
}
```
