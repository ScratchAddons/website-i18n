---
title: Pogosta vprašanja
description: Na tej strani je seznam pogostih vprašanj o razširitvi in projektu Scratch Addons.
---

Na tej strani je seznam pogostih vprašanj o razširitvi in projektu Scratch Addons.

### Kaj je Scratch Addons?

Scratch Addons je razširitev brskalnikov za spletno stran in urejevalnik projektov Scratch. Doda nove funkcije in teme (v razširitvi se imenujejo dodatki) za spletno stran in urejevalnik projektov. Njen cilj je zbrati obstoječe razširitve, uporabniške skripte in uporabniške sloge, ki so jih razvili člani Scratcheve skupnosti, na enem mestu, do katerega lahko uporabniki enostavno dostopajo in kjer lahko še vedno izberejo tiste dodatke, ki bi jih radi uporabili.

### Kaj točno je "dodatek"?

Dodatek je podoben razširitvi ali uporabniški skripti, vendar uporablja posebne programske vmesnike, ki so del razširitve Scratch Addons. Dodatkom omogočajo, da izvajajo kodo na Scratchevih straneh (uporabniške skripte) ali pa Scratchevi spletni strani dodajo sloge (uporabniški slogi).

Uporabniške skripte lahko uporabljajo vmesnike `addon.*`, ki jim omogočajo dostop do podatkov, povezanih s Scratchem (npr. o trenutno vpisanem uporabniku) in do vmesnikov za razširitve (npr. pošiljanje obvestil).

### Če je vse dodatek, kaj naredi Scratch Addons?

Sam po sebi je Scratch Addons samo upravitelj dodatkov. Njegove glavne naloge so:

- Uporabnikom omogoča, da vključijo, izključijo in spremenijo nastavitve dodatkov.
- Izvede kodo dodatkov in jim omogoča dostop do programskih vmesnikov.
- Dodatkom priskrbi podatke o stanju Scratcha in razširitve (npr. vmesnik addon.auth).
- Onesnaži prototipe objektov, ki jih potrebujejo uporabniške skripte dodatkov.
- Omogoči dostop in spreminjanje stanja Redux.
- Prepreči, da bi dodatki motili drug drugega.
- Naredi stvari, za katere bi sicer morali različni dodatki skrbeti posebej.

### Je Scratch Addons varen?

Da. Najnovejša različica razširitve ne bi smela imeti nobenih varnostnih napak. Scratch Addons je odprtokoden projekt, zato kodo ves čas nadzorujejo tako sodelavci Scratch Addons kot pregledovalci Spletne trgovine Chrome in Dodatkov za Firefox.

### Kako lahko prijavim varnostno napako?

Če najdete varnostno napako, pišite World_Languages zasebno na e-poštni naslov `worldxlanguages (at) gmail.com`. Če v 48 urah ne dobite odgovora, prijavite napako [tukaj](https://github.com/ScratchAddons/ScratchAddons/issues/) in omenite, da ste poslali e-pošto.

Lahko [preberete naš varnostni pravilnik](https://github.com/ScratchAddons/ScratchAddons/security/policy) ali [preverite objavljene varnostne napake](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### Bo moj Scratch račun med uporabo Scratch Addons varen?

Scratch Addons za delovanje ne uporablja podatkov o vašem računu. V resnici ni treba, da ste vpisani v Scratch, da lahko uporabljate Scratch Addons. Scratch Addons pošilja zahteve Scratchevi spletni strani samo na podlagi piškotkov, ki jih imate in jih vsaki zahtevi doda brskalnik. Tako nekateri dodatki, na primer Scratch Messaging, ne delujejo, če niste vpisani, vendar to ne vpliva na druge dele razširitve.

Dodatke, ki so del Scratch Addons, preveri več sodelavcev na GitHub, zato nihče ne more preprosto dodati kode, ki bi bila nevarna za vaš račun, ne da bi mi to opazili.

Nikoli ne pošiljamo podatke o vašem Scratch računu ali nastavitvam razširitve nikomur, razen vašemu brskalniku. Za več informacij glejte [politiko zasebnosti razširitve](/docs/privacy/policies/extension).

### Lahko ljudem na Scratchu povem za Scratch Addons?

Ne, in prosimo, da tega ne naredite. [Pravila](https://scratch.mit.edu/discuss/post/2907564/) prepovedujejo oglaševanje razširitev in uporabniških skript. Kljub temu lahko svojim prijateljem predstavite Scratch Addons na drugačne načine.

### Kako lahko pomagam Scratch Addons?

Hvala, da vas zanima sodelovanje pri Scratch Addons. Veseli smo vašega zanimanja in prihodnjih prispevkov.

Kot odprtokoden projekt smo veseli vseh vrst prispevkov. Ni treba niti, da nas prej vprašate ali da imate določen status. Vsak lahko sodeluje. Mogoče sploh ne boste vedeli, da ste sodelovali pri projektu!

Torej: sodelujete lahko na veliko različnih načinov, in nekateri so res preprosti.

- **Prispevajte kodo**

  Če znate jezike JavaScript, HTML5 in CSS, nam lahko pomagate s programiranjem. Lahko popravite kakšno napako, dodate novo funkcijo ali pa naredite nov dodatek.

  After that, you need to create a pull request. You can do so by forking [the repository](https://github.com/ScratchAddons/ScratchAddons/), do your necessary changes, and create a pull request. If it is deemed feasible, we will merge it.

  We're also open for contributions of other aspects than the extension. You can view our repositories on [our GitHub organization page](https://github.com/ScratchAddons) and help us build them.

- **Suggest an idea**  

  Have something that you think would be a good addition to Scratch Addons? [Tell us!](#i-think-you-missed-a-feature-what-can-i-do)

- **Prijavite napako**

  Found a bug in one of our addon, the settings page, or anything else on our extension? [Send us a bug report](#what-can-i-do-if-i-find-a-problem).

- **Prevajajte Scratch Addons**

  Če tekoče govorite jezik, ki ni angleščina, lahko pomagate pri prevajanju Scratch Addons v vaš jezik. Začnete lahko [tukaj](/docs/localization/joining-the-localization-team).

- **Napišite dokumentacijo**

  Are you familiar with Scratch Addons? If so, you can write the documentation for it. The documentation can include how to use it, or how it works. Please contact us on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) for further information.

- **Send feedback**  

  You can send feedback on our form, located at [the feedback page](https://scratchaddons.com/feedback). Your feedback may give us a different perspective in the extension development and help us know things needed attention and fix bugs.

- **Leave a review on the stores**

  You can leave us a review about Scratch Addons on [the Chrome extension page](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) or [the Firefox addon page](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/).

- **Star our repository**

  Basically, the GitHub star is similar to the Scratch star/favorite. You can do this by going to [our repository](https://github.com/ScratchAddons/ScratchAddons) and click the "Star" button on the top-right corner.

- **Spread the word**

  You can tell anyone about Scratch Addons, like your friends, your relatives, your family members, or even your teacher, if you want. We're just asking you to [not do this on the Scratch website](#can-i-tell-people-about-scratch-addons-on-scratch).

### Kako lahko naredim svoj dodatek?

Read more about how to create an addon on Scratch Addons [here](/docs/develop/getting-started).

### How can I put my name on the [contributors page](/contributors)?

Please read and follow the instruction of [this issue](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}) in order to have your name on said page.

### Kako lahko svoje ime odstranim s [strani s sodelavci](/contributors)?

If you don't want your name to be on the page, please tell us by creating an issue on [our contributors repository](https://github.com/ScratchAddons/contributors/issues/), or by other means of contact. We're sorry for the inconvenience.

### Kaj lahko naredim, če najdem težavo?

Lahko nam jo sporočite na enega od naslednjih načinov.

- Izpolnite [obrazec za povratne informacije](https://scratchaddons.com/feedback).
- Prijavite težavo [na GitHub](https://github.com/ScratchAddons/ScratchAddons/issues).
- Ustvarite objavo na [zavihku za pogovor](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Povejte nam na [strežniku Discord](https://discord.gg/R5NBqwMjNc).

### I think you missed a feature. What can I do?

If you think a feature is missing, or you want to suggest an addon to the extension, or you have a good idea, tell us by [following one of the methods mentioned above](#what-can-i-do-if-i-find-a-problem).

### Where can I discuss about Scratch Addons?

You can do it on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) or [our Discord server](https://discord.gg/R5NBqwMjNc). There, you can discuss about it and ask questions if you're having trouble.

### Mislim, da Scratch Addons naredi Scratch počasnejši. Kaj lahko naredim?

Try to turn off addons that you don't need. Also, check addon notices and warnings to decide which addons should be turned off for better performance. 

### How can you activate the easter egg addons?

To reveal the easter egg addons, do the Konami Code (↑↑↓↓←→←→BA) with your keyboard on the settings page. After that, the easter egg addons will be shown, letting you to activate them.

Some of our easter egg addons are "Fix capitalization of Account Settings" and "Semicolon glitch". Check out [the addons tab](/addons) for a complete list.

### Še imam vprašanja!

If you have more questions that need answers, you can create a post on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) or send a message [on our Discord server](https://discord.gg/R5NBqwMjNc). Someone will try to answer it for you.
