---
layout: post
title: Février 2023 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport de février 2023.

# I. Introduction

<br>

Plusieurs parties sont en cours de développement, elles ne seront pas intégrées sur le dépôt de code avant plusieurs semaines.

En effet, ces parties ont des morceaux de code communs et j'ai besoin d'avancer sur chacune afin d'être certain de la bonne cohésion entre elles. Je vais néanmoins présenter leur état actuel dans ce rapport du mois.

<br>

# II. Evènements du projet

<br>

# II.1. Live coding sur Twitch

Plusieurs fois par semaine, je continue de streamer du live coding du projet sur ma chaîne [Twitch](https://www.twitch.tv/ddurieux).

N'hésitez pas à passer faire coucou !

<br>

# III. Développement

<br>

## III.1. Backend

<br>

### III.1.a Gestion de l'affichage personnalisé dans le frontend

Le développement a permis d'améliorer et de corriger plusieurs problèmes, plusieurs tests ont été ajoutés également.

On est sur la fin de cette partie, même s'il reste quelques modifications possibles au niveau des affichages des items.

Deux affichages ont été introduits actuellement : 

* affichage *standard* : l'affichage des propriétés dans un panel
* affichage *timeline* : l'affichage des propriétés en format timeline, utilisable pour les tickets, changements...

Après réflexion, plusieurs autres affichages devraient être ajoutés dans les prochains mois/années et il faut qu'on puisse les gérer aisément, c'est-à-dire sans faire de grosses modifications de base de données à chaque fois.

Pour les idées d'affichages, en voici quelques-unes : 

* vue *baie réseau/serveurs*
* vue *schéma réseau*
* vue *sécurité avec les CVE...*
* ...

<br>

### III.1.b OpenTelemetry

Dans le backend, et plus tard le frontend sera également inclut, OpenTelemetry a été mis en place.

Grâce à ce système, les métriques pourront être envoyées dans un outil d'APM (Application Performance Monitoring) permettant de contrôler la bonne santé de FusionSuite en temps réel.

Il y a 4 modes disponibles, configurables dans le fichier de configuration, à savoir : 

* *OTLM_DISABLED* : traces désactivées
* *OTLM_NORMAL* : traces sur les principaux composants clé du backend, très peu gourmand en ressources
* *OTLM_DATABASE_QUERIES* : traces normales + traces de toutes les requêtes sur la base de données, plus gourmandes en ressources et peut ralentir de quelques millisecondes les requêtes sur le backend
* *OTLM_DEVELOPMENT* : traces extrêmes, utilisables pour le développement et rend les requêtes du backend extrêmement lentes


Voici un affichage d'APM (Jaeger) avec un niveau *OTLM_NORMAL*. Les requêtes ne sont pas encore toutes optimisées sur cette vue.

<img src="/assets/img/jaeger_20230308.png" width="1300">

<br>

### III.1.c FusionInventory

Comme prévu sur le planning (présentation de janvier dernier), le travail sur l'agent FusionInventory a démarré sérieusement.

Pour rappel, modification du format de données et mise en place du protocole API REST pour l'échange standardisé et simplifié avec le serveur.

Le serveur justement, **FusionSuite!!!** le code a débuté, l'inventaire est déjà récupérable en partie, et les premières briques de mise à jour des données effectuées (dans un item laptop pour le moment).

Le travail continue sur le format des données côté agent et dès que ça sera plus avancé (soit d'ici quelques jours), je vais pouvoir écrire les grosses parties de gestion de l'inventaire dans FusionSuite.

<br>

## III.2 Frontend

<br>

### III.2.a Gestion des tâches/workflows

Les spécifications et le début du code ont été effectués, il reste encore du travail pour cette gestion des règles et workflows.

Je vous mets une image de la tendance, c'est loin d'être finalisé, donc il faut juste voir le principe général des flux.


<img src="/assets/img/workflow.png" width="1300">


<br>

# IV. Conclusion

Plusieurs parties liées, donc beaucoup de chantiers en parallèle. J'espère pouvoir merger le code dans les dépôts de code d'ici 2 mois. On aura alors quasiment toutes les briques essentielles pour la release de fin d'année.

**David Durieux - Leader du projet FusionSuite**
