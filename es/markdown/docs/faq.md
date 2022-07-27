---
title: Preguntas frecuentes
description: Esta página lista preguntas frecuentes sobre la extensión y el proyecto de Scratch Addons
---

Esta página lista preguntas frecuentes sobre la extensión y el proyecto de Scratch Addons

### ¿Qué es Scratch Addons?

Scratch Addons es una extensión de navegador "todo en uno" para el sitio web de Scratch y el editor de proyectos. Provee funciones y temas (llamados addons internamente), ambos para el sitio web de Scratch y el editor de proyectos. La misión de Scratch Addons es combinar todos las extensiones de Scratch, userscripts y userstyles, desarrollados por varios miembros de la comunidad de Scratch, en un solo lugar, mientras dejamos a los usuarios elegir cuáles habilitar.

### ¿Qué es un "addon", exactamente?

Un addon es similar a una extensión o un userscript, pero usan APIs especiales proporcionadas por la extensión de Scratch Addons. Estas APIs permiten a los addons ejecutar código en una página de Scratch (userscripts) o aplicar estilos al sitio web de Scratch (userstyles)

Los userscripts pueden usar los APIs de JavaScript de `addon.*`, el cual les permite obtener información relacionada con Scratch (por ejemplo, obtener el usuario actualmente en sesión) y usar APIs de extensión (como enviar notificaciones).

### Si todo es un addon, ¿qué hace Scratch Addons?

Por sí mismo, Scratch Addons es un cargador de addons. Sus tareas principales son:

- Permitir a los usuarios habilitar, deshabilitar y configurar addons.
- Ejecutar addons y proveerles APIs.
- Proporcionar un estado global a los addons (por ejemplo, el addon.auth).
- Pollute prototypes for use by addon userscripts.
- Proveer maneras para acceder y modificar el estado Redux.
- Evitar que los addons interfieran con los demás.
- Evitar la misma función por addons duplicados.

### ¿Es Scratch Addons seguro?

Yes. Scratch Addons should not have any security issues in its most recent version. Scratch Addons is an open source project, so the code is constantly being verified by Scratch Addons contributors, as well as by reviewers from the Chrome Web Store and Add-ons for Firefox.

### ¿Cómo puedo reportar una vulnerabilidad de seguridad?

Si encontraras una vulneravilidad de seguridad por favor contacte a World_Languages de forma privada enviando un email a `worldxlanguages (arroba) gmail.com`. Si no recive una respuesta en 48 horas, por favor cree una propuesta [aquí](https://github.com/ScratchAddons/ScratchAddons/issues/) mencionando que enviaste un email.

You can either [read our security policy](https://github.com/ScratchAddons/ScratchAddons/security/policy), or [check our advisories that we have published](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### ¿Mi cuenta estará segura usando Scratch Addons?

Scratch Addons no usa los credenciales de su cuenta para funcionar esencialmente. En realidad, puede cerrar sesión en Scratch, y Scratch Addons seguirá funcionando. Scratch Addons solo hará pedidos basados en las cookies que tiene, las cuales son requeridas para cada padido hecho por el navegador, entonces algunos addons como Scratch Messaging no funcionarán cuando no inició sesión, pero no afectará otras partes de la extensión.

Los addons en Scratch Addons también han sido revisados por múltiples contribuyentes en el repositorio, entonces nadie puede colarnos código malicioso sin que lo sepamos.

Nunca enviamos información de su cuenta de Scratch o ajustes de la extensión fuera de su navegador. Vea la [política de privacidad de la extensión](/docs/privacy/policies/extension) para más información.

### ¿Puedo contarle a la gente sobre Scratch Addons en Scratch?

Puede, y por favor no lo haga. Hay una política que prohíbe mencionar extensiones de navegador o userscripts [aquí](https://scratch.mit.edu/discuss/post/2907564/). Podría, de cualquier forma, usar diferentes métodos para decirle a tus amigos sobre Scratch Addons.

### ¿Cómo puedo contribuir a Scratch Addons?

Primero que nada, gracias por interesarse en contribuir a Scratch Addons. Apreciamos su interés y sus contribuciones más tarde.

Como un proyecto de código abierto, aceptamos cualquier tipo de contribución. Ni siquiera necesita preguntarnos o tener algún rango. Todos son bienvenidos. ¡Incluso hay una posibilidad de que no se haya dado cuenta de que ya ha contribuido a este proyecto!

De cualquier manera, de vuelta al punto. Puede contribuir de muchas formas, y algunas de ellas son realmente fáciles.

- **Aportar algo de código**

  Si puede programar en JavaScript, HTML5 y CSS, puede contribuir programando. Puede arreglar bugs, abordar algunas solicitudes o crear su propio addon.

  Después de eso, necesita crear una pull request. Puede hacerlo bifurcando [el repositorio](https://github.com/ScratchAddons/ScratchAddons/), hacer los cambios necesarios  crear una pull request. Si es considerada factible, la fusionaremos.

  We're also open for contributions of other aspects than the extension. You can view our repositories on [our GitHub organization page](https://github.com/ScratchAddons) and help us build them.

- **Sugerir una idea**

  ¿Tiene algo que piensa que sería una buena adición a Scratch Addons? [¡Díganoslo!](#i-think-you-missed-a-feature-what-can-i-do)

- **Reportar un bug**

  ¿Encontró un bug en uno de nuestros addons, la página de configuración, o algo más en nuestra extensión? [Envíenos un reporte de bug](#what-can-i-do-if-i-find-a-problem).

- **Traducir Scratch Addons**

  If you can speak another language than English fluently, you can help translate/localize Scratch Addons to your language. You can start from [here](/docs/localization/joining-the-localization-team).

- **Escribir la documentación**

  Are you familiar with Scratch Addons? If so, you can write the documentation for it. The documentation can include how to use it, or how it works. Please contact us on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) for further information.

- **Enviar comentarios**

  You can send feedback on our form, located at [the feedback page](https://scratchaddons.com/feedback). Your feedback may give us a different perspective in the extension development and help us know things needed attention and fix bugs.

- **Dejar una reseña en las tiendas**

  You can leave us a review about Scratch Addons on [the Chrome extension page](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) or [the Firefox addon page](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/).

- **Marcar nuestro repositorio como favorito**

  Basically, the GitHub star is similar to the Scratch star/favorite. You can do this by going to [our repository](https://github.com/ScratchAddons/ScratchAddons) and click the "Star" button on the top-right corner.

- **Correr la voz**

  You can tell anyone about Scratch Addons, like your friends, your relatives, your family members, or even your teacher, if you want. We're just asking you to [not do this on the Scratch website](#can-i-tell-people-about-scratch-addons-on-scratch).

### ¿Cómo puedo crear mi propio addon?

Read more about how to create an addon on Scratch Addons [here](/docs/develop/getting-started).

### ¿Cómo puedo poner mi nombre en la [página de contribuyentes](/contributors)?

Por favor lea y siga la instrucción de [esta propuesta](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}) para tener tu nombre en la página dicha.

### ¿Cómo puedo eliminar mi nombre de la [página de contribuyentes](/contributors)?

If you don't want your name to be on the page, please tell us by creating an issue on [our contributors repository](https://github.com/ScratchAddons/contributors/issues/), or by other means of contact. We're sorry for the inconvenience.

### ¿Qué puedo hacer si encuentro un problema?

You can tell us using one of these methods.

- Send it through [our feedback form](https://scratchaddons.com/feedback).
- Create an issue on [the repository](https://github.com/ScratchAddons/ScratchAddons/issues).
- Create a post on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Tell us on [our Discord server](https://discord.gg/R5NBqwMjNc).

### Creo que les falta una función. ¿Qué puedo hacer?

If you think a feature is missing, or you want to suggest an addon to the extension, or you have a good idea, tell us by [following one of the methods mentioned above](#what-can-i-do-if-i-find-a-problem).

### ¿Dónde puedo discutir sobre Scratch Addons?

You can do it on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) or [our Discord server](https://discord.gg/R5NBqwMjNc). There, you can discuss about it and ask questions if you're having trouble.

### Creo que Scratch Addons realentiza Scratch. ¿Qué puedo hacer?

Try to turn off addons that you don't need. Also, check addon notices and warnings to decide which addons should be turned off for better performance. 

### ¿Cómo puedes activar los addons easter egg?

To reveal the easter egg addons, do the Konami Code (↑↑↓↓←→←→BA) with your keyboard on the settings page. After that, the easter egg addons will be shown, letting you to activate them.

Some of our easter egg addons are "Fix capitalization of Account Settings" and "Semicolon glitch". Check out [the addons tab](/addons) for a complete list.

### ¡Tengo más preguntas!

If you have more questions that need answers, you can create a post on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) or send a message [on our Discord server](https://discord.gg/R5NBqwMjNc). Someone will try to answer it for you.
