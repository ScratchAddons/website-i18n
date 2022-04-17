---
title: Gyakran Ismételt Kérdések
description: Ez az oldal felsorolja a gyakran feltett kérdéseket a Scratch Addons bővítménnyel és projekttel kapcsolatban.
---

Ez az oldal felsorolja a gyakran feltett kérdéseket a Scratch Addons bővítménnyel és projekttel kapcsolatban.

### Mi az a Scratch Addons?

A Scratch Addons egy "minden-egyben" böngészőbővítmény a Scratch weboldalhoz és a szerkesztőjéhez. Különböző segédfunkciókat és témákat (együtt kiegészítőbelsőknek nevezzük) biztosít a Scratch weboldalához és a szerkesztőhöz is egyaránt. A Scratch Addons küldetése, hogy minden létező – a Scratch közösség különféle tagjai által fejlesztett – Scratch kiegészítőt, userscriptet, userstyle-t egyesítsen egy egyetlen, könnyen-elérhető helyre, továbbra is lehetővé téve a felhasználóinak, hogy kiválaszthassák: melyikeket szeretnék aktiválni, és melyikeket nem.

### Mi is egy "kiegészítő" pontosan?

Egy kiegészítő hasonlatos egy bővítményhez, vagy egy userscripthez, de speciális alkalmazásprogramozási felületeket (API) használnak, amiket a Scratch Addons bővítmény biztosít számukra. Ezek a API-k lehetővé teszik a kiegészítőknek, hogy parancsokat futtassanak le egy Scratch oldalon (ezek a userscriptek) vagy stílusokat alkalmazzanak a Scratch weboldalon (userstyle-ok).

A userscriptek tudják használni az `addon.*` JavaScript API-kat, amik lehetővé teszik, hogy megszerezzenek Scratch-hez tartozó információkat (pl. megszerezni a jelenlegi bejelentkezett felhasználót), valamint szintén használják a bővítmény API-kat (mint mondjuk az értesítések küldése).

### Ha minden egy kiegészítő, akkor mit csinál a Scratch Addons?

Önmagában a Scratch Addons csak egy kiegészítő-betöltő. A főfeladatai közé tartoznak:

- A felhasználók számára lehetővé tenni a kiegészítők be-, kikapcsolását, meg konfigurálását.
- A szerkesztők lefuttatása és API-k biztosítása.
- Globális állapotot biztosítani a kiegészítőknek (mint például az addon.auth API)
- Prototípusok átírása használatra a userszkriptek által.
- Lehetőségek biztosítása a Redux állapot eléréséhez és módosításához.
- Kiegészítők egymásba beavatkozásának elkerülése.
- Elkerülése a munka másolásának egy másik kiegészítőtől.

### A Scratch Addons biztonságos?

Igen. A Scratch Addonsnak nem kéne biztonsági problémái akadjanak a legfrissebb verziójában. A Scratch Addons egy nyíltforráskódú projekt, szóval a kód állandóan ellenőrzött a Scratch Addons közreműködői által, ahogy a Chrome Webáruházban és a Firefoxnál is szintén átnézik.

### Hogyan jelenthetek egy biztonsági rést?

Ha bármilyen biztonsági sebezhetőséggel találná szembe magát, akkor kérjük vegye fel a kapcsolatot személyesen World_Languages-sel egy e-mail által, a következő címre küldve: `worldxlanguages (at) gmail.com`. Ha nem kap 48 órán belül sem választ, akkor kérjük készítsen egy problémát [itt] (https://github.com/ScratchAddons/ScratchAddons/issues/) említve, hogy küldött egy e-mailt.

[Elolvashatja a biztonsági irányelveinket](https://github.com/ScratchAddons/ScratchAddons/security/policy), vagy [lecsekkolhatja a advisory-kat, amiket közzé tettünk](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### Biztonságban lesz a fiókom, amikor a Scratch Addons-t használom?

A Scratch Addons nem használja a fiókja hitelesítő adatait az alapvető működéséhez. Valójában lehetsz kijelentkezve is, és a Scratch Addons még úgy is működni fog. A Scratch Addons csak olyan kérelmeket fog küldeni, amik az ön által birtokolt cookie-kon alapulnak, azok pedig a böngésző látja el minden egyes kérésre, így néhány kiegészítő, mint például a Scratch Üzenetküldés nem fog működni, amikor ki van jelentkezve, de más részeit nem fogja érinteni a bővítménynek.

Valamint a kiegészítők a Scratch Addonson felülvizsgálva is vannak számos hozzájáruló által a repositoryn, szóval senki nem tud csak úgy becsúsztatni rosszindulatú kódot a szemünk előtt.

Mi soha nem küldjük el a Scratch fiókinformációkat, vagy bővítménybeállításokat a böngésződön kívül. Nézze meg [a bővítmény biztonsági szabályzatát](/docs/privacy/policies/extension) több információért.

### Tudok beszélni a Scratch Addonsról a Scratchen?

Nem, nem szabad, és kérjük ne is tegye. Van erről egy irányelv [itt](https://scratch.mit.edu/discuss/post/2907564/), ami tiltja a böngészőbővítmények/userscriptek mindennemű reklámozását. Ennek ellenére használhat különböző módszereket a barátai értesítéséhez a Scratch Addonsról.

### Hogyan tudok közreműködni a Scratch Addonsban?

Először is, köszönjük az érdeklődését a Scratch Addonshoz való hozzájárulásban. Értékeljük ezt is, valamint a későbbi közreműködéseit is.

Egy nyíltforráskódú projektként a közreműködés minden fajtájt szeretettel várjuk. Nincs is szüksége megkérdezésre, vagy egy bizonyos rangra. Mindenki szívesen látott. Még arra is van esély, hogy nem is vette észre, hogy már hozzá is járult a projekthez!

Mindenesetre vissza a lényeghez: több típusú módon is közre tud működni, és ezek közül néhány tényleg nagyon egyszerű.

- **Küldjön be kódot**

  Ha tud kódolni JavaScriptben, HTML5-ben, és CSS-ben, akkor néhány kódolással/programozással már hozzá tud járulni a projekthez. Kijavíthat hibákat, megbirkózhat kérésekkel, vagy létrehozhatja a saját kiegészítőjét.

  Ezek után szüksége van egy "pull requestre". Ezt meg tudja tenni a [repository] forkolásával (https://github.com/ScratchAddons/ScratchAddons/), majd a szükséges változtatások átcsinálásával, és végül egy "pull request" készítésével. Ha megvalósíthatóként lesz ítélve, akkor beolvasztjuk a főágba.

  Mi a közreműködés más vonatkozásaira is nyitottak vagyunk, mint a bővítmény. Megtekintheti az összes repositorynkat [a GitHub szervezetünk lapján](https://github.com/ScratchAddons), és segíthet felépíteni azokat.

- **Javasoljon egy ötletet**

  Van valamije, amiről azt gondolja, hogy jó kiegészítés lenne a Scratch Addonshoz? [Meséljen róla!](#i-think-you-missed-a-feature-what-can-i-do)

- **Hiba jelentése**

  Talált egy "bug"-ot az egyik kiegészítőnkben, a beállítások oldalon, vagy bárhol máshol a bővítményünkön? [Küldjön egy hibajelentést róla!](#what-can-i-do-if-i-find-a-problem)

- **Fordítás**

  Ha beszél másik nyelvet is folyékonyan, mint az angol, akkor segíthet a Scratch Addons fordításában/lokalizálásában a nyelvére. Elkezdheti [innen](/docs/localization/joining-the-localization-team).

- **Írjon dokumentációt**

  (Nagy) ismerője a Scratch Addonsnak? Ha így van, akkor bővítheti a dokumentációkat a saját írásával. A dokumentáció magába foglalhatja, hogy hogyan kell használni, vagy hogyan működik a bővítmény. Kérjük vegye fel a kapcsolatot a [Megvitatás lapunkon](https://github.com/ScratchAddons/ScratchAddons/discussions) további információkért.

- **Visszajelzés küldése**

  Visszajelezhet az űrlapunkon, ami a [visszajelzés oldalunkra](https://scratchaddons.com/feedback) van kitéve. A visszajelzése eltérő látásmódot adhat a bővítmény fejlesztésében, valamint mindenképpen segíthet olyan dolgokról tudomás szerzésében, amik figyelmet érdemelnek, vagy hibák, amiket így megtudunk javítani.

- **Hagyjon egy visszajelzést az áruházakban**

  Hagyhat egy áttekintést a Scratch Addonsról a [Chrome bővítmény oldalán](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco), vagy a [Firefox kiegészítő oldalán](https://addons.mozilla.org/hu/firefox/addon/scratch-messaging-extension/).

- **Csillagozza meg a repositorynkat**

  Alapjában a GitHub csillagozás olyan, mint a Scratch kedvenccé nyilvánítás. Meg tudja tenni ezt a [repositorynkra](https://github.com/ScratchAddons/ScratchAddons) látogatva, majd a "Star" gombra kattintva a jobb felső sarokban.

- **Terjessze a hírt**

  Bárkinek beszámolhat a Scratch Addonsról, mint például a barátainak, rokonainak, családtagjainak, vagy akár még a tanárának is, feltéve, ha szeretné. Csak arra kérünk, hogy [ne a Scratch honlapján tegye ezt](#can-i-tell-people-about-scratch-addons-on-scratch).

### Hogyan hozhatom létre a saját kiegészítőmet?

Olvasson többet arról, hogy hogyan kell készíteni egy ilyen Scratch Addons kiegészítőt [itt](/docs/develop/getting-started).

### Hogyan tehetem rá a nevemet a [közreműködők oldalra](/contributors)?

Kérjük olvassa el, és kövesse az utasításait [ennek az "issue"-nak](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}) azért a célért, hogy rajta legyen a neve az említett oldalon.

### Hogyan vehetem le a nevemet a  [közreműködők oldalról](/contributors)?

Ha nem szeretné, hogy rajta legyen a neve az oldalon, akkor kérjük mondja el ezt nekünk egy issue készítésével a [közreműködők reposítornkon](https://github.com/ScratchAddons/contributors/issues/), vagy egyéb formával a kapcsolattartásnak. Elnézést kérünk a kellemetlenségért.

### Mit tudok tenni, ha találtam egy problémát?

Mesélhet róla nekünk a lenti eljárások egyike által.

- Küldje el nekünk [a visszajelzőűrlapunkon](https://scratchaddons.com/hu/feedback) keresztül
- Hozzon létre egy issuet [a epositoryn](https://github.com/ScratchAddons/ScratchAddons/issues).
- Készítsen egy posztot a [vitalapunkon](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Számoljon be róla [a Discord szerverünkön](https://discord.gg/R5NBqwMjNc).

### Azt gondolom, hogy kihagytatok egy funkciót. Mit tehetek?

Ha azt gondolja, hogy hiányzik egy jellemző, vagy szeretne javasolni egy kiegészítőt a bővítményhez, vagy van valami jó ötlete, akkor mondja el nekünk [a fent említett módok egyikével](#what-can-i-do-if-i-find-a-problem).

### Hol tudok megbeszélni dolgokat a Scratch Addonsról?

Megteheti ezt [a Vitalapunkon](https://github.com/ScratchAddons/ScratchAddons/discussions), vagy[a Discord szerverünkön](https://discord.gg/R5NBqwMjNc). Ott megtudja vitatni a dolgokat, valamint az kérdéseit is fel tudja tenni az esetleges problémáival kapcsolatban.

### Azt gondolom, hogy a Scratch Addons lelassítja a Scratchet. Mit tehetek?

Próbálja meg kikapcsolni azokat a kiegészítőket, amikre nincs szüksége. Valamint tekintse át a kiegészítő-figyelmeztetéseket, hogy eldönthesse, hogy melyikeket kell kikapcsolni a teljesítmény növelése érdekében.

### Hogyan lehet aktiválni az easter egg kiegészítőket?

Az easter egg kiegészítők megjelenítéséhez csinálja végig a Konami Kódot (↑↑↓↓←→←→BA) a beállítások oldalon a billentyűzete segítségével. Utána meg fognak már jelenni a kívánt kiegészítők aktiválhatóan.

Néhány az easter-egg kiegészítőink közül: "Account Settings nagy kezdőbetűkkel" és a "Pontosvessző-hiba". Vessen egy pillantást [a kiegészítők lapra](/addons) egy teljes lista megtekintéséért.

### Több kérdésem van!

Ha több kérdése is van, amik válaszra várnak, akkor készítsen egy posztot [a Vitalapunkon](https://github.com/ScratchAddons/ScratchAddons/discussions), vagy küldjön egy üzenetet [a Discord szerverünkön](https://discord.gg/R5NBqwMjNc). Valaki majd biztos meg fog próbálni válaszolni.
