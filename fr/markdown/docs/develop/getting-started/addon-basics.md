---
title: La Base d'un Addon
---

## Qu'est-ce que est vraiment un addon?
Vraiment, un addon/extension n'est pas vraiment plus qu'un script d'utilisateur, un utilisateur de style ou une combinaison des deux. Si un des sont en relation, alors nous prenons ceux-ci et le relions au même addons, sur un simple nom. Par example, le "Boite à Outils de Scratch 3" addon/extension a un script utilisateur en charge d'ajouter un un boite dans l'éditeur et un script de style est d'ajouter le CSS à cette boite.

## Qu'est-ce qu'un script d'utilisateur?
Un script utilisateur est un morceau de code JavaScript qui s'exécute avec un onglet Scratch. Vous pouvez spécifier où ce script utilisateur s'exécutera, par exemple, uniquement les pages de projet. Les scripts utilisateur sont similaires aux scripts de contenu sur les extensions de navigateur, et si vous avez déjà utilisé un gestionnaire de scripts utilisateur, vous remarquerez qu'ils sont fondamentalement les mêmes.
Les scripts utilisateur sont utiles pour modifier le comportement du site Web Scratch, par exemple, en ajoutant ou en supprimant des boutons dans la barre de navigation.

## Qu'est-ce qu'un style d'utilisateur?
Un style d'utilisateur est similaire à un script utilisateur ; vous pouvez également leur spécifier des modèles d'URL. Cependant, les styles d'utilisateur injectent du CSS au lieu de JavaScript. Ils sont souvent utilisés avec les scripts utilisateur pour styliser les éléments ajoutés par eux, mais ils peuvent également être utilisés pour styliser les éléments Scratch natifs. Lorsque c'est le cas, nous les appelons généralement "thèmes".

## Conceptuellement, que devrait être un addon ?
Vous vous demandez peut-être s'il est préférable de créer un nouvel addon ou d'en modifier un existant.
Si 2 addons partagent certains d'entre eux, ils devraient probablement être fusionnés.
- Les deux ont besoin, ou n'ont pas besoin, d'autorisations qui nécessitent une interaction de l'utilisateur (comme les notifications).
- Cela fait beaucoup de code.
- L'utilisateur s'attendrait à ce que cet addon offre les deux fonctionnalités.
 

 
 
 
 
 
- S'ils étaient séparés, ils interféreraient les uns avec les autres. 

Souvenez vous que des addons/entensions sont customisable par l'utilisateur - ajouter une nouvelle fonctionalité n'affectera pas les autres, par contre nous le faisons intentionnellement pour le faire.