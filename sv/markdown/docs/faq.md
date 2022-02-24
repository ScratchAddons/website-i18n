---
title: Vanliga frågor
description: Denna sida innehåller några vanliga frågor relaterade till Scratch Addons tillägget och projektet.
---

Denna sida innehåller några vanliga frågor relaterade till Scratch Addons tillägget och projektet.

### Vad är Scratch Addons?

Scratch Addons är ett "allt-i-ett" tillägg för din webbläsare som justerar Scratch hemsida och projektredigerare. Den tillhandahåller funktioner och teman (benämns som tillägg internt), både för Scratch hemsida och projektredigeraren. Scratch Addons uppdrag är att kombinera alla existerande Scratch-tillägg, användarskript och användarstilar, utvecklade av ett antal medlemmar av Scratch gemenskap, till en enda plats som är enkel att nå, medans den fortfarande ska låta användare välja vilka tillägg de vill använda.

### Vad är ett "tillägg" exakt?

An addon is similar to an extension or a userscript, but they use special APIs provided by the Scratch Addons extension. These APIs allow addons to run scripts on a Scratch page (userscripts) or apply styles to the Scratch website (userstyles).

Userscripts can use the `addon.*` JavaScript APIs, which allow them to obtain Scratch-related information (for example, get the current logged in user) and also use extension APIs (like sending notifications).

### Om allt är tillägg, vad gör då Scratch Addons?

Per se, Scratch Addons är endast en tilläggsladdare. Huvuduppgifterna är:

- Tillåta användare att aktivera, avaktivera och konfigurera tillägg.
- Köra tillägg och tillhandahålla API:er till dem.
- Tillhandahålla global state för tillägg (ett exempel på detta är addon.auth API:et).
- Förorena prototyper för användning av tilläggsanvändarskript.
- Tillhandahålla sätt att få tillgång till samt modifiera Redux state.
- Undvika att tillägg skapar konflikter med varandra.
- Undvika att tillägg upprepar samma funktion från olika webbläsartillägg.

### Är Scratch Addons säkert?

Ja. Scratch Addons bör inte ha några säkerhetsbrister i den senaste versionen. Scratch Addons projektet har öppen källkod, så koden verifieras konstant av Scratch Addons medverkande, såväl som flera granskare från Chrome Web Store samt Add-ons för Firefox.

### Hur kan jag rapportera en säkerhetsbrist?

Om du skulle finna en säkerhetsbrist ber vi dig kontakta World_Languages privat genom att maila `worldxlanguages (snabel-a) gmail.com`. Om du inte får en respons imon 48 timmar, är vi väldigt tacksamma om du skapar en fråga [här](https://github.com/ScratchAddons/ScratchAddons/issues/) med notis om att du skickat ett mail.

Du kan antingen [läsa vår säkerhetspolicy](https://github.com/ScratchAddons/ScratchAddons/security/policy), eller [kolla in våra rådgivare som vi har publicerat](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### Kommer mitt konto förbli säkert medans jag använder Scratch Addons?

Scratch Addons använder inte din kontoinformation i något väsentligt. Du kan vara utloggad från Scratch, och Scratch Addons kommer fortfarande att fungera. Scratch Addons skickar bara förfrågningar baserat på kakorna som du har sparat, som tillhandahålls av webbläsaren för varje förfrågning, av vilket konsekvensen blir att några tillägg så som Scratch meddelandesystem inte fungerar när du loggar in, men det kommer inte att påverka andra delar av Scratch Addons.

Tillägg på Scratch Addons har även granskats av flera medverkande i databasen, så ingen kan bara slänga in ett skadligt skript under våra ögon.

Vi skickar aldrig din kontoinformation eller tilläggsinställningar utanför din webbläsare. Se [tilläggens integritetspolicy](/docs/privacy/policies/extension) för ytterligare information.

### Kan jag nämna Scratch Addons till personer på Scratch?

Du kan inte, och försök snälla inte. Det finns en policy som förbjuder annonsering för webbläsartillägg. tillägg/användarskipt [här](https://scratch.mit.edu/discuss/post/2907564/). Du kan dock använda olika metoder för att berätta för dina vänner om Scratch Addons.

### Hur kan jag bidra till Scratch Addons?

Först, tack för ditt intresse i att bidra till Scratch Addons. Vi uppskattar ditt intresse och framtida bidrag.

Som ett projekt med öppen källkod välkomnar vi alla typer av insatser. Du behöver inte ens fråga oss eller ha en speciell rank. Vem som helst är välkommen. Det finns till och med en chans att du inte ens är medveten om att du har bidragit till projektet!

Hur som helst, tillbaks till frågan. Du kan enkelt bidra på många sett, och vissa alternativ är väldigt smidiga.

- **Bidra med kod**

  Om du kan programmera i JavaScript, HTML5 och CSS, kan du bidra genom att koda. Du kan fixa buggar, hantera några förfrågningar, eller skapa ditt eget tillägg.

  Efter det behöver du skapa en pull request. Du kan göra det genom att klyva [kodbasen](https://github.com/ScratchAddons/ScratchAddons/), genomför dina ändringar och skapa sedan din pull request. Om den bedöms som rimlig, sammanfogas den.

  Vi är öppna för insatser av andra aspekter än tillägg. Du se våra kodbaser på [vår GitHub-organisationssida](https://github.com/ScratchAddons) och hjälpa oss att bygga dem.

- **Föreslå en idé**

  Har du något som du tror skulle var ett bra tillägg i Scratch Addons? [Berätta för oss!](#i-think-you-missed-a-feature-what-can-i-do)

- **Rapportera en bugg**

  Har du hittat en bugg i något av våra addons, inställningssidan, eller vad som helst i vårt tillägg? [Skicka en bugganmälan](#what-can-i-do-if-i-find-a-problem).

- **Översätt Scratch Addons**

  Om du kan tala ett annat språk en Engelska flytande, så kan du hjälpa till med att översätta Scratch Addons till ditt språk. Du kan starta [här](/docs/localization/joining-the-localization-team).

- **Skriv i dokumentationen**

  Är du bekant med Scratch Addons? Om det är fallet så kan du skriva dokumentation för det. Dokumentationen kan innehålla information om hur du använder det, eller hur det fungerar. Var god kontakta oss på [vår diskussionsflik](https://github.com/ScratchAddons/ScratchAddons/discussions) för vidare information.

- **Skicka återkoppling**

  Du kan skicka återkoppling på vårt forum, som finns på [återkopplingssidan](https://scratchaddons.com/feedback). Din återkoppling kan ge oss ett annorlunda perspektiv i tilläggets utveckling och hjälpa oss ta reda på vad vi måste lägga fokus på samt fixa buggar.

- **Lämna en recension på affären**

  Du kan lämna en recension av Scratch Addons på [Chromes tilläggssida](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) eller [Firefox tilläggssida](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/).

- **Ge vår kodbas en stjärna**

  I princip fungerar GitHubs stjärnsystem ungefär som Scratch stjärna/favorit. Du kan göra det här genom att besöka [vår kodbas](https://github.com/ScratchAddons/ScratchAddons) och klicka på "Star"-knappen på det översta högra hörnet.

- **Dela ordet**

  Du kan berätta om Scratch Addons för vem som helst, exempelvis dina vänner, dina släkt, dina familjemedlemmar, eller din lärare, om du vill. Vi ber dig endast att [inte göra detta på Scratch hemsida](#can-i-tell-people-about-scratch-addons-on-scratch).

### Hur kan jag skapa mitt eget tillägg?

Läs mer om hur du kan skapa ett tillägg för Scratch Addons [här](/docs/develop/getting-started).

### Hur kan jag få mitt namn på [medarbetarsidan](/contributors)?

Var god läs och följ instruktionerna på [den här frågan](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}) för att få ditt namn på nämn sida.

### Hur kan jag ta ned mitt namn från [medarbetarsidan](/contributors)?

Om du inte vill ha ditt namn på sidan, ber vi dig berätta av vilken anledning på [vår medarbetarkodbas](https://github.com/ScratchAddons/contributors/issues/), eller genom någon annan form av kontakt. Vi ber om ursäkt för besväret.

### Vad kan jag göra om jag hittar ett problem?

Du kan berätta för oss genom en av dessa metoder.

- Skicka det genom [vårt återkopplingsformulär](https://scratchaddons.com/feedback).
- Skapa en anmälan på [kodbasen](https://github.com/ScratchAddons/ScratchAddons/issues).
- Skapa ett inlägg på [vår diskussionssida](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Berätta för oss på [vår Discord-server](https://discord.gg/R5NBqwMjNc).

### Jag tror att det saknas en funktion. Vad kan jag göra?

Om du tror att det saknas en funktion, eller om du vill ge förslag om ett tillägg till Scratch Addons, eller om du har en bra idé, berätta då för oss genom att [följa en av metoderna vi beskrev ovan](#what-can-i-do-if-i-find-a-problem).

### Var kan jag diskutera Scratch Addons?

Du kan göra detta på [vår diskussionssida](https://github.com/ScratchAddons/ScratchAddons/discussions) eller [vår Discord-server](https://discord.gg/R5NBqwMjNc). Där kan du diskutera eller ställa frågor om du upplever problem med något.

### Jag tror att Scratch Addons saktar ned Scratch. Vad kan jag göra?

Du kan stänga av tillägg som du inte behöver. Du kan även kolla tilläggsnotiser och varningar för att bedöma vilka tillägg som bör stängas av för bättre prestanda.

### Hur kan du aktivera påskäggstillägg?

För att visa påskäggstillägg, slå Konami-koden (↑↑↓↓←→←→BA) med ditt tangentbord på inställningssidan. Efter det, så kommer påskäggstilläggen att uppenbara sig, vilket låter dig aktivera dem.

Några av våra påskäggstillägg är "Fixa kapitalisering av Kontoinställningar" och "Semikolonsglitch". Kolla in [tilläggsfliken](/addons) för en komplett lista.

### Jag har fler frågor!

Om du har fler frågor som kräver svar, kan du skapa ett inlägg på [vår diskussionssida](https://github.com/ScratchAddons/ScratchAddons/discussions) eller genom att skicka ett meddelande [på vår Discord-sever](https://discord.gg/R5NBqwMjNc). Någon kommer att försöka svara på den för dig.
