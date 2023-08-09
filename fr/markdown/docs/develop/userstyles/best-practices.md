---
title: Meilleures pratiques
description: Suivez ces bonnes pratiques lors de la rédaction ou de la révision des styles utilisateur.
---

Suivez ces bonnes pratiques lors de la rédaction ou de la révision des styles utilisateur.


<!-- A FAIRE : ## Support du mode sombre pour les addons -->
<!-- Exemples sur le référencement des variables CSS de editor-dark-mode, dark-www et scratchr2 -->


## Internationalisation

### Pensez aux langues avec des mots plus longs

N'oubliez pas que dans certaines langues, les éléments de l'interface utilisateur tels que les boutons peuvent être plus ou moins larges.

<!-- A FAIRE : ### Prendre en charge les langues de droite à gauche (RTL) -->


## Styliser l'interface utilisateur existante de Scratch


### Éviter de cibler les noms de classe hachés

L'éditeur de projet Scratch contient généralement des noms de classes qui suivent le format `class_name_{hash}`, comme par exemple, `green-flag_green-flag_1kiAo`.

Comme les hachages sont susceptibles de changer à l'avenir et qu'ils peuvent différer d'une version à l'autre de Scratch, vous devriez éviter de les utiliser dans les styles utilisateur.

{{< admonition error >}}
```css
/* Ne faites pas cela : */
.green-flag_green-flag_1kiAo {
  visibility: hidden;
}
```
{{< /admonition >}}

{{< admonition success >}}
```css
/* Faites plutôt ceci : */
[class*="green-flag_green-flag_"] {
  visibility: hidden;
}
```
{{< /admonition >}}

### Éviter `!important` sauf en cas d'absolue nécessité

Si possible, utilisez les fonctionnalités [CSS specificity] (https://web.dev/learn/css/specificity/) pour rendre vos sélecteurs plus spécifiques, au lieu d'utiliser `!important`.
<!-- Cela pourrait être plus détaillé -->


## Styliser les éléments de l'interface utilisateur de l'addon


### Débuter les noms des classes définies par les addons par `sa-`

{{< admonition info >}}
Nous utilisons toujours `kebab-case` lorsque nous définissons nos propres noms de classe.
{{< /admonition >}}

Nous recommandons que les noms des classes définies par les addons commencent par `sa-` afin d'éviter de potentiels conflits de noms avec Scratch ou d'autres extensions.

Il est également recommandé d'inclure l'identifiant de l'addon (ou une partie de celui-ci) dans le nom de la classe.

<!-- A FAIRE : ### Expliquer l'utilisation de z-index dans l'éditeur Scratch et les concepts associés -->
