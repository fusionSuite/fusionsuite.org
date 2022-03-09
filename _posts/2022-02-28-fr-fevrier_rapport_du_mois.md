---
layout: post
title: Février 2022 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport du mois de février 2022, 45 jours après l'annonce du projet.

Plusieurs choses ont été faites et c'est vraiment cool !

C'est parti ;)

# I. Dévelopement

<br>

## I.1. Backend

<br>

### I.1.a. Règles

J'avais commencé à parler des règles dans le rapport du mois précédent et je continue ce mois-ci.

La première implémentation des actions de règles (actions jouées après des modifications dans le backend) est désormais dans le dépôt de code.

The code fonctionne et quand on cré un item (par exemple, un serveur), un email est envoyé, un host est créé dans la solution de supervision Zabbix (et l'id Zabbix est stocké dans une propriété dans le serveur de FusionSuite).

Plusieurs tests ont été ajoutés pour cette partie, mais requiert quelques modifications pour être taggué comme stable!

Un élément dans les spécifications, pas encore ajouté) est d'exécuter les actions en mode asynchrone dans le but de garder une exécution rapide lors d'un ajout/modification/supression d'un item. Il est possible qu'un script d'action prenne plusieurs minutes à s'exécuter.

<br>

### I.1.b Cli

Du code a été écrit pour avoir une *cli* qui va aider l'administrateur à gérer les tâches.

La *cli* peut être utilisée, pour l'instant, à :

* créer et gérer les connexions à la base de données. Il est possible de créer plusieurs connexions de base de données et de basculer de l'une à l'autre très simplement.
* installer le backend (création de la structure de la base de données et insertion des données).

Pour l'utilisation de la cli, il y a 2 modes :

* mode interactif (la cli pose des questions, affiche de l'aide)
* mode non-interactif, avec des arguments à passer à la commande (interessant pour intégrer à des scripts automatisés)


La documentation a été écrite en même temps : [documentation de la cli](https://fusionsuite.org/documentation/administration_tasks/backend/installation_update/2_installation/).

<br>

### I.1.c Types de base de données

J'ai amélioré les test pour qu'ils fonctionnent sur plusieurs bases de données et dans plusieurs versions.

Les bases de données testées et supportés, pour l'instant, sont :

* MySQL: 5.7 / 8
* MariaDB: 10.4 / 10.5 / 10.6 / 10.7
* PostgreSQL: 11 / 12 / 13 / 14

La partie cli pour SQLite n'a pas encore été ajoutée.

Pour MS SQLSERVER, j'ai des problèmes avec le support UTF-8 et je n'ai pas trouvé de méthode pour l'utiliser comme je le voudrai. Si quelqu'un a des compétences là dessus, contactez-nous (l'information est sur le site).

<br>

### I.1.d User params

La base de données et l'endpoint ont commencé à être implémentés dans le backend pour gérer les userparams (requis pour le frontend).

<br>

## I.2 Frontend

Plein d'informations et de nouveautés sur le frontend ce mois ci ^_^.

<br>

### I.2.a Tests

Debut d'ajout de tests sur le forntend afin de vérifier les dépendences de sécurité, la bonne compilation du site.

<br>

### I.2.b Ionic 6 / Angular 13

J'ai mis à jour le framework qu'on utilise vers Ionic 6 et Angular 13. Meilleures performances et quelques nouveautés qu'on va pouvoir utiliser.

<br>

### I.2.c Design

Le travail sur le design a débuté avec Sarah, ergonome travaillant chez notre partenaire [Probesys](https://www.probesys.com/). Après 3 sessions sur les listes d'items, la première implémentation a débutée.

Voici le design sur les listes d'items avant / après :

<iframe width="560" height="315" src="https://www.youtube.com/embed/cOiVJwYPWlw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### I.2.d Paramètres utilisateur

Les paramètres utilisateurs sont en train d'être ajoutés, comme l'ordre des colonnes, cacher des colonnes, le nombre d'éléments à afficher (pagination).

Le code est fonctionnel, sauvegarde dans le backend et chargement quand on recharge le frontend.

Cette partie devrait être finalisée en mars.

<br>

### I.2.e Import CSV

La fonctionnalité d'import CSV a été écrite. Ca permet de charger un fichier CSV, définir les propriétés à remplir pour chaque colonne (le *modèle d'import* pourra être stocké dans les paramètres utilisateurs, mais pas encore codé) et importer dans le backend.

Cette fonctionnalité fonctionne à merveille.

<img src="/assets/img/post_20220228_csvimport.png" width="1300">

<br>

## I.3 Offre d'emploi (en France) par Probesys

Notre partenaire Probesys a ouvert un poste de développeur sur FusionSuite. Vous pouvez consulter l'annonce et les détails sur leur [site internet](https://www.probesys.com/articles/probesys-recrute-une-leaddev-pour-fusionsuite).


<br>

# II. Campagne de tests

Comme introduite en janvier, la première campagne de tests est planifié en mai - juin. Je pense que les inscriptions seront communiquées dans le prochain rapport du mois (donc fin mars).

<br>

# III. Communication

<br>

## III.1. Website / nouvelle personne dans l'équipe

Le site web a été mis à jour, *Maël Jeuffrard* et *Laurent Lienhard* ont été ajoutés dans l'équipe ^_^. Bienvenu à eux!

<br>

## III.2. Documentation

La documentation continue à être écrite. On l'a séparée en trois parties :

* Guide de l'utilisateur final
* Tâches d'administration / Administrateur
* Développeur


Vous pouvez la trouver à cette [URL](https://fusionsuite.org/documentation/).

<br>

# IV. Structure pour le project

Je réfléchi à propos de la création d'une structure pour le projet FusionSuite (fondation, association...)

Les raisons sont de :

* permettre de recevoir des dons
* redistribuer des dons à les librairies / projets qu'on utilise dans le frontend et backend (souvent oubliés par les utilisateurs, mais vraiment important de les supporter pour leur travail)
* payer une société de sécurité (ou peut être trouver une société qui nous offirait ça) pour auditer le code à la fin de l'année pour que ça soit le plus sécurisé possible
* payer des déplacement pour des présentations ou avoir un stans dans des salons
* ...

Aucune prestation ne sera faite avec cette structure, c'est le rôle des partenaires ;)

<br>

# V. Conclusion

Le travail continue et ça commence à fonctionner sur plusieurs parties du projet et dans l'outil, YEAH



**David Durieux - Leader du projet FusionSuite**
