---
layout: post
title: Mars 2022 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport du mois de mars 2022, avec plusieurs jours de retard, veuillez m'en excuser.


# I. Dévelopement

<br>

## I.1. Backend

<br>

### I.1.a. Paramètres utilisateurs

La première partie des paramètres utilisateurs a été implémentée.

* *paramètres des listes d'items*: gestion des colonnes à afficher, et l'ordre + le nombre d'éléments à afficher, gérés par type d'items
* *paramètres d'import CSV*: gestion de la configuration d'import des données CSV, gérés par type d'items


D'autres paramètres utilisateurs seront implémentés dans les prochaines semaines/mois :

* *configuration de la création/mise à jour d'item*
* *configuration du menu*
* *configuration de la page d'accueil*

Peut être d'autres paramètres seront requis, mais pas identifiés pour le moment en dehors de ces 5 paramètres.


<br>

### I.1.b Champs typés des propriétés

Le travail est actuellement concentré sur une partie importante à finaliser, la gestion des propriétés.

Les propriétés peuvent être des string, integer, number, boolean, float, date, datetime, itemlink et itemlinks.

Pour le dernier, *itemslinks*, on a besoin de modifier l'API REST.

Beaucoup de réflexions sur la conception de tous ces champs dans la base de données. Le but étant d'avoir des champs avec une recherche rapide (indexation, performances).

C'est sur le bon chemin et pourra être finalisé début mai.


<br>

## I.2 Frontend


<br>

### I.2.a Paramètres utilisateurs dans les listes d'items

Le code a été implémenté pour gérer les paramètres des listes d'items, en lien avec le travail effectué dans le backend.

<br>

### I.2.b Import CSV

Plusieurs modifications dans l'import CSV. Le desgin a été amélioré grâce au travail de Sarah, ergonome travaillant chez notre partenaire [Probesys](https://www.probesys.com/).

La première implémentation des CSV fonctionne vraiment bien.

<iframe width="560" height="315" src="https://www.youtube.com/embed/SAtcYfFf1ME" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


<br>

### I.2.c Création et affichage des items

Avec la gestion des types de champs des propriétés dans le backend, le code de la création/mise à jour des items est en cours.

Cela sera disponible en mai pour la campagne de tests.


<br>

## I.3 Offre d'emploi (en France) par Probesys

Notre partenaire Probesys a ouvert un poste de développeur sur FusionSuite. Vous pouvez consulter l'annonce et les détails sur leur [site internet](https://www.probesys.com/articles/probesys-recrute-une-leaddev-pour-fusionsuite).


<br>

# II. Campagne de tests

La première campagne de tests est planifiée les 20 et 21 mai.

Le but est de tester les listes d'items, la pagination, l'import CSV, la création d'item et leur modification.

Il y a aura une news complète dans quelques jours et le lien pour s'enregistrer.


<br>

# V. Conclusion

Le travail continue dans la bonne direction - This is the way -



**David Durieux - Leader du projet FusionSuite**
