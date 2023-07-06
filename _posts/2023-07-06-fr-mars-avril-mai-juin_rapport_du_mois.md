---
layout: post
title: Mars / avril / mai / juin 2023 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport des mois de mars, avril, mai et juin 2023.

# I. Introduction

<br>

Il n'y a pas eu de rapport du mois depuis 4 mois, pas que le projet n'avance pas, au contraire, mais ces derniers mois ont été extrêmement chargés pour moi (personnel et professionnel).

Sans plus tarder, nous allons commencer ce rapport avec pas mal d'informations.

<br>

# II. Evénements du projet

<br>

# II.1. Live coding sur Twitch

Plusieurs fois par semaine (mais pas forcément toutes les semaines, je vous l'ai dit, c'est bien chargé quand même :p), je continue de streamer du live coding du projet sur ma chaîne [Twitch](https://www.twitch.tv/ddurieux).

<img src="/assets/img/twitch_01.png" width="600">


N'hésitez pas à passer faire coucou et pour vous montrer le travail avancé !

<br>

# II.2. Tests en cours

Le portail, encore en conception, évolue pas mal.

Des tests exclusifs avec notre partenaire [DCS EASYWARE](https://www.dcsit-group.com/) sont actuellement en cours.

Cela porte sur :

 * configuration de la gestion des changements
 * premiers retours de l'interface, pour commencer à adapter / corriger certaines parties
 * utilisation du backend et de la documentation de l'[API REST](https://fusionsuite.org/documentation/restapi/) pour FusionSoftwares (voir le point II.4)

<br>

# II.3. Tests communautaires

Le portail est donc encore en conception/développement, il avance quand même pas mal, mais est encore vraiment tôt pour vous le faire tester.

Une première session sera organisée pour ceux qui souhaitent au mois d'août. On en reparlera dans le rapport début août pour les inscriptions.

Une version toute prête sur nos serveurs vous sera attribuée personnellement.
Une version commune avec les autres testeurs vous sera mise à disposition.

Le but de ces tests est de découvrir l'interface / l'utilisation, et de nous faire un/des retours sur les difficultés, les améliorations possibles... afin de rendre FusionSuite utilisable au mieux **pour sa première release, toujours prévu fin de cette année**.


<br>

# II.4. FusionSoftwares

Le site n'est pas encore lancé (ni même fait le logo), donc je vais en parler ici même.

Le projet FusionSoftwares, présenté en janvier ne devait débuter qu'au mois d'août.

Sous l'impulsion de notre partenaire [DCS EASYWARE](https://www.dcsit-group.com/), des ressources de notre partenaire ont été allouées à ce projet et il a déjà pas mal avancé.

Pour rappel, **FusionSoftwares** a pour but de collecter les logiciels, versions de logiciels, CVE... et de centraliser les données.

Ensuite les utilisateurs, scripts... viendront chercher ces données et pourront les traiter. Dans notre cas, un script dans FusionSuite viendra tagger les logiciels remontés par FusionInventory afin que les techniciens / administrateurs puissent voir les logiciels obsolètes et/ou contenants des failles sur leur parc.

<br>

# III. Développement

<br>

## III.1. Backend

<br>

### III.1.a Modification des pré-requis

PHP 8.0 va être obsolète le 26 novembre prochain, les versions requises seront PHP 8.1 ou 8.2. 

La documentation a été mise à jour, les pré-requis dans le backend également, ainsi que les tests.

<br>

### III.1.b Amélioration de la documentation de l'API REST

La documentation de l'API (à destination des développeurs), a été améliorée pour être plus lisible (modification des styles).

Il reste des parties à améliorer, à restructurer, travail qui sera effectué prochainement.


<br>

### III.1.c Amélioration de la qualité du code

Une branche est en cours afin de faire passer le code au niveau maximal de [PHPStan](https://phpstan.org/).

Ceci permet de garantir un meilleur code et de prévenir plusieurs bugs.


Cette branche devrait être finalisée en septembre (il reste 800 problèmes actuellement sur les 2000 identifiés au début).


<br>

### III.1.d Amélioration des propriétés d'items

Plusieurs améliorations des propriétés d'items ont été effectuées :

* amélioration et correction des valeurs par défaut pour les *itemlinks* et *typelinks*
* ajout des *allowedtypes* pour les *itemlink* et *itemlinks*, qui permet de définir les types d'items autorisés dans ces propriétés
* modification des *internalname* où la génération utilise désormais un *uniqid* afin d'éviter les collisions et donc les erreurs


<br>

### III.1.e Gestion des paramètres d'affichage

Des endpoints sur l'API REST ont été ajoutés afin de pouvoir stocker et gérer l'affichage dans le frontend : 

* gestion des menus
* gestion des menus personnalisés
* gestion des panels (dans la page l'affichage/modification des items)



<br>

### III.1.f Workflows / FusionInventory

Les spécifications ont été faites, cela a pris bien plus de temps que prévu, mais est une partie essentielle de FusionSuite.

Le code a commencé en ce début juillet et devrait être finalisé fin du mois de juillet.

Ces workflows sont composés comme suit : 

* *trigger* : ce sont des déclencheurs
  * *create* : déclenché lors de la création d'item
  * *update* : déclenché lors de la modification d'item (modification de nom, de propriétés)
  * *softdelete* : déclenché lors de la suppression d'item
  * *delete* : déclenché lors de la suppression définitive d'item
  * *datetime* : déclenché à une date et heure prévue (event)
  * *webhook* : déclenché par une requête web simple (généralement un autre logiciel)
  * *fusioninventory* : déclenché lors d'un inventaire FusionInventory (inventaire qui arrive dans le backend)
* *engine* : ce sont des briques qui effectuent diverses opérations sur les données
  * *checkcriteria* : permet de vérifier telle ou telle valeur (dans un item, propriété d'item, ou dans l'inventaire FusionInventory)
  * *getdata* : permet de prendre une valeur et de la stocker dans une variable qui peut être utilisée dans le workflow
  * *renamedata* : permet de modifier une valeur (issue d'un *getdata*) via une valeur fixe, une regex...
  * *searchitem* : permet de chercher un item via des paramètres de recherche (champ, opérateur, valeur)
  * *foreachfusioninventoryitem* : permet de faire des traitements après ce bloc pour chaque élément d'inventaire (par exemple lorsque l'on a plusieurs disques durs)
* *actions* : permet de modifier dans la base de données... les données :D
  * *actionscript* : permet de lancer un script d'action (envoi de notification mail, envoi de notification slack, création d'host dans Zabbix...)
  * *createitem* : permet de créer un nouvel item
  * *updateitem* : permet de modifier un item
  * *fusioninventoryanothertype* : permet de continuer le traitement de l'inventaire FusionInventory pour un autre item (par exemple, après l'ordinateur, on va traiter les processeurs)
  * *associateitemtoproperty* : permet d'associer un item à la propriété d'un autre item géré précédemment par un autre workflow
  * *createevent* : permet de créer un event à une date heure et qui servira pour le trigger *datetime* vu précédemment


<br>

## III.2 Frontend

<br>

### III.2.a Gestion des menus


Avec le code dans le backend pour la gestion des menus, ils sont désormais développés dans le frontend.

Il y a 3 sections de menus, entièrement configurables : 

* *personel* : ce sont les items de menu que vous pouvez définir en personnel, ils seront accessibles par défaut lorsque vous vous connectez
* *business* : ce sont les items groupés qui seront définis par l'administrateur via l'interface
* *configuration* : ce sont les items pour la configuration de FusionSuite, accessible via des droits spécifiques

<hr>

Affectation d'un type d'item (ici les ordinateurs portables) dans le menu *Assets* :
<img src="/assets/img/menu_config.png" width="1300">

<hr>

Visualisation des 3 menus : 

<img src="/assets/img/menus.png" width="1000">

<hr>

Visualisation du menu personel en format smartphone : 

<img src="/assets/img/menu_custom_mobile.png" width="466">


<br>

### III.2.b Gestion des panels des items

Pour chaque type d'item (tickets, ordinateurs portables...), il est possible de créer plusieurs panels et d'y mettre certaines propriétés dedans. Ceci se fait grâce à un drag and drop dans la configuration du type d'item : 

<img src="/assets/img/panels_config.png" width="1300">


<hr>

Dans l'item, on a les propriétés classées dans les panels :

<img src="/assets/img/panels_item.png" width="1300">


<br>

### III.2.c Gestion des workflows

La gestion des workflows a été spécifié, le travail sur l'interface a commencé à évoluer, voici à quoi ça ressemble actuellement :

<img src="/assets/img/workflow_20230706.png" width="1300">

Ces workflows sont gérés dans la configuration de chaque type.


<br>

# IV. Conclusion

Encore désolé pour le délai de ce rapport, le développement a été privilégié à la communication. Rendez-vous début août ^_^.


**David Durieux - Leader du projet FusionSuite**
