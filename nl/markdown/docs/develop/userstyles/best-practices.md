---
title: Optimale Praktijken
description: Volg deze optimale praktijken wanneer je userstyles aan het schrijven of beoordelen bent.
---

Volg deze optimale praktijken wanneer je userstyles aan het schrijven of beoordelen bent.


<!-- TODO: ## Addon dark mode support -->
<!-- Examples on referencing CSS variables from editor-dark-mode, dark-www and scratchr2 -->


## Internationalisatie

### Bedenk dat woorden soms lang kunnen zijn

Onthoud dat UI-elementen, zoals knoppen, smaller of breder kunnen zijn in sommige talen.

<!-- TODO: ### Supporting right-to-left languages (RTL) -->


## Stijlen toepassen op bestaande Scratch-UI


### Vermijd het richten op gehashte class-namen

De projecteditor van Scratch bevat doorgaans class-namen die het `class_name_{hash}`-formaat volgen. Bijvoorbeeld `green-flag_green-flag_1kiAo`.

Aangezien de hashes in de toekomst kunnen veranderen en kunnen verschillen tussen forks van Scratch moet je het gebruik ervan vermijden in userstyles.

{{< admonition error >}}
```css
/* Doe dit NIET: */
.green-flag_green-flag_1kiAo {
  visibility: hidden;
}
```
{{< /admonition >}}

{{< admonition success >}}
```css
/* Doe in plaats daarvan dit: */
[class*="green-flag_green-flag_"] {
  visibility: hidden;
}
```
{{< /admonition >}}

### Vermijd het gebruik van `!important` tenzij strikt noodzakelijk

Gebruik [CSS specificity](https://web.dev/learn/css/specificity/)-functies indien mogelijk om je selectors specifieker te maker, i.p.v. `!important` te gebruiken.
<!-- This could be more detailed -->


## Stijlen toepassen op UI-elementen van addons


### Laat class-namen die door addons zijn gedefinieerd beginnen met `sa-`

{{< admonition info >}}
We gebruiken altijd `kebab-case` wanneer we onze eigen class-namen definiëren.
{{< /admonition >}}

We raden aan dat je class-namen die door addons zijn gedefinieerd laat beginnen met `sa-` om potentiële botsingen met Scratch of andere extensies te voorkomen.

Het wordt ook aangeraden om de addon-ID (of een deel ervan) in de class-naam te includeren.

<!-- TODO: ### explain usage of z-index in the Scratch editor and related concepts -->
