---
title: คำถามที่พบบ่อย
description: หน้านี้มีรายการคำถามที่พบบ่อยเกี่ยวกับส่วนขยายสำหรับ scratch และโครงงานของมัน
---

หน้านี้มีรายการคำถามที่พบบ่อยเกี่ยวกับส่วนขยายสำหรับ scratch และโครงงานของมัน

### ส่วนขยายสำหรับ scratch คืออะไร

ส่วขยายสำหรับ scratch คือส่วนขยาย "ทุกอย่างในที่เดียว" สำหรับเว็บไซต์ และ ตัวแก้ไขงานของ scratch เราเพิ่มคุณสมบัติและธีม (เราเรียกมันว่าส่วนขยาย) ทั้งสำหรับเว็บไซต์และตัวแก้ไขงาน ภารกิจของเราคือการรวม ส่วนขยาย scratch ที่มีอยู่แล้วทั้งหมด userscript userstyles สร้างโดยผู้คนหลายคนในชุมชน scratch เป็นสิ่งที่เข้าถึงได้ง่าย โดยยังให้ผู้ใช้งานเลือกว่าจะเปิดใช้งานอะไร

### "ส่วนขยาย" คืออะไรกันแน่

ส่วนขยายนั้นคล้ายกับ ส่วนเสริม หรือ userscript แต่พวกมันใช้ api พิเศษ สร้างโดย ส่วนขยายสำหรับ scratch. api เหล่านี้ทำให้ส่วนขยายสามารถเรียกใช้สคริปต์ บนหน้า scratch (userscript) หรือใช้งานธีม บนหน้า scratch (userstyle)

userscript สามารถใช้ JavaScript APIs `ส่วนขยาย*` ซึ่งทำให้มันสามารถดึงข้อมูลเกี่ยวกับ scratch (เช่น ดูว่าใครเป็นคนที่ล็อกอินอยู่) และใช้ APIs ส่วนขยาย (เช่นส่งการแจ้งเตือน)

### แล้วถ้าทุกอย่างเป็นส่วนขยาย แล้ว ส่วนขยายสำหรับ scratch ทำอะไรละ

โดยตัวมันเอง ส่วนขยายสำหรับ scratch เป็นเพียงตัวโหลด ส่วนขยาย งานหลักๆของมันมี :

- ทำให้ผู้ใช้งานสามารถ เปิด ปิด ตั้งค่า ส่วนขยายได้
- เรียกใช้ส่วนขยาย และให้  APIs กับพวกมัน
- Provide global state to addons (for example, the addon.auth API).
- Pollute prototypes for use by addon userscripts.
- Provide ways to access and modify Redux state.
- Avoid addons from interfering with each other.
- Avoid duplicate work from different addons.

### Is Scratch Addons safe? 

Yes. Scratch Addons should not have any security issues in its most recent version. Scratch Addons is an open source project, so the code is constantly being verified by Scratch Addons contributors, as well as by reviewers from the Chrome Web Store, Add-ons for Firefox and Microsoft Edge Add-ons.

### How can I report a security vulnerability?

If you happen to find a security vulnerability please contact World_Languages privately by emailing `worldxlanguages (at) gmail.com`. If you don't get a response within 48 hours, please create an issue [here](https://github.com/ScratchAddons/ScratchAddons/issues/) mentioning you sent an email.

You can either [read our security policy](https://github.com/ScratchAddons/ScratchAddons/security/policy), or [check our advisories that we have published](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### Will my account be safe when using Scratch Addons?

Scratch Addons doesn't use your account credentials to essentially work. In fact, you can be logged out from Scratch, and Scratch Addons will still work. Scratch Addons will only send requests based on the cookies that you have, which is supplied by the browser for each request, so some addons like Scratch Messaging won't work when you are logging in, but it won't affect other parts of the extension.

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

  You can leave us a review about Scratch Addons on [the Chrome extension page](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco), [the Firefox addon page](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) or the [Microsoft Edge addon page](https://microsoftedge.microsoft.com/addons/detail/scratch-addons/iliepgjnemckemgnledoipfiilhajdjj).

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
