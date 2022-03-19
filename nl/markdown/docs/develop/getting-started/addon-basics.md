---
title: Addon-Basis
---

## Wat is eigenlijk een addon?
Eigenlijk is een addon niet meer dan een userscript, een userstyle, of een combinatie ervan. Als ze relevant zijn, zetten we ze in dezelfde addon, onder een enkele naam. De "Scratch 3-Ontwikkelaarstools"-addon heeft bijvoorbeeld een userscript voor het toevoegen van een zoekbalk aan de editor, en een userstyle die CSS aan die balk toevoegt.

## Wat is een userscript?
Een userscript is een stukje JavaScript-code die samen met een Scratchtabblad uitvoert. Je kunt kiezen waar die userscript zich uitvoert, bijvoorbeeld, alleen projectpagina's. Userscripts zijn vergelijkbaar met inhoudscripts op browserextensies, en als je ooit een userscript-manager hebt gebruikt zul je zien dat ze praktisch hetzelfde zijn. 
Userscripts zijn handig om het gedrag van de Scratchwebsite aan te passen, bijvoorbeeld, knoppen toevoegen of verwijderen van de navigatiebalk.

## Wat is een userstyle?
Een userstyle is vergelijkbaar met een userscript; je kunt ook URL-patronen voor ze kiezen. Echter, userstyles injecteren CSS in plaats van JavaScript. Ze worden vaak met userscripts gebruikt om de elementen ervan een stijl te geven, maar dat kan ook met natieve Scratchelementen. Als dat het geval is, noemen we die meestal "thema's".

## Wat zou conceptueel een addon moeten zijn?
Je zou kunnen twijfelen of het beter is om een nieuwe addon te maken, of een bestaande addon te veranderen. 
Als 2 addons enkele van deze delen, zouden ze waarschijnlijk samengevoegd moeten worden.
- Ze hebben beiden, of niet, toestemmingen nodig die gebruikersinteractie nodig hebben (zoals notificaties).
- Ze delen veel code.
- De gebruiker zou verwachten dat de addon beide functies aanbiedt.
- Als ze gescheiden worden, zouden ze problemen veroorzaken.

Onthoud dat addons aanpasbaar zijn door de gebruiker - nieuwe functionaliteit toevoegen beïnvloedt oude gebruikers van de addon niet, behalve als we dit opzettelijk doen.