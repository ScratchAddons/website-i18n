---
---

**Način hitrejšega osveževanja v predvajalniku projektov** je dodatek, ki omogoča povečanje hitrosti projektov.

Scratch zanke navadno ponavlja 30-krat na sekundo, zato je hitrost osveževanja zaslona 30 sličic na sekundo (FPS). Ta dodatek lahko poveča hitrost izvajanja kode in s tem tudi hitrost osveževanja. Posledično so animacije v projektih bolj gladke, ampak tudi hitrejše, sorazmerno z nastavljeno vrednostjo FPS: privzeta nastavitev 60 FPS v bistvu naredi projekte dvakrat hitrejše.

Nekateri projekti se povečani hitrosti osveževanja prilagodijo, na primer z [merjenjem časa med sličicami](https://en.wikipedia.org/wiki/Delta_timing), da animacije tečejo enako hitro in hkrati bolj gladko.

Hitrejše osveževanje lahko vključite ali izključite tako, da držite `alt` in kliknete zeleno zastavico. Zastavica se bo spremenila v modro z rumeno ikono za pospeševanje, ki pomeni, da projekt deluje hitreje.

## Delovanje dodatka

- Hitrejše osveževanje je vključeno samo, kadar ga uporabnik aktivira s klikom na zeleno zastavico med držanjem tipke `alt`. Samodejno se izključi vsakič, ko je stran znova naložena.
- Dodatek deluje na strani projekta in v urejevalniku.
- Dodatek (ko je aktiviran) s privzetimi nastavitvami nastavi hitrost osveževanja projekta na 60 FPS. To vrednost se da v nastavitvah dodatka spremeniti v katero koli celo število med 31 in 240.

## Nastavitve

### FPS po meri

Nastavi hitrost osveževanja projekta, ko je dodatek vključen.

## Načrti

- Dodatek bo morda dobil oznako, da je nevaren, saj ne želimo, da bi projekti na Scratchevi spletni strani zahtevali ta dodatek. [#6860](https://github.com/ScratchAddons/ScratchAddons/issues/6860)
- Ker dodatka ni mogoče vključiti brez tipke `alt`, ni združljiv z napravami z zaslonom na dotik. To bi lahko rešili tako, da bi zeleni zastavici dodali meni, v katerem bi bil ta dodatek in nekateri drugi. [#7230](https://github.com/ScratchAddons/ScratchAddons/issues/7230)

## Zahvale

Jeffalo - za prvotni dodatek, ki je nastavil predvajalnik projekta na 60 FPS.  
TheColaber - za nastavitev FPS po meri in razne popravke.  
JoanRiosiPla in WorldLanguages - za modro zastavico s puščicama.

## Seznam sprememb

- **v1.1.0** The **60FPS Player Mode** addon was created.
- **v1.3.0** The addon is now enabled by default for all users, and was given the Recommended tag.
- **v1.7.0** Option added to customize the target FPS, which was locked to 60 before.
- **v1.11.0** The addon was renamed to **Alt+GreenFlag 60FPS player mode**, and a brief information box was added. A limit was set on the custom FPS, which now ranges from 31 to 240.
- **v1.13.0** `Alt` + green flag click detection was improved. The addon can now be dynamically enabled and disabled.
- **v1.14.0** The addon was given the Project Player tag.
- **v1.18.0** The addon was renamed to **60FPS project player mode**. The addon can now run in project embeds.
- **v1.24.0** Bug fix: The addon no longer loses track of state when changing from project page to editor.
- **v1.26.0** Bug fix: The addon no longer causes variables to not visually update in some cases.
- **v1.30.0** The addon is no longer enabled by default for all users.
- **v1.34.0** A more accessible yellow fast-forward icon was added to the green flag indicator whenever the addon is toggled on. Information box was rewritten to clarify that most projects will not behave properly when addon is enabled.
- **v1.36.0** The addon was renamed to **Higher project framerate mode**. The addon's description and information box was rewritten for clarity.
- **v1.37.0** A second information box was added that explains issues with user devices' power saving mode.

## Zanimivosti

- Although TurboWarp Addons does not have this addon, Turbowarp's advanced project settings allows you to customize the project's framerate in a similar way.
- Despite the addon's setting for customizing the FPS is limited from 31 to 240, the Scratch project player is perfectly fine with values both lower and higher than these limits! There are several ways to bypass this limit, as only the setting's input field sets the limit.
- Jeffalo added the addon because "its hecking cool"[^1]
- There is a method that allows Scratch projects to roughly detect a custom FPS, which may indicate that the addon is enabled.[^2]

## Galerija

{{< docs/stub-section >}}

## Povezano

{{< docs/stub-section >}}

[^1]: https://github.com/ScratchAddons/ScratchAddons/pull/383#issue-714126835
[^2]: https://en.scratch-wiki.info/wiki/Making_an_FPS_Counter
