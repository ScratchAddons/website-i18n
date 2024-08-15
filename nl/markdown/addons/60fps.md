---
---

**Higher project framerate mode** is an addon that allows customization of the project's run speed to be faster than the default of 30 FPS. This has the effect of making the project appear to run smoother and at a faster rate relative to the custom FPS value; therefore, the default value of 60 FPS will essentially make the project run twice as fast.

Je kunt de functie snel in- of uitschakelen door `alt` ingedrukt te houden en op de groene vlag te klikken. The vlag zal dan blauw worden en een geel snel vooruitspoel-icoontje zal er overheen verschijnen, waarmee wordt laten zien dat het project sneller draait.

## Functies

- De functionaliteit van de addon wordt alleen ingeschakeld als de gebruiker hem inschakelt door `alt` ingedrukt te houden en op de groene vlag te klikken. De functionaliteit van de addon wordt elke keer dat de pagina wordt geopend/vernieuwd weer uitgeschakeld.
- De addon werkt zowel op de projectpagina als in de editor.
- De addon stelt standaard (wanneer ingeschakeld) de framerate van het project in op 60 FPS. Deze waarde kan worden veranderd in de instellingen van de addon in een geheel getal tussen 31 en 240.

## Instellingen

### Aangepaste FPS

Stelt de framerate-waarde van het project in als de addon is ingeschakeld.

## Toekomstplannen

- The addon might be marked as dangerous to curb projects that require this addon on the Scratch website. [#6860](https://github.com/ScratchAddons/ScratchAddons/issues/6860)
- Omdat je de `alt`-toets ingedrukt moet worden om de addon in te schakelen, is het niet compatibel met apparaten met een touchscreen. Een oplossing kan zijn om een contextmenu toe te voegen aan de groene vlag voor deze en andere addons. [#7230](https://github.com/ScratchAddons/ScratchAddons/issues/7230)

## Credit

Jeffalo created the original addon that only set the project player to 60 FPS. TheColaber added the custom FPS setting and various other bug fixes. The accessible green flag indicator was created by JoanRiosiPla before being tweaked by WorldLanguages.

## Changelog

- **v1.1.0** De **60FPS Player Mode** addon is gemaakt.
- **v1.3.0** De addon is nu standaard ingeschakeld voor alle gebruikers en heeft het label 'Aanbevolen' gekregen.
- **v1.7.0** Optie toegevoegd om de doel-FPS aan te passen, deze was hiervoor vergrendeld op 60.
- **v1.11.0** De addon is hernoemd naar **Alt+GreenFlag 60FPS player mode**, en er is een kort informatievenster toegevoegd. Er is een limiet ingesteld op de aangepaste FPS, die nu minimaal 31 en maximaal 240 kan zijn.
- **v1.13.0** De detectie van `Alt` + het klikken op de groene vlag is verbeterd. De addon kan nu dynamisch worden in- en uitgeschakeld.
- **v1.14.0** De addon heeft het label Project Player gekregen.
- **v1.18.0** De addon is hernoemd tot **60FPS project player mode**. De addon kan nu worden uitgevoerd in geëmbedde projecten.
- **v1.24.0** Bug fix: The addon no longer loses track of state when changing from project page to editor.
- **v1.26.0** Bug fix: The addon no longer causes variables to not visually update in some cases.
- **v1.30.0** The addon is no longer enabled by default for all users.
- **v1.34.0** A more accessible yellow fast-forward icon was added to the green flag indicator whenever the addon is toggled on. Information box was rewritten to clarify that most projects will not behave properly when addon is enabled.
- **v1.36.0** The addon was renamed to **Higher project framerate mode**. The addon's description and information box was rewritten for clarity.
- **v1.37.0** A second information box was added that explains issues with user devices' power saving mode.

## Trivia

- Although TurboWarp Addons does not have this addon, Turbowarp's advanced project settings allows you to customize the project's framerate in a similar way.
- Despite the addon's setting for customizing the FPS is limited from 31 to 240, the Scratch project player is perfectly fine with values both lower and higher than these limits! There are several ways to bypass this limit, as only the setting's input field sets the limit.
- Jeffalo added the addon because "its hecking cool"[^1]
- There is a method that allows Scratch projects to roughly detect a custom FPS, which may indicate that the addon is enabled.[^2]

## Gallery

{{< docs/stub-section >}}

## Related

{{< docs/stub-section >}}

[^1]: https://github.com/ScratchAddons/ScratchAddons/pull/383#issue-714126835
[^2]: https://en.scratch-wiki.info/wiki/Making_an_FPS_Counter