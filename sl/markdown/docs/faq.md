---
title: Pogosta vprašanja
description: Na tej strani je seznam pogostih vprašanj o razširitvi in projektu Scratch Addons.
---

Na tej strani je seznam pogostih vprašanj o razširitvi in projektu Scratch Addons.

## General questions

### Kaj je Scratch Addons?

Scratch Addons je razširitev brskalnikov za spletno stran in urejevalnik projektov Scratch. Doda nove funkcije in teme (v razširitvi se imenujejo dodatki) za spletno stran in urejevalnik projektov. Njen cilj je zbrati obstoječe razširitve, uporabniške skripte in uporabniške sloge, ki so jih razvili člani Scratcheve skupnosti, na enem mestu, do katerega lahko uporabniki enostavno dostopajo in kjer lahko še vedno izberejo tiste dodatke, ki bi jih radi uporabili.

### Who created Scratch Addons?

Scratch Addons is a team project led by World_Languages. You can find the list of people who have contributed to us on [the Credits page](/credits). While the "Scratch Messaging" and "Developer tools" addons were initially created by griffpatch, he does not maintain the extension.

### What does Scratch Addons include?

Scratch Addons includes over 100 addons, which can be enabled or disabled individually. Some addons can also be further configured, and some have presets, such as dark mode for the website theme. Scratch Addons also includes a popup, which can be used to quickly access messages, cloud games, and the settings page. Scratch Addons is translated into multiple languages, including German, French, Spanish, and Japanese.

### Is this the same as TurboWarp Addons?

[TurboWarp](https://turbowarp.org/) has some addons from Scratch Addons which can be used on their editor without installing Scratch Addons. However, Scratch Addons also includes addons for the Scratch website and the popup display. Therefore, it is still useful to have Scratch Addons even if you only code using TurboWarp.

## System requirements

### What are the system requirements for Scratch Addons?

Scratch Addons is officially supported on the desktop versions of [Google Chrome](https://google.com/chrome/) (version 80 and up), [Microsoft Edge](https://www.microsoft.com/en-us/edge) (version 80 and up), and [Mozilla Firefox](https://mozilla.org/firefox/) (version 86 and up), and should also work on other desktop browsers that are based on those browsers. Please check out [this page](../getting-started/installing/) for complete information.

### Can I use Scratch Addons on a mobile device?

For Android users: Yes, but it is not recommended. Major browsers do not allow Scratch Addons (or any other extensions) to be installed, so you need to use browsers such as [Kiwi](https://kiwibrowser.com/) to do so. Scratch Addons' UI is not well-tested on touchscreens or environments with small screen size, so some of the features might not work as expected.

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

## Security and privacy

### Je Scratch Addons varen?

Yes. Scratch Addons should not have any security issues in its most recent version. Scratch Addons is an open source project, so the code has been reviewed by Scratch Addons contributors. Additionally, Chrome Web Store, Add-ons for Firefox, and Microsoft Edge Add-ons review each new version of Scratch Addons before publishing it on their stores.

### Kako lahko prijavim varnostno napako?

If you happen to find a security vulnerability, please contact World_Languages privately by emailing `worldxlanguages (at) gmail.com`. If you don't get a response within 48 hours, please [create an issue](https://github.com/ScratchAddons/ScratchAddons/issues/) mentioning that you had sent an email.

You can either [read our security policy](https://github.com/ScratchAddons/ScratchAddons/security/policy) or [check our advisories that we have published](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### Bo moj Scratch račun med uporabo Scratch Addons varen?

Yes. Features related to your Scratch account are thoroughly reviewed by Scratch Addons contributors to ensure that they will not harm your Scratch account. Scratch Addons keeps your account credentials secure, and it will not modify or delete your projects or assets without your permission. However, you may use the extension without any account-related features if you so choose.

Dodatke, ki so del Scratch Addons, preveri več sodelavcev na GitHub, zato nihče ne more preprosto dodati kode, ki bi bila nevarna za vaš račun, ne da bi mi to opazili.

We never send any confidential or personally identifying information outside of your browser. See [the extension privacy policy](/docs/privacy/policies/extension) for more information.

## Using Scratch Addons

### How do I enable addons?

To enable addons, first go to the settings by:

- opening the popup and clicking the gear icon on the top-right corner
- going to https://scratch.mit.edu/scratch-addons-extension/settings. Note: you must have the extension installed for this link to work.

Then, find addons you'd like to enable using the sidebar or the search box. To enable an addon, click the switch on the right side of the addon tile.

### Lahko ljudem na Scratchu povem za Scratch Addons?

You can't, and please don't. There is a policy that forbids mentioning browser extensions/userscripts [here](https://scratch.mit.edu/discuss/post/2907564/), and violations have resulted in Scratch Team removing posts or muting accounts. You may, however, use different methods to tell your friends about Scratch Addons.

### Mislim, da Scratch Addons naredi Scratch počasnejši. Kaj lahko naredim?

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

### How can you activate the easter egg addons?

To reveal the easter egg addons, do the Konami Code (↑↑↓↓←→←→BA) with your keyboard on the settings page. After that, the easter egg addons will be shown, letting you to activate them.

Some of our easter egg addons are "Fix capitalization of Account Settings" and "Semicolon glitch". Check out [the addons tab](/addons) for a complete list.

## Contributing

### Kako lahko pomagam Scratch Addons?

Firstly, we appreciate your interest in contributing to Scratch Addons!

As an open source project, we welcome any kind of contribution. You don't need to ask in advance -- everyone is welcome to contribute! You can contribute in many ways, many of which don't require programming knowledge.

- **Prispevajte kodo**

  If you are familiar with JavaScript, HTML, and CSS, you can contribute by fixing bugs, making adjustments, or adding features.

  To incorporate your changes into the main extension, you need to create a pull request. You can do so by forking [the repository](https://github.com/ScratchAddons/ScratchAddons/), creating a branch, making the necessary changes, and then locating the option to create a pull request. We will review it and most likely make some changes before it gets merged.

  You can also contribute to other aspects of the organization, such as our website. You can view all of our repositories on [our GitHub organization page](https://github.com/ScratchAddons).

- **Suggest an idea**  

  Have an idea that you think would be a good addition to Scratch Addons? [Let us know!](#i-think-you-missed-a-feature-what-can-i-do)

- **Prijavite napako**

  Found a bug in one of our addons, the settings page, or anything else in our extension? [Send us a bug report](#what-can-i-do-if-i-find-a-problem).

- **Prevajajte Scratch Addons**

  If you are fluent in another language, you can help translate/localize Scratch Addons to said language. You can start by [joining the localization team](/docs/localization/joining-the-localization-team).

- **Napišite dokumentacijo**

  Are you familiar with the inner workings of Scratch Addons? If so, you can write the documentation for it. The documentation is located in [our website repo](https://github.com/ScratchAddons/website-v2/tree/master/content/docs). Feel free to open a pull request!

- **Send feedback**  

  You can send feedback [on this page](/feedback). Your feedback may give us a different perspective in the extension development and help us know things needed attention and fix bugs.

- **Leave a review on the stores**

  You can leave a review about Scratch Addons on [the Chrome extension page](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco), [the Firefox addon page](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) or [the Microsoft Edge addon page](https://microsoftedge.microsoft.com/addons/detail/scratch-addons/iliepgjnemckemgnledoipfiilhajdjj). This is a great way to help convince others to install the extension!

- **Star our repository**

  Basically, the GitHub star is similar to the Scratch star/favorite. You can do this by going to [our repository](https://github.com/ScratchAddons/ScratchAddons) and clicking the "Star" button on the top-right corner.

- **Spread the word**

  You can tell anyone about Scratch Addons, including your friends, relatives, and teachers. We're just asking you [not to do this on the Scratch website](#can-i-tell-people-about-scratch-addons-on-scratch).

### Kako lahko naredim svoj dodatek?

Read more about it [here](/docs/develop/getting-started).

### Kaj lahko naredim, če najdem težavo?

Lahko nam jo sporočite na enega od naslednjih načinov.

- Send it through [our feedback form](/feedback).
- Prijavite težavo [na GitHub](https://github.com/ScratchAddons/ScratchAddons/issues).
- Ustvarite objavo na [zavihku za pogovor](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Povejte nam na [strežniku Discord](https://discord.gg/R5NBqwMjNc).

### I think you missed a feature. What can I do?

If you want to suggest an addon for the extension or have some other kind of good idea, tell us with [one of these methods](#what-can-i-do-if-i-find-a-problem).

### Where can I discuss Scratch Addons?

You can do it on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) or [our Discord server](https://discord.gg/R5NBqwMjNc). There, you can ask questions and engage with the Scratch Addons community.

## Technical

### Kaj točno je "dodatek"?

Dodatek je podoben razširitvi ali uporabniški skripti, vendar uporablja posebne programske vmesnike, ki so del razširitve Scratch Addons. Dodatkom omogočajo, da izvajajo kodo na Scratchevih straneh (uporabniške skripte), v ozadju (skripte v ozadju) ali pa Scratchevi spletni strani dodajo sloge (uporabniški slogi).

Userscripts can use the `addon.*` JavaScript APIs, which allow them to obtain Scratch-related information (for example, the currently logged in user) and use extension APIs (like sending notifications).

### Če je vse dodatek, kaj naredi Scratch Addons?

By itself, Scratch Addons is just an addon loader. Its main tasks are to:

- Uporabnikom omogoča, da vključijo, izključijo in spremenijo nastavitve dodatkov.
- Izvede kodo dodatkov in jim omogoča dostop do programskih vmesnikov.
- Provide useful data to addons (for example, the addon.auth API).
- Onesnaži prototipe objektov, ki jih potrebujejo uporabniške skripte dodatkov.
- Omogoči dostop in spreminjanje stanja Redux.
- Prepreči, da bi dodatki motili drug drugega.
- Naredi stvari, za katere bi sicer morali različni dodatki skrbeti posebej.

## Other 

### How can I add/remove myself to/from the contributors page?

If you want your name to be on the page, please read and follow the instructions of [this issue](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}).

If you don’t want your name to be on the page, please tell us by creating an issue on our contributors repository, or by other means of contact. We’re sorry for the inconvenience.

### Še imam vprašanja!

If you have more questions that need answers, you can create a post on [our Discussion tab](https://github.com/ScratchAddons/ScratchAddons/discussions) or send a message [on our Discord server](https://discord.gg/R5NBqwMjNc). We will answer as best we can!
