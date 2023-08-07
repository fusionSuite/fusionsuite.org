---
layout: post
title: Juillet 2023 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport du mois de juillet 2023.

# I. Introduction

<br>

Lors de ce mois de juillet, le focus a été mis sur les workflows, la validation du schéma de données de FusionInventory agent 3.0, préparation des tests utilisateurs.

Voici le menu de ce rapport.

<br>

# II. Evénements du projet

<br>

# II.1. Validation de l'agent FusionInventory 3.0

Le développement accru des workflows, en ce mois de juillet, a permis d'avoir les premiers inventaires FusionInventory avec l'agent en version 3.0 intégrés dans FusionSuite. Ceci fonctionne parfaitement et avec les infos que l'on souhaite.

L'inventaire fonctionne bien, mais pas encore optimisé évidemment. Des attributs supplémentaires peuvent être ajoutés dans l'agent d'inventaire et pris en compte dans FusionSuite très facilement.

Ces tests permettent ainsi de valider le nouveau protocole (API REST) et la nouvelle structure de données (au format JSON) de l'inventaire de FusionInventory 3.0 \o/

J'attendais ces tests pour valider le nouveau format et ainsi continuer le code sur l'agent 3.0, donc très bonne nouvelle !

<br>

# II.2. Tests communautaires, inscriptions

Il est désormais temps de lancer le premier test des utilisateurs.

<img src="/assets/img/yeah.gif" width="500">


Il y a plusieurs points importants à prendre en compte : 

  * c'est **une version de développement**, donc tout n'est pas implémenté/finalisé
  * **ce n'est PAS une version beta** et beaucoup de choses peuvent encore changer
  * besoin de retours sur l'application pour voir les choix pris et les modifications à effectuer pour arriver à la version 1.0
  * vous devez posséder un compte *github* pour les issues
  * un compte discord peut être un plus, mais pas obligatoire. Un canal de discussion *privé* entre testeurs et développeurs sera disponible
  * le test durera 3 jours, soit **du 31 août au 2 septembre inclus**
  * chaque testeur aura une instance personnelle (test individuel)
  * tous les testeurs auront accès à une instance globale / partagée (test groupé)
  * les testeurs auront accès à une version de développement de l'agent FusionInventory en version 3.0, pour Windows uniquement
  * les langues utilisées pour les retours des testeurs sont uniquement en *anglais* et *français* (github & discord)
  * de nombreuses données seront collectées pour analyse et amélioration : 
    * logs web NGINX
    * logs d'erreurs (dans la base de données & fichiers erreur NGINX)
    * télémétrie du backend
      * en mode *OTLM_NORMAL* le premier jour
      * en mode *OTLM_DATABASE_QUERIES* les 2 autres jours (temps de réponse un peu plus lents)


Si vous êtes d'accord avec ces informations et que vous souhaitez participer, merci de m'envoyer <a href="mailto:david@durieux.family?subject=Inscription premier test FusionSuite&body=je souhaite participer à ce premier test de FusionSuite et FusionInventory%0D%0A%0D%0AMon compte github : %0D%0AMon compte discord (facultatif) : %0D%0AQuelques mots sur ce que vous attendez de FusionSuite : %0D%0A">un mail rempli avec les informations requises</a>.


Je vous confirmerai votre inscription ou non dans les heures suivant la réception du mail, le nombre d'inscriptions étant limité.

Je vous enverrai un récapitulatif par mail le 29 août avec les URL des 2 instances (une personnelle et une globale) à utiliser le 31 août.

Je vous remercie très fortement d'avance pour ces tests, les retours permettront d'adapter la feuille de route de cette fin d'année avant la release 1.0.

<br>

# III. Développement

<br>

## III.1. Backend

<br>

### III.1.a Workflow

Le code des workflow a bien avancé, les tests unitaires et fonctionnels également.

Le code est réalisé à 80 % et les tests à 60 %.

Cela devrait être finalisé courant août.

<br>

## III.2 Frontend

<br>

### III.2.a Gestion des types

Avec les workflows, des raccourcis ont été ajoutés en haut afin de se rendre rapidement dans la partie demandée dans la configuration des types (workflow, timeline...).

C'est fonctionnel, pas encore très joli par contre (mais ça viendra).

<br>

### III.2.b Gestion des workflows

Le développement a bien avancé.

Des modifications importantes ont été effectuées dans le code afin que ce dernier soit plus simple et maintenable.

Le code est réalisé à 70 %, les tests à 10 %.

<br>

# IV. Conclusion

Les workflows sont la partie la plus importante de FusionSuite, les premières utilisations permettent de voir l'étendu des possibilités, et c'est vraiment cool et excitant.

**David Durieux - Leader du projet FusionSuite**
