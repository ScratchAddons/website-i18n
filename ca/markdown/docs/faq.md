---
title: Preguntes freqüents / FAQ
description: Aquesta pàgina enumera les preguntes més freqüents relacionades amb l'extensió i el projecte Scratch Addons.
---

Aquesta pàgina enumera les preguntes més freqüents relacionades amb l'extensió i el projecte Scratch Addons.

### Què és Scratch Addons?

Scratch Addons és una extensió del navegador "tot en un" per la web i l'editor de Scratch. Proporciona funcions i temes (anomenats addons internament), tant per al lloc web de Scratch com per a l'editor de projectes. La missió d'Scratch Addons és combinar totes les extensions, userscripts i userstyles existents de Scratch, desenvolupats per diversos membres de la comunitat Scratch, en un únic lloc de fàcil accés, alhora que permet als usuaris triar quines volen activar.

### Què és exactament un "addon"?

Un addon és similar a una extensió o un userscript, però utilitzen API especials proporcionades per l'extensió de Scratch Addons. Aquestes API permeten als complements executar scripts en una pàgina de Scratch (userscripts) o aplicar estils al lloc web de Scratch (userstyles).

Els Userscripts poden utilitzar les API de JavaScript `addon.*`, que els permeten obtenir informació relacionada amb Scratch (per exemple, obtenir l'usuari que ha iniciat sessió actual) i també utilitzar API d'extensió (com ara enviar notificacions).

### Si tot és un addon, què fa Scratch Addons?

Per si mateix, Scratch Addons és només un carregador de addons. Les seves principals tasques són:

- Permet als usuaris habilitar, desactivar i configurar addons.
- Executeu addons i proporcioneu-los API.
- Proporcioneu un estat global als complements (per exemple, l'API addon.auth).
- Prototips contaminats perquè els utilitzin scripts d'usuari addicionals.
- Proporcioneu maneres d'accedir i modificar l'estat de Redux.
- Eviteu que els complements interfereixin entre ells.
- Eviteu treballs duplicats de diferents complements.

### Scratch Addons és segur? 

Sí. Scratch Addons no hauria de tenir cap problema de seguretat en la seva versió més recent. Scratch Addons és un projecte de codi obert, de manera que el codi està constantment verificat pels col·laboradors de Scratch Addons, així com per revisors de Chrome Web Store i Add-ons for Firefox.

### Com puc informar d'una vulnerabilitat de seguretat?

Si trobeu una vulnerabilitat de seguretat, poseu-vos en contacte amb World_Languages en privat enviant un correu electrònic a `worldxlanguages (at) gmail.com`. Si no rebeu una resposta en 48 hores, creeu un problema [aquí](https://github.com/ScratchAddons/ScratchAddons/issues/) indicant que heu enviat un correu electrònic.

Pots [llegir la nostra política de seguretat](https://github.com/ScratchAddons/ScratchAddons/security/policy) o [consultar els nostres avisos que hem publicat](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### El meu compte estarà segur quan utilitzi Scratch Addons?

Scratch Addons no utilitza les credencials del vostre compte per funcionar normalment. De fet, podeu tancar la sessió des de Scratch i encara funcionará. Només enviaran sol·licituds en funció de les galetes que tingueu, que us proporciona el navegador per a cada sol·licitud, de manera que alguns complements com Scratch Messaging no funcionaran quan inicieu sessió, però no afectaran altres parts del fitxer. extensió.

Addons a Scratch Addons també han estat auditats per diversos col·laboradors al repositori, de manera que ningú no pot passar un codi maliciós sota els nostres ulls.

Mai no enviem informació del compte de Scratch ni configuració d'extensió fora del vostre navegador. Consulteu [la política de privadesa de l'extensió](/docs/privacy/policies/extension) per obtenir més informació.

### Puc explicar a la gent sobre Scratch Addons a Scratch?

No pots, i si us plau, no. Hi ha una política que prohibeix la publicitat d'extensions del navegador/scripts d'usuari [aquí] (https://scratch.mit.edu/discuss/post/2907564/). Tanmateix, podeu utilitzar diferents mètodes per explicar als vostres amics els complements de Scratch.

### Com puc contribuir al Scratch Addons?

En primer lloc, gràcies pel vostre interès en contribuir a Scratch Addons. Agraïm el vostre interès i les vostres aportacions posteriors.

Com a projecte de codi obert, donem la benvinguda a qualsevol tipus de contribució. Ni tan sols cal que ens preguntis ni que tinguis un determinat rang. Qualsevol és benvingut. Fins i tot hi ha la possibilitat que ni tan sols us adoneu que heu contribuït al projecte!

De totes maneres, tornem al punt. Pots contribuir de moltes formes, i algunes són molt fàcils.

- **Aporta algun codi**

  Si pots programar en JavaScript, HTML5 i CSS, pots contribuir fent una mica de codificació/programació. Pots corregir errors, fer front a algunes sol·licituds o crear el teu propi addon.

  Després d'això, heu de crear una sol·licitud d'extracció. Podeu fer-ho bifurcant [el repositori](https://github.com/ScratchAddons/ScratchAddons/), feu els canvis necessaris i creeu una sol·licitud d'extracció. Si es considera factible, ho fusionarem.

  També estem oberts a aportacions d'altres aspectes que no siguin l'ampliació. Podeu veure els nostres dipòsits a [la nostra pàgina de l'organització de GitHub] (https://github.com/ScratchAddons) i ajudar-nos a crear-los.

- **Suggereix una idea**

  Teniu alguna cosa que creieu que seria una bona addició als complements de Scratch? [Explica'ns!](#i-think-you-missed-a-feature-what-can-i-do)

- **Informa d'un error**

  Has trobat un error a un dels nostres complements, la pàgina de configuració o qualsevol altra cosa a la nostra extensió? [Envieu-nos un informe d'error](#what-can-i-do-if-i-find-a-problem).

- **Tradueix Scratch Addons**

  Si pots parlar un altre idioma que no sigui l'anglès amb fluïdesa, pots ajudar a traduir/localitzar Scratch Addons al vostre idioma. Podeu començar des d' [aquí](/docs/localization/joining-the-localization-team).

- **Escriu la documentació**

  Coneixes Scratch Addons? Si és així, pots escriure la documentació corresponent. La documentació pot incloure com utilitzar-la o com funciona. Si us plau, poseu-vos en contacte amb nosaltres a [la nostra pestanya Discussió] (https://github.com/ScratchAddons/ScratchAddons/discussions) per obtenir més informació.

- **Enviar comentaris**

  Pots enviar comentaris al nostre formulari, situat a [la pàgina de comentaris] (https://scratchaddons.com/feedback). Els  comentaris poden donar-nos una perspectiva diferent en el desenvolupament de l'extensió i ajudar-nos a saber les coses que necessiten atenció i corregir errors.

- **Deixa una valoració a les botigues**

  Pots deixar-nos una ressenya sobre els complements de Scratch a [la pàgina d'extensió de Chrome](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) o a la [pàgina de addons de Firefox](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/).

- **Dona-li una estrella al nostre repositori**

  Bàsicament, l'estrella de GitHub és similar a l'estrella/favorit de Scratch. Podeu fer-ho si aneu al [nostre repositori](https://github.com/ScratchAddons/ScratchAddons) i feu clic al botó "Estrella" a la cantonada superior dreta.

- **Escampa la veu**

  Podeu parlar a qualsevol persona sobre Scratch Addons, com ara els vostres amics, els vostres familiars, els membres de la vostra família o fins i tot el vostre professor, si voleu. Només us demanem que [no feu això al lloc web de Scratch](#can-i-tell-people-about-scratch-addons-on-scratch).

### Com puc crear el meu propi addon?

Read more about how to create an addon on Scratch Addons [here](/docs/develop/getting-started).

### Com puc posar el meu nom a la [pàgina de col·laboradors](/contributors)?

Si us plau, llegiu i seguiu les instruccions d'[aquest issue](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}) per tenir el vostre nom a la pàgina.

### Com puc eliminar el meu nom de la [pàgina de col·laboradors](/contributors)?

Si no voleu que el vostre nom aparegui a la pàgina, digueu-nos-ho creant un problema al [nostre repositori de col·laboradors](https://github.com/ScratchAddons/contributors/issues/), o per altres mitjans de contacte. Lamentem les molèsties.

### Què puc fer si trobo un problema?

Ens pots dir mitjançant un d'aquests mètodes.

- Envieu-lo a través del [nostre formulari de comentaris] (https://scratchaddons.com/feedback).
- Creeu un issue al [repositori] (https://github.com/ScratchAddons/ScratchAddons/issues).
- Creeu una publicació a [la nostra pestanya Discussió] (https://github.com/ScratchAddons/ScratchAddons/discussions).
- Digueu-nos-ho al [nostre servidor de Discord](https://discord.gg/R5NBqwMjNc).

### Crec que us heu oblidat una funció. Què puc fer?

Si creus que falta una funció, o vols suggerir un complement a l'extensió, o tens una bona idea, digueu-nos-ho [seguint un dels mètodes mencionats anteriorment](#what-can-i-do-if-i-find-a-problem).

### On puc parlar sobre Scratch Addons?

Pots fer-ho a [la nostra pestanya Discussió] (https://github.com/ScratchAddons/ScratchAddons/discussions) o al [nostre servidor de Discord] (https://discord.gg/R5NBqwMjNc). Allà, podeu parlar-ne i fer preguntes si teniu problemes.

### Crec que Scratch Addons relentitza el Scratch. Què puc fer?

Intenteu desactivar els complements que no necessiteu. A més, comproveu els avisos i avisos de complements per decidir quins complements s'han de desactivar per obtenir un millor rendiment.

### Com pots activar els addons d'ou de pasqua?

Per revelar els addons de ous de Pasqua, fes el "Konami Code" (↑↑↓↓←→←→BA) amb el teclat a la pàgina de configuració. Després d'això, es mostraran els complements d'ou de Pasqua, que us permetran activar-los.

Alguns dels nostres addons d'ou de Pasqua són "Corregir la majúscula de la configuració del compte" i "Problema de punt i coma". Consulteu [la pestanya de addons](/addons) per obtenir una llista completa.

### Tinc més preguntes!

Si teniu més preguntes que necessiten respostes, podeu crear una publicació a [la nostra pestanya Discussió](https://github.com/ScratchAddons/ScratchAddons/discussions) o enviar un missatge [al nostre servidor de Discord](https:// discord.gg/R5NBqwMjNc). Algú intentarà respondre-ho per tu.
