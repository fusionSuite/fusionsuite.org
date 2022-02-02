---
layout: post
title: Janvier 2022 - Rapport du mois
categories: news
lang: fr
---

Comme pour le projet FusionInventory, j'écris chaque fin de mois ou début du mois suivant un rapport sur le projet. Le but est de vous informer de ce qui se passe dans le mois (code, communauté, documentation...) et de donner les directions pour les jours/semaines/mois suivants.

Allons-y ;)

# I. Annonce et présentation du projet

Après des semaines de travail pour préparer la présentation du projet, de lecture et corrections de la présentation par nos 2 partenaires, j'ai présenté le projet en direct sur la plateforme Twitch le 12 janvier 2022.

Environ 230 personnes ont suivi cette présentation. Ca semble avoir eu son effet ;)

Plusieurs utilisateurs/sociétés m'ont contacté (directement ou sur le serveur Discord) pour offrir leur aide sur le projet.

Snax44 et Laurent Lienhard ont rejoins le projet. Ils écrivent la documentation du projet, et Laurent a créé des dockers des versions de développement dans le but de pouvoir tester rapidement le produit (1 docker pour le backend et 1 docker pour le frontend, voir plus loin).

# II. Développement

## II.1. Backend

### II.1.a. REST API

Ce mois, soit après la fin du POC, la première tâche a été de stabiliser et d'ajouter des tests à l'API REST. The travail n'est pas fini mais une grosse partie a été effectuée.
Il est possible que les endpoints de l'API REST bougent encore (comme on a eu `/cmdb/type` qui est maintenant `/config/type`).

J'ai ajouté des librairies aux fonctions REST API afin de valider les données reçues : les noms des clés (par exemple vérifier qu'il y a bien les clés`name`, `type_id`), les types de valeurs (comme string, integer, boolean...). Ce système est plus puissant que celui que j'avais utilisé dans le POC. Dans le cas où la validation ne passe pas, une exception est déclarée et un message d'erreur explicite est renvoyé, associé à un code d'erreur HTTP.


### II.1.b. Règles

Comme vous avez pu le voir sur la présentation, les règles sont très importantes.

J'ai commencé à concevoir et à écrire les règles quand on *ajoute* ou *met à jour* un élément.

On a 2 types de règles :

* mettre à jour un champ
* exécuter un script

Ceci est la description d'*executer un script*.

Quand un élément est ajouté ou modifié, un script peut être appelé et exécuté. Plusieurs exemples de scripts :

* envoyer une notification par email
* envoyer une notification sur Slack
* créer un host dans Zabbix (solution de supervision)

Comme on peut le voir, ces règles sont utilisées pour communiquer à l'extérieur de FusionSuite.

Le premier script (ajout de host Zabbix) est écrit (c'est en PHP) et fonctionne bien.

La documentation pour les développeurs est écrite (c'est encore en format ébauche pour l'instant).

J'écrirais un article sur le site internet dans quelques jours à propos avec toutes les informations. Je serai content si des utilisateurs écrivent des scripts pour peut être d'autres usages et d'intégrer ces scripts pour la future et première release.

Ca va également me donner les usages que vous pourriez avoir et me forcer à modifier certaines parties de ces règles (probablement que je n'ai pas pensé à tous les cas d'usage possibles que vous pourriez avoir).

## II.2. Frontend

Le frontend n'a pas été mis à jour depuis le POC. Je préfère stabilisé le backend en premier lieu et ne pas le modifier sans arrêt, car ça va entraîner du temps perdu inutilement.

Mais oui, il y a un *mais*, le travail sur le design commence en ce début de février par Sarah, qui est ergonome chez notre partenaire [Probesys](https://www.probesys.com/). Merci à eux !


## II.3. Images docker

Laurent Lienhard a créé le docker FusionSuite pour le backend et le frontend. **C'est de la version de développement, donc ça ne fonctionne pas bien pour le moment**. Vous pouvez le trouver sur son [dépôt](https://github.com/LaurentLienhard/FusionSuite-Docker).



# III. Campagnes de tests

Durant l'année et avant la release, plusieurs campagnes de test vont être planifiées portant sur des parties spécifiques à tester (certaines fonctionnalités à tester dans tous les sens) de FusionSuite.

La première campagne peut être planifiée pour mai - juin (pas encore exactement défini). Ca sera annoncé quand les dates (prévues sur 2 ou 3 jours) seront confirmées.

# IV. Communication

Quelques actualités sur la communication ;)


## IV.1. Serveur Discord

Le serveur Discord, qu'on partage avec l'équipe de FusionInventory est toujours ouvert, plusieurs fonctionnalités sont discutés dessus. Si vous souhaitez échanger avec nous, venez...


## IV.2. Youtube

La vidéo de la présentation, enregistrée sur Twitch le 12 janvier sera bientôt publiée sur notre chaîne Youtube. Je suis en train d'écrire les sous-titres en français, espérant que la traduction automatique dans d'autres langues soit ok. Si vous souhaitez réaliser la traduction vous-même, contactez-nous, ça sera un plaisir de vous donner un accès aux sous-titres and d'intégrer la traduction.

## IV.3. Site web

Le site web a été lancé le 12 janvier.

La semaine dernière, une section *actualités* a été ajoutée pour informer sur le projet, comme ce rapport mensuel de janvier.

La documentation a commencé à être écrite quelques heures seulement après l'annonce du projet by snax44, et sera bientôt disponible sur le site web.

La documentation de l'API REST (documentation technique pour le développeur) est publiée comme une ébauche pour le moment. L'url est disponible [ici](https://fusionsuite.org/documentation/restapi/). C'est une ébauche et elle a encore besoin de temps pour être consistante.



# V. Conclusion


Le projet prend de l'ampleur et il me remplit de joie.



**David Durieux - Leader du projet FusionSuite**

