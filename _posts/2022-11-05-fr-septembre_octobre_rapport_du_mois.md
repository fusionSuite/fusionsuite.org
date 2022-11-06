---
layout: post
title: Septembre et octobre 2022 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport de septembre et octobre réunis.

# I. Introduction

<br>

Je rassemble septembre et octobre dans un seul rapport, les 2 mois ont été assez chargés.

Parmis les gros évènements, on peut citer le *retrait de la société Probesys* du projet, mon *COBID qui m'a cloué au lit un bon moment*, 
le code du backend et *l'avancée du code de la gestion des tickets dans le frontend*.

On va détailler tout ça dans la suite du rapport.

<br>

# II. Evènements du projet

<br>

## II.1. Retrait de Probesys du projet

En septembre, plusieurs réunions ont eu lieu entre moi (David Durieux) et Probesys.

Fin septembre, ils ont décidé d'abandonner le projet pour différentes raisons qui leur sont propres.

On a décidé de se refaire des réunions de temps en temps afin d'échanger sur l'évolution du projet FusionSuite et du logiciel de gestion de ticket qu'ils vont développer.

Je les remercie pour le travail effectué sur le projet.

<br>

# II.2. Live coding sur Twitch

Plusieurs fois par semaine, je stream du live coding du projet sur ma chaîne [Twitch](https://www.twitch.tv/ddurieux).

Je me demandais si c'était intéressant pour les gens et au final il semble que oui, et pour plusieurs raisons : 

* pour les développeurs, ils peuvent voir l'écriture du code et le processus de développement
* pour les (futurs) utilisateurs, ce à quoi FusionSuite va ressembler
* intervenir pour ajouter des fonctionnalités pendant que je code (c'est arrivé 2 fois en octobre sur les tickets)
* je peux demander des avis sur un design, des couleurs...
* échanger sur le projet

Je suis très heureux de streamer, ça crée un lien assez fort avec la communauté, n'hésitez pas à venir ;)

<br>

# II.3. Anniversaire du projet le 12 Janvier 2022

Le projet FusionSuite soufflera sa première bougie le 12 Janvier prochain.

Je suis en train de préparer un live avec une présentation du travail de l'année écoulée, les difficultés, les modifications de planning, une démo de la version de développement.

<br>


# III. Développement

<br>

## III.1. Backend

<br>

### III.1.a Nouvelle option cli : reset de la base de données

Pour les tests end-to-end du frontend, on avait besoin de pouvoir supprimer simplement toutes les tables et rejouer l'installation.

Cette commande est désormais intégrée dans le cli `php bin/cli reset`.


<br>

### III.1.b Rôles et permissions

Comme spécifiée dans le rapport d'août, cette fonctionnalité est finie et a été intégrée.


<br>


### III.1.c Log de type audit

Les logs d'audit on été intégrés dans le backend. Tous les ajouts, modifications, suppressions, connexions (ok ou fail) sont logués dans la base de données et accessible via l'API REST.

Voici le [lien de la documentation](https://fusionsuite.org/documentation/restapi/#api-LogAudits-GetLogAudits) pour interroger le backend.

<br>


### III.1.d Nouvelle option des types : nom unique

On a certains types d'items qui doivent avoir un nom unique, par exemple les comptes utilisateurs.

Cette option a été ajoutée dans la configuration des types.

En écrivant ce paragraphe, je me rends compte qu'il y a eu un loupé dans la documentation de l'API REST. Correction à prévoir.

<br>


### III.1.e Demande de token (login) et refresh de token

L'endpoint pour se loguer et pour rafraîchir le token était complexe, encore plus car c'était dans le même endpoint.

Ces 2 fonctionnalités ont été séparées dans 2 endpoints.

Pour le refresh du token, on a amélioré la sécurité en demandant obligatoirement le token JWT valide (signature) même si périmé (c'est d'ailleurs pour cette raison qu'on a besoin de rafraîchir le token) ainsi que le token du refresh.

[Documentation de l'API REST](https://fusionsuite.org/documentation/restapi/#api-Authentication-PostRefreshToken) disponible.

Le token de refresh est un peu light en nombre de caractères, une Pull Request sera faite pour le complexifier.

<br>

### III.1.f Gestion des mots de passe et des hashs de mots de passes

Une Pull Request est en cours pour gérer les mots de passe (chiffrés) dans la base de données, ainsi que les hash de mot de passe (pour le mot de passe des comptes utilisateurs par exemple).

<br>

### III.1.g Petit mot sur les tests

On a actuellement un total de **2257 tests**.
L'exécution dure environ 2 minutes (il y a des pauses à cause des tests sur les date/heures).

Le backend est codé en *PHP* et les tests en *Javascript*.

Fait amusant, on a plus de code pour les tests (58%) que le code en lui-même (34%), forcément l'utilisation des frameworks (Slim & Eloquent) aide à réduire le code du backend.


<br>

## III.2 Frontend

<br>

### III.2.a Test end-to-end

Les tests end-to-end qui simule un utilisateur dans le navigateur ont été mis en place. On utilise [Cypress](https://www.cypress.io/).

<br>

### III.2.b HTTP Interceptor et rafraîchissement du token

Actuellement, le TOKEN fourni par le backend lors de la connexion expire au bout de 20 minutes pour des raisons de sécurité.

Quand il expire et qu'une requête est effectuée, elle retourne une erreur liée au token, et le rôle du HTTP Interceptor est de redemander un nouveau token à l'aide du refresh token. Une fois le nouveau token reçu, la requête est renvoyée au backend avec ce token valide.

Le système fonctionne parfaitement et c'est transparent pour l'utilisateur.

<br>

### III.2.c Gestion des tickets

La gestion des tickets est en cours de développement.

Vous trouverez ci-dessous une vidéo sur le travail en cours.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9_Bv43gFNaI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>


# IV. Conclusion


Malgré le départ de Probesys, le projet avance bien sur le frontend et la gestion de ticket.

Tout le travail côté backend depuis ces derniers mois (gestion d'API, types dynamiques, propriétés dynamiques...) permet d'avancer rapidement sur le code et l'intégration côté frontend.

La dynamique est bonne ^_^

**David Durieux - Leader du projet FusionSuite**
