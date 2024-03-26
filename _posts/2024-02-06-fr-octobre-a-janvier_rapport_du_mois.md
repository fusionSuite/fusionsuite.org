---
layout: post
title: Octobre 2023 à janvier 2024 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport du mois pour les mois d'octobre 2023 à janvier 2024. Oui, ça fait 4 mois d'un coup... désolé !

# I. Introduction

<br>

Après 4 mois sans nouvelles (on va revenir sur les raisons), voici ce nouveau rapport du mois.

Mais que s'est il passé ?

Il y a de multiples raisons pour le ralentissement de fin 2023, aussi bien sur la communication que sur le code (forcément, c'est un peu lié) :

* début novembre, pas assez de nouveautés pour justifier un rapport du mois
* démotivation en novembre et première moitié de décembre ; avec le recul, plusieurs raisons : 
  * le fait de ne pas avoir fini FusionSuite & FusionInventory dans les prévisions de mon planning m'a mis un coup de démotivation
  * 2 mois de pluie en continu (il y a de la mousson en France maintenant ?) qui n'aide pas le moral
  * le code des workflows est plus complexe que prévu et le rendre simple est vraiment compliqué, je l'ai mis en pause pour quelques semaines / mois
* de grosses journées au travail qui m'ont un peu épuisé aussi
* une situation personnelle un peu compliquée
* gestion de la traduction communautaire du jeu StarCitizen (ça m'a changé les idées)

Avec le recul sur le développement de ces dernières semaines, je me suis rendu compte de toutes les parties complexes que j'ai déjà implémentées et qui fonctionnent très bien, ça fait du bien au moral.

Pour la date de release, on va tenter pour cet été, en espérant que ça soit bon, mais c'est possible que ça glisse un peu. Il reste les workflows à finaliser, focus en cours sur le soin de la partie graphique web (frontend), finir la gestion des inventaires avec FusionInventory, finir la version 3.0 de FusionInventory, de la documentation (mais ça se fera surtout à la fin), la gestion des droits dans l'interface web...

Donc oui, il reste du travail, mais ça avance.

<br>

# II. Evènements du projet

<br>

# II.1. Performances et charge de la base de données

En janvier, j'ai introduit un bon nombre de données (50k utilisateurs, 20k tickets).

Après des tests en situation standard, la base de données reste réactive, ce qui est plutôt une bonne nouvelle ; un test avec encore bien plus de données sera effectué courant février.

Le pire des cas, soit lister les tickets par 100, a permis de mettre en évidence des problèmes de performance : **8500 requêtes SQL pour 8.5 secondes** de chargement.
Ce n'était bien évidement pas acceptable, mais normal à ce stade du projet, tout n'est pas encore optimisé.

Des modifications ont été effectuées pour utiliser le *Eager Loading*. Grâce aux 3000 tests backend, j'ai pu corriger le code pour que tous les tests repassent au vert, car ça avait cassé une très grosse partie des tests.

Finalement, on arrive à **53 requêtes pour 0.5 secondes (500 ms)** de chargement. Ca peut encore être optimisé et ça le sera sur le mois de février, mais on est déjà dans un scénario bien plus viable (meilleur temps, réduction des ressources serveur utilisées...).

Ce travail a nécessité de nombreux jours et beaucoup de réflexion pour optimiser au mieux au cours du mois de janvier.

<br>


# II.2. Design & utilisation de l'interface web

Le backend est relativement bien stable et a une longueur d'avance en maturité par rapport à l'interface web.

L'accent a été mis fin décembre sur le frontend pour, en premier lieu, corriger les nombreuses parties qui marchaient mal ou pas du tout.

Il reste encore pas mal de fonctionnalités à ajouter côté interface web.


<br>

# III. Développement

<br>

## III.1. Backend

<br>

### III.1.a Modification des pré-requis

La version 8.3 de PHP est prise en charge.

La version 10 de Eloquent a été intégrée.

Les librairies (dépendances) ont été mises à jour.

<br>

### III.1.b Recherche

La partie recherche a été finalisée, les très nombreux tests également.

On peut rechercher un item, sur ses propriétés. Ca permet déjà de faire la majeure partie des recherches d'items.

Certaines recherches ne seront pas possibles avec le code actuel, notamment sur les inventaires avec des sous-sous-sous éléments. Je vais avoir besoin de faire des essais, mais il y aurait 2 solutions possibles : 

* via les workflows, l'ajout ou mise à jour de sous éléments liés pourraient être copiés sur l'élément principal pour faire des recherches dessus (une sorte de résumé sur lequel on pourra faire des recherches)
* modifier la recherche pour autoriser les recherches en multiples sous niveau avec un niveau de profondeur élevé, ça pourrait avoir une incidence sur les performances (à voir)

Je vous tiendrai informé du résultat des tests et de la décision.


<br>

### III.1.c Import des templates

Comme vous le savez peut-être, ou peut-être pas du tout en fait, dans FusionSuite on crée ses types d'items, ses propriétés...

Ca peut être long et pas forcément simple pour tout le monde, donc cette configuration peut être importée via un fichier au format JSON.

Plusieurs corrections ont été effectuées. Le modèle de template de gestion des incidents a été amélioré et testé, il me sert de référence. Des tests ont également été ajoutés afin de prévenir des erreurs que j'ai pu avoir.

<br>

### III.1.d Amélioration des performances

Comme expliqué longuement précédemment, les performances ont été améliorées dans le backend, il est plus réactif dans la récupération des données.

<br>


### III.1.e Scripts de migration de données

Les scripts de migration de données ont commencé à être écrits. Ca permet d'améliorer les performances et les fonctionnalités côté frontend qui sont essentielles ; c'est plus simple quand il y a plein de données.

J'ai commencé par GSIT (9.5) et GLPI (9.5), il y aura d'autres outils du marché pris en charge par la suite.

L'import des comptes utilisateurs est quasiment fini.

Je me suis ensuite focalisé sur les tickets : c'est le plus complexe. Dans ce cas, il faut récupérer l'historique de la vie du ticket et l'injecter par le bon compte utilisateur et avec les bonnes dates. Finalement ça se fait un peu plus facilement que je ne le pensais, et c'est codé à 70 %. Il restera les autres types (parcs informatiques, changements...), il y a encore du travail, mais c'est plutôt encourageant.

<br>

## III.2 Frontend

<br>

### III.2.a Recherche

La recherche est finalisée et correspond bien à ce que je voulais (heureusement :p).

Elle permet d'être utilisée par les amoureux de la souris ainsi que ceux du clavier :D

En mode clavier, l'utilisation est très rapide pour effectuer les filtres.

<img src="/assets/img/2024-02-08-search.png" width="1300">

Il manque la sauvegarde de la recherche, qui sera ajoutée dans les prochaines semaines (avec la sauvegarde des colonnes, des filtres...).


<br>

### III.2.b Rework du menu en mode smartphone

Le menu fonctionne plutôt bien en mode desktop, par contre en mode smartphone c'est inutilisable.

La refonte de cet affichage a été effectuée. Le résultat est plutôt propre et c'est génial.

Quelques captures pour vous rendre compte du résultat : 

<img src="/assets/img/2024-02-08-menu-smartphone-personal.png" width="360">

<img src="/assets/img/2024-02-08-menu-smartphone-business.png" width="360">

<img src="/assets/img/2024-02-08-menu-smartphone-configuration.png" width="360">

<br>

### III.2.c Nouveau design de la page de login

La page de login était cassée et pas jolie du tout.

Son design a été complètement revu (desktop et smartphone).

Pour vous faire plaisir, une capture d'écran de cette page de login :


<img src="/assets/img/2024-02-08-login-page-desktop.png" width="1300">

<img src="/assets/img/2024-02-08-login-page-smartphone.png" width="360">


<br>

### III.2.d Amélioration de la page de recherche / liste des items

Un gros travail a été fait pour améliorer l'ergonomie des listes, des actions, etc... ce travail n'est pas terminé et plusieurs fonctionnalités ne sont pas encore implémentée.

Je les ajoute petit à petit.

<img src="/assets/img/2024-02-08-itemslist.png" width="1300">

<br>


# IV. Conclusion

Malgrés un creux de motivation, les fonctionnalités arrivent et FusionSuite devient de plus en plus mature pour la release.

Il reste encore du travail bien évidemment, et je suis bien motivé pour cette dernière grosse ligne droite.

Pour le prochain rapport du mois, qui arrivera début avril, je devrais avoir de belles captures d'écran de l'interface à vous montrer \o/


**David Durieux - Leader du projet FusionSuite**
