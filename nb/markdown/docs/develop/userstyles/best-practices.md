---
title: Beste praksis
description: Følg disse beste praksisene når du skriver eller gjennomgår brukerstiler.
---

Følg disse beste praksisene når du skriver eller gjennomgår brukerstiler.


<!-- TODO: ## Legg til støtte for mørk modus -->
<!-- Eksempler på referanse til CSS-variabler fra editor-dark-mode, dark-www og scratchr2 -->


## Internasjonalisering

### Vurder språk med lengre ord

Husk at i noen språk kan brukergrensesnittselementer som knapper være smalere eller bredere.

<!-- TODO: ### Støtte for høyre-til-venstre-språk (RTL) -->


## Styling eksisterende Scratch UI


### Unngå å målrette hasjede klasse navn

Scratch-prosjektredigereren inneholder vanligvis klassenavn som følger formatet `class_name_{hash}`. For eksempel, `green-flag_green-flag_1kiAo`.

Som hashene kan endre seg i fremtiden og kan variere mellom Scratch-gafler, bør du unngå å bruke dem i brukerstiler.

{{< admonition error >}}
```css
/* Ikke gjør dette: */
.green-flag_green-flag_1kiAo {
  visibility: hidden;
}
```
{{< /admonition >}}

{{< admonition success >}}
```css
/* Gjør dette i stedet: */
[class*="green-flag_green-flag_"] {
  visibility: hidden;
}
```
{{< /admonition >}}

### Unngå `!important` med mindre det er helt nødvendig

Hvis mulig, bruk [CSS spesifisitet](https://web.dev/learn/css/specificity/) funksjoner for å gjøre dine selektorer mer spesifikke, i stedet for å bruke `!important`.
<!-- Dette kan være mer detaljert -->


## Styling tillegg UI-elementer


### Begynn tilleggsdefinerte klassenavn med `sa-`

{{< admonition info >}}
Vi bruker alltid `kebab-case` når vi definerer våre egne klasse navn.
{{< /admonition >}}

Vi anbefaler at klasse navn definert av tillegget begynner med `sa-` for å unngå potensielle navnekonflikter med Scratch eller andre utvidelser.

Det anbefales også å inkludere tilleggs-IDen (eller deler av den) i klassenavnet.

<!-- TODO: ### forklar bruken av z-indeks i Scratch-redigereren og relaterte konsepter -->
