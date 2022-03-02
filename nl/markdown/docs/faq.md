---
title: Veelgestelde Vragen
description: Op deze pagina staan veelgestelde vragen verwant met de Scratch Addons-extensie en -project.
---

Op deze pagina staan veelgestelde vragen verwant met de Scratch Addons-extensie en -project.

### Wat is Scratch Addons?

Scratch Addons is een alles-in-een browserextensie voor de Scratchwebsite en -projecteditor. Het geeft je functies en thema's (intern genaamd addons) voor zowel de Scratchwebsite als de projecteditor. De missie van Scratch Addons is om alle bestaande Scratchextensies, userscripts en userstyles te combineren, gemaakt door meerdere leden van de Scratchgemeenschap, in een enkele makkelijk toegankelijke plaats, terwijl gebruikers nog steeds mogen kiezen welke ze willen aanzetten.

### Wat is precies een "addon"?

Een addon is vergelijkbaar met een extensie of een userscript, maar ze gebruiken speciale API's geleverd door de Scratch Addons-extensie. Deze API's geven addons de mogelijkheid om scripts op een Scratchpagina uit te voeren (userscripts) of stijlen toepassen op de Scratchwebsite (userstyles).

Userscripts kunnen de `addon.*` JavaScript-API's gebruiken, waar ze Scratch-gerelateerde informatie vandaan halen (bijvoorbeeld de ingelogde gebruiker), en ze gebruiken ook extensie-API's (zoals notificaties sturen).

### Als alles een addon is, wat doet Scratch Addons dan?

Op zichzelf is Scratch Addons gewoon een addonlader. Zijn hoofdtaken zijn:

- Laat gebruikers addons in- of uitschakelen en instellen.
- Addons uitvoeren en ze API's leveren.
- De globale status aan addons leveren (zoals de addon.auth API).
- Pollute prototypes for use by addon userscripts.
- Manieren om toegang te krijgen tot Redux-status en het te bewerken geven.
- Vermijden dat addons elkaar onderbreken.
- Dubbel werk van andere addons vermijden.

### Is Scratch Addons veilig?

Ja. Scratch Addons zou geen beveiligingsproblemen moeten hebben in zijn laatste versie. Scratch Addons is een open-bron project, dus de code wordt constant gecheckt door Scratch Addons-helpers, net zoals door recensenten van de Chrome Web Store en Addons voor Firefox.

### Hoe kan ik een beveiligingskwetsbaarheid melden?

Als je een beveiligingskwetsbaarheid tegenkomt, neem dan privé contact op met World_Languages door een e-mail te sturen naar `worldxlanguages (at) gmail.com`. Als je binnen 48 uur geen antwoord krijgt, maak dan [hier](https://github.com/ScratchAddons/ScratchAddons/issues/) een issue dat vermeldt dat je een e-mail hebt gestuurd.

Je kunt [ons beveiligingsbeleid lezen](https://github.com/ScratchAddons/ScratchAddons/security/policy), of [onze gepubliceerde adviezen checken](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### Zal mijn account veilig zijn als ik Scratch Addons gebruik?

Scratch Addons gebruikt niet je accountgegevens om echt te werken. In feite kun je uitgelogd zijn van Scratch, en Scratch Addons zal nog steeds werken. Scratch Addons verstuurt alleen verzoeken gebaseerd op de cookies die je hebt, die worden geleverd door de browser voor elk verzoek, dus sommige addons zoals Scratch-Berichtgeving zullen niet werken als je niet bent ingelogd, maar het zal andere delen van de extensie niet beïnvloeden.

Addons on Scratch Addons also have been audited by multiple contributors on the repository, so no-one can just slip some malicious code under our eyes.

We never send Scratch account information or extension settings outside of your browser. See [the extension privacy policy](/docs/privacy/policies/extension) for more information.

### Can I tell people about Scratch Addons on Scratch?

You can't, and please don't. There is a policy that forbids advertising browser extensions/userscripts [here](https://scratch.mit.edu/discuss/post/2907564/). You may, however, use different methods to tell your friends about Scratch Addons.

### How can I contribute to Scratch Addons?

Firstly, thank you for your interest of contributing to Scratch Addons. We appreciate your interest and your later contributions. 

As an open source project, we welcome any kind of contributions. You don't even need to ask us or to have a certain rank. Anyone is welcome. There's even a chance that you don't even realize that you have contributed to the project! 

Anyway, back to the point. You can contribute in many ways, and some of it is really easy.

- **Contribute some code**

  If you can code on JavaScript, HTML5, and CSS, you can contribute by doing some coding/programming. You can fix bugs, tackle some requests, or create your own addon.

  After that, you need to create a pull request. You can do so by forking [the repository](https://github.com/ScratchAddons/ScratchAddons/), do your necessary changes, and create a pull request. If it is deemed feasible, we will merge it.

  We're also open for contributions of other aspects than the extension. You can view our repositories on [our GitHub organization page](https://github.com/ScratchAddons) and help us build them.

- **Suggest an idea**  

  Have something that you think would be a good addition to Scratch Addons? [Tell us!](#i-think-you-missed-a-feature-what-can-i-do)

- **Report a bug**

  Found a bug in one of our addon, the settings page, or anything else on our extension? [Send us a bug report](#what-can-i-do-if-i-find-a-problem).

- **Translate Scratch Addons**  

  If you can speak another language than English fluently, you can help translate/localize Scratch Addons to your language. You can start from [here](/docs/localization/joining-the-localization-team).

- **Write the documentation**

  Are you familiar with Scratch Addons? If so, you can write the documentation for it. The documentation can include how to use it, or how it works. Please contact us on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) for further information.

- **Send feedback**  

  You can send feedback on our form, located at [the feedback page](https://scratchaddons.com/feedback). Your feedback may give us a different perspective in the extension development and help us know things needed attention and fix bugs.

- **Leave a review on the stores**

  You can leave us a review about Scratch Addons on [the Chrome extension page](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) or [the Firefox addon page](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/).

- **Star our repository**

  Basically, the GitHub star is similar to the Scratch star/favorite. You can do this by going to [our repository](https://github.com/ScratchAddons/ScratchAddons) and click the "Star" button on the top-right corner.

- **Spread the word**

  You can tell anyone about Scratch Addons, like your friends, your relatives, your family members, or even your teacher, if you want. We're just asking you to [not do this on the Scratch website](#can-i-tell-people-about-scratch-addons-on-scratch).

### How can I create my own addon?

Read more about how to create an addon on Scratch Addons [here](/docs/develop/getting-started).

### How can I put my name on the [contributors page](/contributors)?

Please read and follow the instruction of [this issue](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}) in order to have your name on said page.

### How can I remove my name from the [contributors page](/contributors)?

If you don't want your name to be on the page, please tell us by creating an issue on [our contributors repository](https://github.com/ScratchAddons/contributors/issues/), or by other means of contact. We're sorry for the inconvenience.

### What can I do if I find a problem?

You can tell us using one of these methods.

- Send it through [our feedback form](https://scratchaddons.com/feedback).
- Create an issue on [the repository](https://github.com/ScratchAddons/ScratchAddons/issues).
- Create a post on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Tell us on [our Discord server](https://discord.gg/R5NBqwMjNc).

### I think you missed a feature. What can I do?

If you think a feature is missing, or you want to suggest an addon to the extension, or you have a good idea, tell us by [following one of the methods mentioned above](#what-can-i-do-if-i-find-a-problem).

### Where can I discuss about Scratch Addons?

You can do it on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) or [our Discord server](https://discord.gg/R5NBqwMjNc). There, you can discuss about it and ask questions if you're having trouble.

### I think Scratch Addons slows down Scratch. What can I do?

Try to turn off addons that you don't need. Also, check addon notices and warnings to decide which addons should be turned off for better performance. 

### How can you activate the easter egg addons?

To reveal the easter egg addons, do the Konami Code (↑↑↓↓←→←→BA) with your keyboard on the settings page. After that, the easter egg addons will be shown, letting you to activate them.

Some of our easter egg addons are "Fix capitalization of Account Settings" and "Semicolon glitch". Check out [the addons tab](/addons) for a complete list.

### I have more questions!

If you have more questions that need answers, you can create a post on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) or send a message [on our Discord server](https://discord.gg/R5NBqwMjNc). Someone will try to answer it for you.
