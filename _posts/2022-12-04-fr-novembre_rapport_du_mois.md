---
layout: post
title: Novembre 2022 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport de novembre.

# I. Introduction

<br>

Amélioration des tests, gestion des changements, casse-tête sur les tests lancés par github.

On va détailler tout ça, et d'autres choses, dans la suite du rapport.

<br>

# II. Evènements du projet

<br>

# II.1. Live coding sur Twitch

Plusieurs fois par semaine, je continue de streamer du live coding du projet sur ma chaîne [Twitch](https://www.twitch.tv/ddurieux).

C'est toujours un plaisir de streamer du développement de code. Ce mois-ci, c'était assez abstrait car centré sur le backend.

En décembre, le plus gros du travail portera sur le frontend, et notamment pendant les vacances de noël, ça sera donc plus visuel ^_^

N'hésitez pas à passer faire coucou !

<br>

# II.2. Anniversaire du projet le 12 janvier 2023

Le projet FusionSuite soufflera sa première bougie le 12 janvier prochain.

J'en ai parlé lors du rapport précédent, mais je confirme les informations : 

* date : **le jeudi 12 janvier à 20h00**
* lieu : sur [Twitch](https://www.twitch.tv/ddurieux)

<br>


# II.3. Mise à disposition de serveurs par notre partenaire DCS EASYWARE

Notre partenaire [DCS EASYWARE](https://www.dcsit-group.com/) nous a mis à disposition 5 serveurs pour commencer les tests de performance et les configurations possibles, à savoir : 

* tests de performance de l'application sous charge (requêtes SQL, optimisation de code...)
* tests de répartition de charge (load balancing), avec chaque type de répartition possible
* tests de Haute Disponibilité (HA)

Pour les 2 derniers points, ça sera simple à mettre en place une fois en production chez vous, car le backend a été pensé et architecturé pour un mode normal (1 serveur), mais également pour ces modes-là, utiles pour les plus gros environnements.

Je vous en reparlerai dans un prochain rapport du mois ;)

<br>

# III. Développement

<br>

## III.1. Backend

<br>

### III.1.a Amélioration des tests

Enormément de temps a été consacré à l'amélioration des tests :

* renommage des dossiers des tests *RESTAPI*
* mise en place du *lint* (eslint) des tests pour avoir du code propre (même pour des tests)

Cela représente des dizaines de milliers de lignes modifiées, mais on a des tests plutôt propres (2400 tests).

<br>

### III.1.b Github actions

Beaucoup d'heures ont été perdues (environ 20 ;/ ) dans la résolution des actions github.

Les actions github sont les tests lancés lorsque l'on commit dans le dépôt pour vérifier que l'on n'a rien cassé.

En novembre, une nouvelle image du système d'exploitation a été mise en place par Github (Ubuntu 22.04).
On lançait les tests php-fpm dans le dossier `home` et c'est désormais protégé dans cette nouvelle version.

Après plein de tests, au final la seule solution est de déplacer les fichiers du backend dans `/var/www/` pour que *php-fpm* puisse accéder aux fichiers.

<br>


### III.1.c PHP 7.4

En novembre, **PHP 7.4 est passé EOL**.

Cette version a été enlevée du backend, donc PHP 8.0 et 8.1 sont recommandées (obligatoire en réalité).

<br>


### III.1.d Gestion des changements

La gestion des changements a été mise en place, c'est l'historique des modifications.
Lorsque l'on modifie le nom d'un item, sa propriété...


Ces changements ne sont accessibles que via la récupération d'un item avec son id.

Lorsque l'on récupère plusieurs items, les changements ne seront pas dans les données.

Les données historisées sont : 

* userid : l'id de l'utilisateur
* username : le login de l'utilisateur (utile dans le cas où l'utilisateur est supprimé de la base)
* model_type : c'est le model/endpoint
* model_id : l'id de l'item
* property_name : le nom de la propriété dans le cas d'une modification de la propriété d'un modèle *item*
* property_id : id de la propriété
* set_by_rule : dit si ça a été modifié par une règle ou pas
* message : le message, par exemple *admin changed "priority" to "high"*
* old_value : l'ancienne valeur
* new_value : la nouvelle valeur
* created_at : la date/heure à laquelle la modification a eu lieu


Après plusieurs jours de réflexion, lors de la suppression définitive, il a été décidé de mettre dans *old_value* la liste de tous les champs de l'item. Ceci permettra à un admin de pouvoir retrouver les informations qu'il y avait avant suppression. J'ai eu le cas plusieurs fois et c'est vraiment utile.

Je ne sais pas encore s'il y aura une page admin spécialement pour ça ou si ça restera manuel dans la base de données.

<br>


### III.1.e Upgrade Eloquent

Eloqent a été mis à jour en version 9.x, les tests passent tous donc pas d'effet de bord détecté.


<br>

## III.2 Frontend

<br>

### III.2.a Introduction

Les efforts ont été portés en novembre sur le backend pour stabiliser et ajouter les changements, donc très peu de modifications sur le frontend.

<br>

### III.2.b Programme de décembre

Les tickets ont été pas mal codés ces derniers mois.

Je me rends compte que le code est assez conséquent, il va donc être divisé en plusieurs parties, à savoir : 

1/ mise en place de la partie conversation dans un composant spécifique, car utilisé également pour l'historique (types, ordinateurs...)
2/ code de la gestion des propriétés (+ historique)
3/ code de la gestion des types (+ historique)
4/ code de l'import des templates (tickets...)
5/ code des tickets


<br>


# IV. Conclusion

Le projet continue bien, on va passer un stade en décembre en avançant sur le frontend suite à la stabilisation et la gestion des changements dans le backend.

**David Durieux - Leader du projet FusionSuite**
