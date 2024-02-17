---
title: Addon Basics
---

## Hva er egentlig en tillegg?
Faktisk er en tilleggsfunksjon ikke mye mer enn et brukerskript, en brukerstil eller en kombinasjon av begge deler. Hvis noen av disse er relatert, gjør vi dem til en del av samme tilleggsfunksjon, under ett navn. For eksempel har tilleggsfunksjonen "Scratch 3 Developer Tools" et brukerskript som er ansvarlig for å legge til en søkeboks i redigeringsverktøyet, og en brukerstil som legger til CSS i den boksen.

## Hva er en brukerskript?
Et brukerskript er en bit JavaScript-kode som kjører sammen med en Scratch-fane. Du kan spesifisere hvor dette brukerskriptet skal kjøre, for eksempel bare på prosjektsider. Brukerskript er lignende innholdsskript på nettleserutvidelser, og hvis du noen gang har brukt en brukerskriptbehandler, vil du legge merke til at disse er omtrent det samme.
Brukerskript er nyttige for å endre oppførselen til Scratch-nettstedet, for eksempel å legge til eller fjerne knapper fra navigasjonslinjen.

## Hva er en brukerstil?
En brukerstil er lik en brukerskript; du kan også spesifisere URL-mønstre for dem. Imidlertid injiserer brukerstiler CSS i stedet for JavaScript. De brukes ofte sammen med brukerskript for å style elementer som er lagt til av dem, men de kan også brukes til å style native Scratch-elementer. Når det er tilfelle, kaller vi dem vanligvis "temaer".

## Konseptuelt, hva bør være en tilleggsfunksjon?
Du lurer kanskje på om det er en bedre idé å lage en ny tillegg, eller endre en eksisterende. 
Hvis 2 tillegg deler noen av disse, bør de sannsynligvis slås sammen.
- Både trenger, eller trenger ikke, tillatelser som krever brukerinteraksjon (som varsler).
- De deler mye kode.
- Brukeren ville forvente at tillegget tilbyr begge funksjonene.
- Hvis de blir separert, vil de forstyrre hverandre.

Husk at tillegg kan tilpasses av brukeren - å legge til ny funksjonalitet påvirker ikke gamle brukere av tillegget, med mindre vi med vilje gjør det.