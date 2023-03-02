---
title: Een Addon Maken
---
Vereiste software: teksteditor, Chrome. 
Wanneer mogelijk, schakel de Scratch Addons-extensie die je hebt gedownload van de store uit om problemen te voorkomen.

## Stap 1: Lees over [de addon-basis](/docs/develop/getting-started/addon-basics/)
Lees dat artikel om de termen te weten.

## Stap 2: Vertak/kopieer het [archief](https://github.com/ScratchAddons/ScratchAddons)
Volg [deze instructies](/docs/getting-started/installing/#from-source) om lokaal de broncode te downloaden.

## Stap 3: Laad de extensie in Chrome
*Opmerking: Chrome is aanbevolen voor het werken aan addons. Addons zouden daarentegen wel op Firefox en Edge moeten werken.* 
Nu dat je de extensie in je bestandssysteem hebt, ga naar `chrome://extensions` en schakel "ontwikkelaarmodus" in. 
Klik op "uitgepakte extensie laden", selecteer dan de map met Scratch Addons. Als je hiermee problemen hebt, zorg ervoor dat je de map selecteert waar `manifest.json` zich bevindt. 
Dat is alles, je hebt de extensie geladen! Het zou er ongeveer zo uit moeten zien: 
![afbeelding](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)  
Opmerking: je kunt de "errors" veilig negeren. Dat is gewoon een waarschuwing voor een onherkende manifest-key die Firefox nodig heeft.

## Stap 4: Waar gaat je addon over?
Nu komt het leuke!  
Wat gaat je addon doen? Bedenk een zelfbeschrijvende addon-ID (geen spaties of speciale tekens, behalve streepjes, en het liefst in het Engels).  
Snap je het?

## Stap 5: Maak de map voor de addon
Ga in een bestandenverkenner naar de map met Scratch Addons. Ga naar de `addons`-map.  
Maak dan een nieuwe map met je geweldige addon-ID als naam.

## Stap 6: Voeg een addon-manifest toe
De addon-manifest vertelt Scratch Addons over hoe je addon werkt. Doe dit goed om veel hoofdpijn te voorkomen.  
Maak een bestand genaamd `addon.json` in de map die je net hebt gemaakt.  
Dit is een basis die je kunt gebruiken om te beginnen met programmeren, zorg ervoor dat je het verandert in de toekomst:
```json
{
  "name": "Geweldige plaatsvervanger voor addonnaam",
  "description": "Hallo Wereld! Het zou heel slim zijn om deze plaatsvervangende tekst te vervangen met een beschrijving.",
  "tags": ["community"],
  "enabledByDefault": false
}
```
Voor meer informatie over wat je kunt verklaren in de manifest, check [dit artikel](/docs/reference/addon-manifest/).


## Stap 7: Vertel Scratch Addons wat het ID van je addon is
Scratch Addons kan niet uit zichzelf nieuwe mappen vinden, dus dan zul je de naam aan een speciaal bestand toe moeten voegen.  
Ga naar `scratchAddonsFolder/addons/addons.json` en voeg het ID van je addon toe aan de array.

## Stap 8: Hallo wereld
Op dit moment doet je addon niets, dus nu is een goed moment om te controleren of alles wat we net hebben gemaakt werkt.  
Ga naar `chrome://extensions` en ververs Scratch Addons door op het ververspictogram op zijn kaart te klikken.  
Rechterklik nu op het Scratch Addons-pictogram, en klik op "opties".  
Je zou je addon in de lijst moeten zien staan! Als je het ziet, zet het aan, en verander de instellingen die je hebt.

## Stap 9: Het leuke, code!
*Voordat je verdergaat, zorg ervoor dat je het wiki-artikel in stap 1 hebt gelezen.*

Hier komt het leukste deel: maak je eigen JS- of CSS-bestanden!  
Pro-tip: nadat je veranderingen maakt aan je addon, ververs dan de Scratch Addons-extensie zoals in stap 8.

Afhankelijk van wat je wilt dat je addon doet, zou je deze wikipagina's moeten bekijken:
- [Userscripts](/docs/develop/userscripts)
- [Userstyles](/docs/develop/userstyles)

## Stap 10: Maak je addon aanpasbaar
Als je wilt, kun je je addon aanpasbaar maken!  
Gebruikers van je addon kunnen instellingen in- of uitschakelen, getallen invoeren, en meer!  
Om te beginnen, bekijk [hoe je instellingen in de addon-manifest verklaart](/docs/reference/addon-manifest/#settings-object).  
Ga dan naar de [addon.settings-documentatie](/docs/reference/addon-api/addon.settings) om te leren hoe je toegang krijgt tot de keuzes van gebruikers van userscripts.

## Stap 11: Voordat je je addon publiceert
Nu dat je addon werkt, laten we ervoor zorgen dat we het aan de addonbibliotheek kunnen toevoegen.  
Zorg ervoor dat de manifest van je addon geschikt is, [hier meer informatie](/docs/reference/addon-manifest). Let goed op de naam, beschrijving en tags van je addon. Stel `"enabledByDefault"` in op `false` of verwijder het.  
Zorg ervoor dat je addon geen andere addons verhindert.  
Zorg ervoor dat je code begrijpbaar is; het hebben van onnodige opmerkingen is beter dan niets.

## Stap 12: Maak een pull-verzoek!
Volg de stappen in onze [bijdragingsrichtlijnen](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md). Simpelweg: vertak het archief als je dat nog niet hebt gedaan, commit je nieuwe addon en verstuur een pull-verzoek!  
Onthoud dat we je kunnen vragen wat veranderingen te maken, we accepteren je addon echter waarschijnlijk wel als het minimaal geschikt is.
