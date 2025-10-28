---
---

**Iskanje blokov** je dodatek, ki omogoči uporabnikom, da namesto iskanja blokov v paleti vnesejo ime bloka in ga vstavijo tja, kjer je miška, kar pospeši sestavljanje kode. Okno za iskanje odprete tako, da kliknete prostor za kodo s srednjim miškinim gumbom ali pritisnite `ctrl` + `presledek`. Nato lahko s tipkanjem poiščete blok in uporabite miško, da ga izberete.

## Zgodovina

Prvotno različico je naredil Griffpatch kot del razširitve Orodje za razvijalce. Med ločevanjem _Orodja za razvijalce_ na posamezne dodatke je nastal tudi ta dodatek.

## Delovanje dodatka

- Iščete lahko kateri koli blok. To vključuje "moje bloke", bloke iz razširitev, spremenljivke in sezname.
- Za še hitrejše vstavljanje lahko uporabite tipke s puščicami in Enter, da se premikate po rezultatih.
- Ko je rezultat označen, lahko pritisnite Tab, da dopolnite iskanje do tistega bloka.
- Vstavite lahko več gnezdenih blokov naenkrat, tako da vnesete nekaj takega kot "pojdi moja spremenljivka + 10 korakov".
- Pri matematičnih blokih se privzeto upošteva vrstni red operacij, vendar lahko uporabite oklepaje.
- Besedilo lahko vnesete v narekovajih, da preprečite iskalniku, da bi ga spremenil v bloke. Na primer, če bi radi, da figura reče "položaj x" namesto vrednosti spremenljivke `položaj x`, lahko napišete reci "položaj x".

## Nastavitve

### Velikost blokov v oknu za iskanje

Določi velikost posameznega bloka v oknu v slikovnih pikah.

### Širina okna za iskanje

Določi širino okna kot odstotek širine brskalnikovega okna.

### Največja višina okna za iskanje

Določi, kako visoko je lahko okno, preden se doda drsna vrstica, kot odstotek višine brskalnikovega okna.

## Načrti

- Spreminjanje velikosti okna z vlečenjem enega od vogalov v urejevalniku, ne da bi bilo treba spremeniti nastavitev.
- Zamenjava spremenljivk v nizih z narekovaji bi bila koristna v primerih, ko bi sicer bilo treba ročno sestaviti veliko blokov "združi".

## Znane napake

- Bloki v oknu tega dodatka ne upoštevajo nastavitev dodatka *Prilagoditev oblike blokov*.
- Algoritem za razvrščanje rezultatov iskanja še ni izpopolnjen, zato je iskani rezultat včasih skrit pod kupom slabših rezultatov.

## Zahvale

Tacodiva je naredila večji del današnjega dodatka. Veliko je prispeval tudi Griffpatch z odkrivanjem pomanjkljivosti v posodobljeni različici.

## Seznam sprememb

{{< docs/outdated-section >}}

- **v1.30.0** The insert blocks by name addon was created.
- **v1.31.0** The addon was completely overhauled, allowing for nesting blocks, adding autocomplete and changing how the blocks where shown in the popup.
- **v1.31.1** The algorithm for searching was altered and several bugs where fixed.

## Zanimivosti

- This was the first addon page written for the Addon Docs!
- Despite only recently becoming its own addon, the middle click popup is one of the oldest features of Scratch Addons being a part of dev tools sense the beginning.
- The original code for the popup was created before Scratch Addons even existed by Griffpatch in 2019.
- When Tacodiva overhauled the addon for v1.31.0, the code had almost 2,800 lines of code added and 149 commits!
- The name of the Git branch for the overhaul was `idk-what-im-doing`.
- Tacodiva was struggling to fix an issue so much, that despite only contributing two lines of CSS to fix the problem, CST1229 is in the addon's credits!

## Galerija

{{< docs/stub-section >}}

## Povezano

{{< docs/stub-section >}}
