---
layout: post
title: Août 2022 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport du mois d'août 2022.

# I. Introduction

<br>

Août a été un bon mois et plusieurs parties du logiciel continuent à être ajoutées à un bon rythme.

Le logiciel continue à avoir une base solide.

<img src="/assets/img/IMG_0791-1024x768.jpg" width="1024">

*Crédit: [https://www.thiscobhouse.com](https://www.thiscobhouse.com)*


# II. Développement

<br>

## II.1. Backend

<br>

### II.1.a Docker env pour les développeurs

Marien a ajouté du code pour les développeurs afin d'exécuter le backend dans Docker (conteneur).

<br>

### II.1.b Rôles et permissions

Quasiment terminé, David a ajouté du code pour gérer les rôles et les permissions.

Le rôle est défini par :

 * un nom
 * une permission pour les structures (types, propriétés, rôles, règles...) avec les valeurs possibles : **grant**, **none**, **custom**
 * une permission pour les données (tous les items) : **grant**, **none**, **custom**

Si la permission pour la structure est *custom*, on a un sous-niveau de permissions. Pour chaque endpoint (*config/type*, *config/properties*...), on défini :

 * permission de voir : **grant**, **none**, **custom**
 * permission de créer : **grant**, **none**
 * permission de mettre à jour : **grant**, **none**, **custom**
 * permission de suppression soft : **grant**, **none**, **custom**
 * permission de supprimer : **grant**, **none**, **custom**

Si certaines de ces permissions sont définies en *custom*, on va avoir un troisième et dernier niveau de permissions. Les IDs du endpoint (par exemple le type *Organization*, le type *Users*, la propriété *address*) sont définis :

 * permission de voir : **true** / **false**
 * permission de mettre à jour : **true** / **false**
 * permission de suppression soft : **true** / **false**
 * permission de supprimer : **true** / **false**

Pour les rôles, il n'est pas possible de créer un rôle & permissions avec plus de permissions que l'utilisateur qui crée ce rôle. C'est un système de sécurité.


Pour les données, si définies comme *custom*, on défini les propriétés de tous les items d'un type d'items (*Organization*, *Users*, *Laptop*, *Tickets*...) :

 * permission de voir : **true** / **false**
 * permission de création : **true** / **false**
 * permission de mise à jour : **true** / **false**
 * permission de suppression soft : **true** / **false**
 * permission de suppression : **true** / **false**
 * option pour gérer les propriétés des items en *custom*, si pas défini, on utilise les permissions de voir et de mettre à jour défini dans les items de ce type.


Si les propriétés des items sont définies en *custom*, vous devez définir les permissions de chaque propriété du type d'items en :

 * permission de voir : **true** / **false**
 * permission de mettre à jour : **true** / **false**


Avec un exemple, ça peut être plus facile de comprendre :

Vous pouvez avoir des tickets, refus d'en créer, mais pouvez les voir et ne les modifier uniquement, et pas la permission de voir la propriété relative au lieu.


**Nous avons défini 1 utilisateur = 1 rôle**. Nous avons commencé à réfléchir pour avoir 1 rôle par organisation (donc plusieurs rôles par utilisateur), mais on n'est pas encore sûr de faire ça.


Le code est quasiment finalisé et on a ajouté un peu plus de 200 tests.

<br>


### II.1.c Performances de la base de données

Plusieurs grosses parties sont été ajoutées dans le backend, David a développé un script qui analyse toutes les requêtes et détecte les requêtes qui n'utilisent pas les index correctement ou qui sont absents, dans le but de les optimiser. Avec la simplicité du schéma de la base de données, ajouter les bons index est relativement simple.

Cette tâche va être exécutée plusieurs fois dans le process de développement afin d'optimiser au mieux les requêtes.

Juste avec les tests, on exécute plus de 25 000 requêtes de type SELECT dans la DB en 1 minute.

Des tests de performance ont commencé à être écrits, mais on détaillera cela dans un futur rapport du mois ;)

<br>


### II.1.d FusionInventory inventory

Les spécifications du nouveau protocole de FusionInventory (version 3 : format JSON et structure en forme de conteneurs) continuent, mais a besoin encore de quelques semaines.

<br>


### II.1.e Premiers bugs

Marien travaille sur le frontend, il a découvert quelques problèmes avec le backend pour récupérer les données dans des cas spécifiques. Du code et des tests vont être ajoutés en septembre pour gérer ces cas.

<br>

## II.2 Frontend

<br>

### II.2.a Docker env pour les développeurs

Marien a ajouté du code pour les développeurs afin de faire tourner le frontend dans Docker (conteneur).


<br>

### II.2.b Organisations

Marien a codé les pages pour voir, créer et supprimer les organisations.

<img src="/assets/img/Screenshot_2022-09-04_at_08-23-05_Organizations.png" width="1116">


<br>

### II.2.c Utilisateurs

Marien a codé les pages pour voir, créer et supprimer les utilisateurs.

<img src="/assets/img/Screenshot_2022-09-04_at_09-01-00_New_user.png" width="1116">


<br>

### II.2.d Messages interatifs

Les messages interactifs ont été ajoutés lorsqu'une action est effectuée et que le logiciel a besoin de prévenir l'utilisateur pour plusieurs raisons :

* item créé
* item modifié
* item supprimé
* n'importe quel message d'erreur provenant du backend (pas de permission, champ manquant...)

<br>

### II.2.e Traduction

Marien a commencé la traduction de l'interface et ajouté la commande pour extraire les textes qui sont à traduire dans le *Makefile*.

<br>

### II.2.f Améliorations internes

Marien a effectué des modifications pour réorganiser le code pour :

* gérer les versions d'API du backend (actuellement *v1*)
* les requêtes d'API du backend
* l'authentification
* le modèle de données comme les items / utilisateurs / organisations (interfaces typescript)

Cette réorganisation va aider à gérer tous les items et types d'items dans FusionSuite (laptop, tickets, contrats...).

<br>

### II.2.g Menu

On écrit des spécifications sur le menu [issue #60](https://github.com/fusionSuite/FusionSuite/issues/60). Comme on peut avoir énormément de types d'items, on essaye de faire une liste et de les dispatcher du mieux possible pour avoir un menu simple.

<br>

### II.2.h Tests End to End

Marien a commencé à implémenter les tests sur le frontend.

Ces types de tests démarrent un moteur de navigateur (chrome, firefox...) et effectuent les actions comme le ferait un utilisateur et vérifie que les actions fonctionnent bien (remplir un formulaire, cliquer sur le bouton, vérifier les messages interactifs...).

Ces tests permettent de prévenir les problèmes des utilisateurs quand les développeurs ajoutent / modifient des parties de code.

La qualité de FusionInventory est une de nos priorités ^_^

<br>


# V. Conclusion


Beaucoup de changements, et le travail continu.

<img src="/assets/img/Worker.svg" width="300">

Merci à nos partenaires [PROBESYS](https://www.probesys.com/) et [dcs EASYWARE](https://www.dcsit-group.com) pour le temps consacré sur le projet.


**David Durieux - Leader du projet FusionSuite**
