---
title: Preguntas frecuentes
description: Esta página lista preguntas frecuentes sobre la extensión y el proyecto de Scratch Addons
---

Esta página lista preguntas frecuentes sobre la extensión y el proyecto de Scratch Addons

## Preguntas generales

### ¿Qué es Scratch Addons?

Scratch Addons es una extensión de navegador "todo en uno" para el sitio web de Scratch y el editor de proyectos. Provee funciones y temas (llamados addons internamente), ambos para el sitio web de Scratch y el editor de proyectos. La misión de Scratch Addons es combinar todos las extensiones de Scratch, userscripts y userstyles, desarrollados por varios miembros de la comunidad de Scratch, en un solo lugar, mientras dejamos a los usuarios elegir cuáles habilitar.

### ¿Quién creó Scratch Addons?

Scratch Addons es un proyecto de equipo guiado por World_Languages. Puede encontrar la lista de las personas que nos han contribuido en la página de [Créditos](/es/contributors). Aunque que los addons "Herramientas de desarrolador" y "Scratch Messaging" fueron inicialmente creados por griffpatch, él no mantiene la extensión.

### ¿Qué incluye Scratch Addons?

Scratch Addons incluye más de 100 addons, los cuales pueden ser activados o desactivados individualmente. Algunos addons pueden además ser configurados y tienen presets (conjuntos de configuraciones determinadas para un addon), como el tema del modo oscuro para la web. Scratch Addons también incluye un popup, el cual puede ser usado para acceder rápidamente a mensajes, juegos en la nube, y la página de configuración. Scratch Addons está traducido a múltiples idiomas, incluyendo alemán, francés, español y japonés.

### ¿Es esto lo mismo que los addons de TurboWarp?

[TurboWarp](https://turbowarp.org/) tiene algunos de los addons de Scratch Addons, los cuales pueden ser usados en su editor sin instalar Scratch Addons. De todas formas, Scratch Addons incluye además addons para el sitio web de Scratch y el popup. Por lo tanto, sigue siendo útil tener Scratch Addons incluso si programa en TurboWarp solamente.

## Requerimientos del sistema

### ¿Cuáles son los requerimientos del sistema para Scratch Addons?

Scratch Addons se mantiene oficialmente en las versiones de escritorio de [Google Chrome](https://google.com/chrome/) (desde la versión 80) y [Mozilla Firefox](https://www.mozilla.org/es-ES/firefox/) (desde la versión 74), y también debería funcionar en otros navegadores de escritorio que estén basados en estos navegadores. Por favor vea [esta página](../getting-started/installing) para información completa.

### ¿Puedo usar Scratch Addons en un dispositivo móvil?

Para usuarios Android: Sí, pero no es recomendado. Los navegadores principales no permiten instalar Scratch Addons (o cualquier otra extensión), por lo tanto necesita navegadores como [Kiwi](https://kiwibrowser.com/) para hacerlo. El buen funcionamento de la interfaz de usuario de Scratch Addons no está bien comprobado en paltallas táctiles oentornos con un tamaño de pantalla pequeño, entonces puede que algunas de las funciones no se ejecuten como se espera de ellas.

For iOS and iPadOS users: Sadly, it is not. App Store policy does not allow browser implementations to be uploaded, which means all browsers available on that platform are just re-skinned Safari. This causes some problems (see below).

### Can I use Scratch Addons on Safari?

Currently, you cannot.

First, Safari extension store requires all developers to pay an annual fee to list extensions on the store. As Scratch Addons team does not have a source of income, this makes it very hard to maintain the extension. There is also a technical problem with the implementation of browser extensions in Safari which makes some of the core features to be unusable.

### Can I use Scratch Addons on the offline editor?

Scratch Addons cannot be used on the official Scratch application, including the offline editor.

As an alternative, most of the project editor addons are available on [TurboWarp](https://turbowarp.org/) which has a [downloadable app](https://desktop.turbowarp.org/) for Windows, macOS, and Linux. Additionally, on browsers that support Progressive Web Applications (PWA) such as Google Chrome, you can also install the TurboWarp editor as a PWA and use it without an internet connection.

### Are there any incompatible programs?

Some browser extensions and userscripts may interfere with Scratch Addons. If you experience issues, you should try disabling these:

- Scratch 3 Developer Tools: This browser extension is a copy of the Developer tools addon. You should uninstall the Developer Tools browser extension and turn on the addon instead.
- Better3.0: This browser extension can interfere with some addons. Luckily, most of its features are also available as addons.
- Redux DevTools: This can interfere with the internal workings of Scratch Addons. You should disable the Redux DevTools extension if you are not using it.

## Security and privacy

### ¿Es Scratch Addons seguro?

Yes. Scratch Addons should not have any security issues in its most recent version. Scratch Addons is an open source project, so the code has been reviewed by Scratch Addons contributors. Additionally, Chrome Web Store, Add-ons for Firefox, and Microsoft Edge Add-ons review each new version of Scratch Addons before publishing it on their stores.

### ¿Cómo puedo reportar una vulnerabilidad de seguridad?

If you happen to find a security vulnerability, please contact World_Languages privately by emailing `worldxlanguages (at) gmail.com`. If you don't get a response within 48 hours, please [create an issue](https://github.com/ScratchAddons/ScratchAddons/issues/) mentioning that you had sent an email.

You can either [read our security policy](https://github.com/ScratchAddons/ScratchAddons/security/policy) or [check our advisories that we have published](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### ¿Mi cuenta estará segura usando Scratch Addons?

Yes. Features related to your Scratch account are thoroughly reviewed by Scratch Addons contributors to ensure that they will not harm your Scratch account. Scratch Addons keeps your account credentials secure, and it will not modify or delete your projects or assets without your permission. However, you may use the extension without any account-related features if you so choose.

Los addons en Scratch Addons también han sido revisados por múltiples contribuyentes en el repositorio, entonces nadie puede colarnos código malicioso sin que lo sepamos.

We never send any confidential or personally identifying information outside of your browser. See [the extension privacy policy](/docs/privacy/policies/extension) for more information.

## Using Scratch Addons

### How do I enable addons?

To enable addons, first go to the settings by:

- opening the popup and clicking the gear icon on the top-right corner
- going to https://scratch.mit.edu/scratch-addons-extension/settings. Note: you must have the extension installed for this link to work.

Then, find addons you'd like to enable using the sidebar or the search box. To enable an addon, click the switch on the right side of the addon tile.

### ¿Puedo contarle a la gente sobre Scratch Addons en Scratch?

You can't, and please don't. There is a policy that forbids mentioning browser extensions/userscripts [here](https://scratch.mit.edu/discuss/post/2907564/), and violations have resulted in Scratch Team removing posts or muting accounts. You may, however, use different methods to tell your friends about Scratch Addons.

### Creo que Scratch Addons realentiza Scratch. ¿Qué puedo hacer?

You can try disabling addons that you don't need, especially complex features such as the variables tab, debugger, and cat blocks that watch the mouse pointer. Most addons with a performance impact will provide a warning in the extended addon information.

Some specific advices:
- Turn off 60FPS addon. While the addon can increase the maximum speed a project can run, it does not reduce lags. To run such projects faster, use [TurboWarp](https://turbowarp.org/).
- "Variable manager" addon should not be used while the project is running.

### I cannot receive notifications. Why?

First, disable and re-enable the "Scratch Notifier" addon. This can fix some issues.

If the problem continues, then check the operating system's notification settings. You have to allow the browser - such as Google Chrome - to send notifications. 

- Windows: Open Settings, open the "Notifications & actions" category, then find "Change notification settings for individual senders". Read [Microsoft's help article](https://support.microsoft.com/en-us/windows/change-notification-settings-in-windows-8942c744-6198-fe56-4639-34320cf9444e) for more detailed information.
- macOS: Open System Preferences, then open the Notifications section. Select the browser (e.g. Google Chrome) on the left and enable notifications. Read [Apple's help article](https://support.apple.com/en-us/HT204079) for more detailed information.

You should also make sure that "focus assist" (on Windows) or "Do Not Disturb" (on macOS) is disabled.

### How do I watch recordings made with the project video recorder addon?

Due to technical limitations, videos recorded with this addon are in the WebM format. You can view .webm files using your browser (by dragging and dropping the file) or by using a media player that supports it, such as [VLC Media Player](https://www.videolan.org/).

To convert WebM files into MP4 or other formats, you can use a video conversion software that supports WebM, such as [HandBrake](https://handbrake.fr/) or [CloudConvert](https://cloudconvert.com/webm-to-mp4), although we recommend simply viewing these files with a browser or media player. Note that this can take a long time depending on the size of the video.

### ¿Cómo puedes activar los addons easter egg?

To reveal the easter egg addons, do the Konami Code (↑↑↓↓←→←→BA) with your keyboard on the settings page. After that, the easter egg addons will be shown, letting you to activate them.

Some of our easter egg addons are "Fix capitalization of Account Settings" and "Semicolon glitch". Check out [the addons tab](/addons) for a complete list.

## Contributing

### ¿Cómo puedo contribuir a Scratch Addons?

Firstly, we appreciate your interest in contributing to Scratch Addons!

As an open source project, we welcome any kind of contribution. You don't need to ask in advance -- everyone is welcome to contribute! You can contribute in many ways, many of which don't require programming knowledge.

- **Aportar algo de código**

  If you are familiar with JavaScript, HTML, and CSS, you can contribute by fixing bugs, making adjustments, or adding features.

  To incorporate your changes into the main extension, you need to create a pull request. You can do so by forking [the repository](https://github.com/ScratchAddons/ScratchAddons/), creating a branch, making the necessary changes, and then locating the option to create a pull request. We will review it and most likely make some changes before it gets merged.

You can also contribute to other aspects of the organization, such as our website. You can view all of our repositories on [our GitHub organization page](https://github.com/ScratchAddons).

- **Sugerir una idea**

  Have an idea that you think would be a good addition to Scratch Addons? [Let us know!](#i-think-you-missed-a-feature-what-can-i-do)

- **Reportar un bug**

  Found a bug in one of our addons, the settings page, or anything else in our extension? [Send us a bug report](#what-can-i-do-if-i-find-a-problem).

- **Traducir Scratch Addons**

  If you are fluent in another language, you can help translate/localize Scratch Addons to said language. You can start by [joining the localization team].(/docs/localization/joining-the-localization-team).

- **Escribir la documentación**

  Are you familiar with the inner workings of Scratch Addons? If so, you can write the documentation for it. The documentation is located in [our website repo](https://github.com/ScratchAddons/website-v2/tree/master/content/docs). Feel free to open a pull request!

- **Enviar comentarios**

  You can send feedback [on this page](https://scratchaddons.com/feedback). Your feedback may give us a different perspective in the extension development and help us know things needed attention and fix bugs.

- **Dejar una reseña en las tiendas**

  You can leave a review about Scratch Addons on [the Chrome extension page](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco), [the Firefox addon page](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) or [the Microsoft Edge addon page](https://microsoftedge.microsoft.com/addons/detail/scratch-addons/iliepgjnemckemgnledoipfiilhajdjj). This is a great way to help convince others to install the extension!

- **Marcar nuestro repositorio como favorito**

  Basically, the GitHub star is similar to the Scratch star/favorite. You can do this by going to [our repository](https://github.com/ScratchAddons/ScratchAddons) and clicking the "Star" button on the top-right corner.

- **Correr la voz**

You can tell anyone about Scratch Addons, including your friends, relatives, and teachers. We're just asking you [not to do this on the Scratch website](#can-i-tell-people-about-scratch-addons-on-scratch).

### ¿Cómo puedo crear mi propio addon?

Read more about it [here](/docs/develop/getting-started).

### ¿Qué puedo hacer si encuentro un problema?

You can tell us using one of these methods.

- Send it through [our feedback form](https://scratchaddons.com/feedback).
- Create an issue on [the repository](https://github.com/ScratchAddons/ScratchAddons/issues).
- Create a post on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Tell us on [our Discord server](https://discord.gg/R5NBqwMjNc).

### Creo que les falta una función. ¿Qué puedo hacer?

If you want to suggest an addon for the extension or have some other kind of good idea, tell us with [one of these methods](#what-can-i-do-if-i-find-a-problem).

### Where can I discuss Scratch Addons?

You can do it on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) or [our Discord server](https://discord.gg/R5NBqwMjNc). There, you can ask questions and engage with the Scratch Addons community.

## Technical

### ¿Qué es un "addon", exactamente?

An addon is similar to an extension or a userscript, but they use special APIs provided by the Scratch Addons extension. These APIs allow addons to run scripts on a Scratch page (userscripts), run scripts on the background (persistent scripts), or apply styles to the Scratch website (userstyles).

Userscripts can use the `addon.*` JavaScript APIs, which allow them to obtain Scratch-related information (for example, the currently logged in user) and use extension APIs (like sending notifications).

### Si todo es un addon, ¿qué hace Scratch Addons?

By itself, Scratch Addons is just an addon loader. Its main tasks are to:

- Permitir a los usuarios habilitar, deshabilitar y configurar addons.
- Ejecutar addons y proveerles APIs.
- Provide useful data to addons (for example, the addon.auth API).
- Pollute prototypes for use by addon userscripts.
- Proveer maneras para acceder y modificar el estado Redux.
- Evitar que los addons interfieran con los demás.
- Evitar la misma función por addons duplicados.

## Other 

### How can I add/remove myself to/from the contributors page?

If you want your name to be on the page, please read and follow the instructions of [this issue](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}).

If you don’t want your name to be on the page, please tell us by creating an issue on our contributors repository, or by other means of contact. We’re sorry for the inconvenience.

### ¡Tengo más preguntas!

If you have more questions that need answers, you can create a post on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) or send a message [on our Discord server](https://discord.gg/R5NBqwMjNc). We will answer as best we can!
