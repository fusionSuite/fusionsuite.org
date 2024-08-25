---
layout: post
title: Juillet 2024 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport du mois pour les mois d'avril à juillet 2024

# I. Introduction

<br>

Amélioration des performances, documentation de l'API REST du backend, gestion de la sécurité, tests End-To-End (e2e), financement participatif...

Pas mal de points à aborder dans ce rapport du mois.

<br>

# II. Evènements du projet

<br>

# II.1. Financement participatif

Fin août, je lancerai un financement participatif.

<img src="/assets/img/crowdfunding.jpg" width="600">

Le projet FusionSuite, ainsi que les autres attenants comme FusionInventory, ne vont pas assez vite. En effet, je développe sur mon temps libre et ça n'avance pas aussi vite que je le souhaite.

Afin de pouvoir finaliser **FusionSuite 1.0** et **FusionInventory 3.0** au plus vite, j'aimerais être à plein temps sur ces projets, pendant 1 an complet.

Ceci permettra : 

 * avant la release :
   * finir le développement
   * rédiger la documentation
 * gérer la communication
 * sortir les releases
 * après les releases :
   * faire le support communautaire
   * définir la roadmap
   * gérer les versions correctives (il y aura forcément quelques bugs qui traînent)

Il y aura des contreparties virtuelles, et d'autres physiques, pour des personnes, et même pour des sociétés qui participeraient.

Vous l'avez compris, j'ai besoin de vous pour cette dernière ligne droite.

**Plus d'information dans une news dédiée fin août pour le lancement**

<br>

# II.2. Expérimentation chez notre partenaire DCS EASYWARE

La version de développement a été mise en place en juin chez notre partenaire DCS EASYWARE afin de gérer la gestion des changements.

La solution se comporte plutôt bien, il reste des fonctionnalités à implémenter afin de le rendre encore plus facile d'utilisation (oui, c'est quand même encore en développement); la quasi-totalité était déjà prévue ;)

Ceci me permet d'avoir des retours d'utilisation de l'outil avant la release.

Merci à [DCS EASYWARE](https://www.dcsit-group.com/) pour leur confiance.

<br>

# III. Développement

<br>

## III.1. Backend

<br>

### III.1.a Standardisation et optimisation de la récupération des items 

Il y avait un problème dans la liste des champs de propriétés (nom, valeur par défaut, peut être null/empty, unité...) quand on récupère un item ou une liste d'items.

Certains champs n'étaient pas vraiment requis et ça consomme des ressources au niveau de la base de données et du backend pour rien.

Ces champs sont donc standardisés (sous-entendu le nombre a été réduit) et les requêtes sont ainsi plus rapides.

<br>

### III.1.b Sécurité des données

Des outils de pentests ont été utilisés afin de vérifier les erreurs éventuelles, comme des erreur PHP, des erreurs d'insertion dans la base de données...

J'ai pu corriger les erreurs mises en évidence, très peu en définitive.

<img src="/assets/img/data-security.jpg" width="600">


L'écriture de ces tests est en cours et sera intégrée dans le dépôt ; on pourra les lancer ponctuellement.

Des tests de XSS, notamment, vont être effectués dans les mois à venir.

<br>

### III.1.c La documentation de l'API REST 

La documentation de l'API REST est rédigée dans le code et générée par un script avec *APIDoc*, mais le mainteneur du projet a [annoncé son abandon](https://github.com/apidoc/apidoc/issues/1436).

J'ai commencé à transposer cette documentation sur les spécifications *openapi 3.1*, mais elles sont nettement moins bien fournies (par exemple impossible de définir si un champ est un *integer* ou un *number*).

je vais voir comment contourner le problème et fournir une documentation qui soit à jour et maintenue, je ne peux pas rester sur *APIDoc*, car bientôt on ne pourra plus générer cette documentation, sauf si quelqu'un reprend le projet, je vais voir ça en août et septembre.

La documentation de l'API REST est déjà disponible depuis de très nombreux mois [ici](https://fusionsuite.org/documentation/restapi/).

<br>

## III.2 Frontend

<br>

### III.2.a Les champs

Les champs (string, integer, boolean, listes...) continuent à être mis en place avec un code générique au sein du frontend.

Les tests End-To-End (c'est-à-dire simulant des opérations faites par des humains dans un navigateur) sont de plus en plus nombreux. Ces tests avancent plutôt vite depuis quelques jours. 
De nombreuses corrections ont déjà été appliquées sur le frontend, mais aussi sur le backend.

Ces tests sont écrits pour [Cypress](https://www.cypress.io/).

J'espère les finaliser d'ici 1 ou 2 mois et pousser toutes ces modifications dans le dépôt de code.

<br>


# IV. Conclusion

L'outil continue de s'améliorer, en route pour la version 1.0 !

**David Durieux - Leader du projet FusionSuite**
