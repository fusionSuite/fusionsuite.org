---
layout: post
title: Juillet 2022 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport du mois de juillet 2022, et pour les mois depuis mars.

# I. Introduction

<br>

## I.1. Pause forcée de plusieurs semaines

Je n'ai pas écrit de rapport du mois depuis le dernier écrit en avril à cause de plusieurs raisons :

* en avril, je me suis fait mal au dos et j'ai eu très mal pendant 7 semaines, il m'était donc impossible de coder le projet pendant ce laps de temps
* pas vraiment de nouveautés à communiquer

<br>

## I.2. Campagne de tests repoussée

J'avais défini les premiers tests utilisateurs en mai, mais avec le délai du code, on repousse à fin d'année.

<br>

## I.3. Nouveau développeur chez Probesys

Comme mentionné sur le dernier rapport du mois, notre partenaire *Probesys* cherchait quelqu'un pour développer sur le projet.

Bonne nouvelle, ils ont trouvé et il se nomme Marien.
Marien travaille depuis plusieurs années sur [flus](https://flus.fr/).

Bienvenue à lui au sein du projet et il a commencé à nous aider depuis juin.

<br>

## I.4. Planning


Suite à des discussions entre l'équipe et les partenaires en juillet, on a décidé d'un nouveau planning (qui peut encore bouger) :

* première campagne de tests en fin d'année (tickets et peut être l'inventaire FusionInventory)
* première version stable début 2023


# II. Développement

<br>

## II.1. Backend

<br>

### II.1.a. Introduction

Plusieurs parties sont finalisées ou en revue de code pour intégration (ça sera fait dans quelques jours).

Je vais expliquer chaque partie, car c'est la base de FusionSuite et c'est important.

Tous les codes et fonctionnalités sont ajoutés avec beaucoup de tests, pour tester ce qui fonctionne et tester ce qui ne doit pas fonctionner ; le but est d'avoir pensé au plus de cas possibles.

Actuellement, on a un peu plus de 1700 tests (et énormément d'insertions, mais pas quantifiées), et l'exécution prend moins d'une minute :D

<br>

### II.1.b Propriétés

Dans FusionSuite, vous pourrez créer des types (ordinateur portable, ticket, smartphone, switch, routeur, voiture...).

Pour ces types, vous aurez certainement besoin de gérer des propriétés, par exemple *numéro de série*, *date d'achat*, *en location?*...

Donc vous allez pouvoir créer des propriétés et les attacher au type.

Pour les propriétés, plusieurs champs et types de propriétés sont possibles.

Pour les champs, il y a :

* name
* internalname
* valuetype : *boolean*, *date*, *datetime*, *decimal*, *integer*, *itemlink*, *itemlinks*, *list*, *number*, *password*, *passwordhash*, *propertylink*, *string*, *text*, *time*, *typelink*, *typelinks*
* regexformat
* unit : l'unité de la valeur, par exemple secondes, Kio, Gio...
* default : la valeur par défaut
* description
* setcurrentdate : ne fonctionne que pour les *valuetype*: *date*, *datetime*, *time*
* canbenull

Comme vous pouvez le voir, les propriétés peuvent être utilisés pour de nombreux cas.

<br>

### II.1.c id_bytype

Notre base de données a une table où sont stockés tous les items.

Il peut y avoir des tickets, des ordinateurs portables... dans la même table.

Pour les performances, le partitionnement va aider à garder FusionSuite performant (ça sera documenté plus tard).

Mais le problème c'est qu'un ticket peut avoir des ID manquants entre 2 tickets, car l'id peut être utilisé par un ordinateur portable ou un autre item.

Pour ça, on garde l'id primaire de l'item et on ajoute un nouveau id, nommé id_bytype et qui sera incrémenté par type.

Ainsi, pour deux tickets consécutifs, le second sera toujours `+1` comparé au premier ticket.

<br>

### II.1.d Items arborescents

Pour plusieurs besoins, comme les organisations, catégories de tickets... on a besoin d'avoir des items organisés en arborescence.

Après un temps de recherche, on a décidé d'utiliser la méthode `Materialized paths` qui permet d'être performant dans les requêtes.

Dans la configuration des types, deux nouveaux champs sont disponibles :

 * tree
 * allowtreemultipleroots

Les deux sont des booléens pour dire oui ou non.

Le champ `allowtreemultipleroots` permet d'avoir une arborescence en arbres (enfin dans ce cas des arbres) qui peuvent avoir plusieurs racines. Par exemple, on en a souvent dans les catégories de tickets (plusieurs premier niveau).

Puis, dans les items, vous définissez l'id parent quand vous créez l'item et il va générer le treepath dans la base de données.

On a nommé le champ `treepath` dans la base de données et il est possible d'avoir un maximum de 63 niveaux dans l'arborescence.


<br>

### II.1.e Organisations et utilisateurs

On gère les items par rapport à des organisations.

Les organisations sont des types arborescents, avec une seule racine. Tous les items, types et propriétés ont besoin d'être définis sur une organisation et peut être taguée comme visible sur les sous-organisations.

Les utilisateurs sont également définis sur une organisation et ont un paramètre de visibilité de sous-organisation.

Les organisations et les utilisateurs sont, en fait, des items et définis par un type. Ainsi, c'est comme pour les autres items et vous pouvez attacher les propriétés que vous voulez sur ces types. Par exemple, vous pouvez définir un utilisateur responsable sur une organisation, une adresse...

<br>

### II.1.f. Prochaines fonctionnalités

Les prochaines fonctionnalités qui vont être ajoutées sont :

* gestion des droits : gérer afficher, créer, mettre à jour, supprimer et purger les items et chaque propriété
* historique de tous les changements
* audit : stockage de toutes les connexions, création et suppression des données

## II.2 Frontend

<br>

### II.2.a Interface de tickets désign-ée

Marien (de Probesys), a conçu une interface pour les tickets. Ce n'est pas la version finale, car ça va évoluer, mais ça donne une vision de ce que l'on souhaite : simple et efficace dans la création et la mise à jour...


<img src="/assets/img/Screenshot_2022-07-04_at_11-13-19_Ticket.png" width="1300">



<br>

### II.2.b Changement de frameworks

Après plusieurs discussions avec Marien et le POC qu'il a crée, on a décidé d'abandonner Ionic/Angular car jugé trop lourd.

On utilise désormais principalement *Angular*. Le travail fait précédemment va pouvoir être utilisé, car le code utilisait angular.


<br>

# V. Conclusion

Beaucoup de changements, et le travail continu.

Le rapport du mois prochain sera disponible début septembre sur le travail effectué en août.


**David Durieux - Leader du projet FusionSuite**
