---
layout: post
title: Février & mars 2024 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport du mois pour les mois de février et mars 2024

# I. Introduction

<br>

Sur ces 2 derniers mois, une attention toute particulière a été portée sur le frontend (interface web).

L'amélioration de l'interface est nécessaire, ainsi que son uniformisation afin que l'utilisateur puisse l'utiliser dans de bonnes conditions, que le code soit le plus simple possible afin que les corrections puissent se faire aisément !

On va détailler tout ça.

<br>

# II. Evènements du projet

<br>

# II.1. Conférence en mai à Lyon (France) pour les JDLL

La 25e édition des [JdLL](https://www.jdll.org) se déroulera les 25 et 26 mai 2024 à Lyon.

Pour l'occasion, j'ai soumis une conférence intitulée **Concevoir un logiciel libre (FusionSuite) depuis 3 ans sans être encore releasée : parcours du combattant**, et bien figurez-vous qu'elle a été acceptée. Je serai donc le 25 mai pour donner la conférence à Lyon, je vous donnerai plus d'informations le mois prochain.


<br>

# III. Développement

<br>

## III.1. Backend

<br>

### III.1.a Corrections diverses 

Le focus étant porté sur le frontend, le backend a reçu quelques corrections, identifiées grâce à l'utilisation intensive du frontend.

Les corrections sont manuelles et pas encore dans le dépôt, car elles nécessitent d'ajouter des tests.

Malgré les plus de 3 000 tests, il reste des cas que je n'avais pas prévus, je reste humain :D

Il risque d'y avoir quelques autres corrections en avril sur le backend avec l'ajout des nombreux tests du frontend.

<br>

## III.2 Frontend

<br>

### III.2.a Les champs

Une réflexion sur les différents type de champs (string, integer, liste déroulante, booléen...) a été menée début février dans le but de gérer toutes les configurations de ces champs et d'avoir une **uniformisation** de ces champs dans toute l'application.

Un composant pour chaque type a été codées, puis intégré dans toutes les pages (création et édition des types, propriétés, items, et même la page de login).

Le résultat est vraiment au top. Il reste encore du travail sur ces champs, notamment la partie test End-to-End, avec [Cypress](https://www.cypress.io/), qui avance bien mais n'est pas encore terminée. Je vais essayer de finir ces tests pour fin avril et de pousser ça dans le dépôt de code.


Voici à quoi ça correspond :

*En mode visualisation*
<img src="/assets/img/frontend_fields_visualisation.png" width="752">

*En mode édition*
<img src="/assets/img/frontend_fields_edition.png" width="762">


<br>

### III.2.b Boutons & en-têtes de page

Ah les boutons ! 

Pareil que pour les champs, il y a eu un besoin d'uniformiser les boutons et d'avoir leur disposition à peu près toujours pareille.

Les en-têtes de pages ont également été revus afin d'avoir les informations utiles et facilement lisibles. Je ne suis pas encore tout à fait satisfait, donc il y aura encore des modifications.

Ci-après, quelques captures d'écran de ces boutons et en-têtes.


*Liste d'items*
<img src="/assets/img/buttons_list.png" width="1300">
<br>
<br>
*Page de création d'item*
<img src="/assets/img/buttons_newitem.png" width="1300">
<br>
<br>
*Page de visualisation / modification d'item*
<img src="/assets/img/buttons_item_detail.png" width="1300">
<br>
<br>
*Page de visualisation / modification d'item, mais avec l'item en soft delete*
<img src="/assets/img/buttons_softdelete.png" width="1300">


<br>


# IV. Conclusion

L'interface avance bien, je devrais pouvoir écrire la documentation d'utilisation de FusionSuite d'ici 2 ou 3 mois \o/

Ca commence à ressembler à une application finalisée !

**David Durieux - Leader du projet FusionSuite**
