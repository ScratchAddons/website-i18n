---
title: La Base d'un Addon
---

## Qu'est-ce que est vraiment un addon?
En fait, un addon n'est pas plus qu'un script utilisateur, un style utilisateur ou une combinaison des deux. Si certains d'entre eux sont liés, nous les intégrons au même module complémentaire, sous un seul nom. Par exemple, l'addon "Outils de Développement pour Scratch 3" a un script utilisateur chargé d'ajouter une boîte de recherche à l'éditeur et un style utilisateur qui ajoute du CSS à cette boîte.

## Qu'est-ce qu'un script utilisateur?
Un script utilisateur est un morceau de code JavaScript qui s'exécute avec un onglet Scratch. Vous pouvez spécifier où ce script utilisateur s'exécutera, par exemple, uniquement les pages de projet. Les scripts utilisateur sont similaires aux scripts de contenu sur les extensions de navigateur, et si vous avez déjà utilisé un gestionnaire de scripts utilisateur, vous remarquerez qu'ils sont fondamentalement les mêmes.
Les scripts utilisateur sont utiles pour modifier le comportement du site Web Scratch, par exemple, en ajoutant ou en supprimant des boutons dans la barre de navigation.

## Qu'est-ce qu'un style utilisateur?
Un style utilisateur est similaire à un script utilisateur ; vous pouvez également leur spécifier des modèles d'URL. Cependant, les styles utilisateur injectent du CSS au lieu du JavaScript. Ils sont souvent utilisés avec les scripts utilisateur pour styliser les éléments rajoutés, mais ils peuvent également être utilisés pour styliser les éléments Scratch natifs. Lorsque c'est le cas, nous les appelons généralement "thèmes".

## Conceptuellement, que devrait être un addon ?
Vous vous demandez peut-être s'il est préférable de créer un nouvel addon ou d'en modifier un existant.
Si 2 addons partagent certains d'entre eux, ils devraient probablement être fusionnés.
- Les deux ont besoin, ou n'ont pas besoin, d'autorisations qui nécessitent une interaction de l'utilisateur (comme les notifications).
- Cela fait beaucoup de code.
- L'utilisateur s'attendrait à ce que cet addon offre les deux fonctionnalités.
 

 
 
 
 
 
- S'ils étaient séparés, ils interféreraient les uns avec les autres. 

Souvenez vous que des addons/entensions sont customisable par l'utilisateur - ajouter une nouvelle fonctionalité n'affectera pas les autres, par contre nous le faisons intentionnellement pour le faire.