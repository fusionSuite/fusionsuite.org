---
layout: post
title: Août & septembre 2023 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport du mois pour les mois d'août et septembre 2023.

# I. Introduction

<br>

Je n'ai pas pu faire celui du mois d'août, le mois de septembre a été très chargé personnellement, j'ai dû repousser et grouper les 2 mois.

Sujets qu'on va aborder dans ce rapport :

* retour du premier test par des utilisateurs
* mise en place des workflows
* mise en place de la recherche d'items
* planning release

Voici le menu de ce rapport.

<br>

# II. Evènements du projet

<br>

# II.1. Tests communautaires

Le premier test des utilisateurs a été effectué **du 31 août au 2 septembre** dernier.

Forcément, tout n'est pas finalisé, donc certains retours étaient logiques, d'autres plus intéressants.

Voici les retours, avec mes commentaires en italique :

* la barre latérale du menu est bien et facile à utiliser
* le texte (du menu par exemple) semble trop grand, il faut réduire un peu *- après vérification, c'est effectivement le cas -*
* le surlignage de l'élément menu dans lequel on se situe est difficile à lire, essayer de mettre juste une barre dessus (souligner) *- je vais faire des tests et demanderai certainement des retours sur le serveur Discord -*
* la couleur rouge/rose du menu de configuration ne fait pas l'unanimité
* divers problèmes dans la création d'utilisateur dans le frontend (interface web)
* il manque la possibilité de changer le mot de passe utilisateur *- normal, pas encore fait -*
* possibilité de mettre un texte personnalisé sur la page de connexion et en pied de page, texte requis dans certains pays
* gestion de l'encodage par rapport à la langue
* gestion de l'affichage des dates/heure avec la timezone *- pas encore regardé ce point-là -*
* gestion des devises requise
* les conversations des tickets ne fonctionnent pas *- j'ai dû casser quelque chose, je n'avais pas encore mis de tests là-dessus donc pas anormal -*
* création des types : mettre *required* en rouge et derrière le titre
* création des types : besoin de plus d'espace entre les champs
* comment gérer la fusion d'entreprises, et donc de 2 instances FusionSuite *- pas encore réfléchi à ces cas-là -*
* gestion de l'authentification via LDAP, SAML, Azure AD et OAuth *- c'est prévu -*
* pas de gestion des droits/rôles *- c'est fait dans le backend, mais pas encore dans l'interface web -*
* migration de GLPI à FusionSuite *- prévu en décembre -*
* traductions d'interface *- ça se fait à la fin, la traduction pourra être effectuée par la communauté en décembre / janvier prochain -*
 

Plus lié à FusionInventory :

* divers problèmes liés à l'agent sous Windows ont été reportés et corrigés
* l'inventaire fonctionne partiellement dans FusionSuite
* plusieurs problèmes de mapping de champs *- en cours d'intégration et quelques soucis dans les workflows, voir le chapitre plus loin -*


Ce premier test à permis de soulever quelques points dont je n'avais pas encore pensé, ça va permettre d'affiner l'affichage.

On va planifier un autre test, plutôt fin novembre.

<br>

# III. Développement

<br>

## III.1. Backend

<br>

### III.1.a Workflow

Les workflows sont un peu plus complexes que je pensais. Il y a déjà pas mal de code fonctionnel (inventaire FusionInventory, webhook...) mais d'autres qui requiert encore un peu de travail. Le curseur entre simplicité d'utilisation et puissance/complexité des workflows prend forcément du temps.

Malgré ça, ça fonctionne plutôt dans le sens que je souhaite, donc c'est un bon point.

**La partie workflow est la brique la plus importante de FusionSuite.**

<br>

### III.1.b Recherche

J'ai commencé à développer la recherche d'items.

Ce chantier est plutôt bien avancé et je suis en cours d'écriture des tests en parallèle du code.

<br>

### III.1.c Planning

Au niveau du backend, il reste 2 grosses fonctionnalités à terminer pour la release : 

* workflow : fin planifiée en décembre (très gros morceau)
* recherche : fin planifiée en octobre

<br>

## III.2 Frontend

<br>

### III.2.a Gestion des workflows

L'interface a évolué, on a un menu pour paramétrer chaque bloc, il reste encore du travail d'ergonomie dessus pour être le plus simple possible à utiliser, mais la première ébauche est une bonne base de travail.

<img src="/assets/img/2023-10_workflow_general.png" width="1300">

<img src="/assets/img/2023-10_workflow_block-config.png" width="1300">

Au niveau technique, j'ai dû séparer tous les blocs dans le code pour simplifier grandement le code et donc la maintenance pour plus tard.


<br>

### III.2.b Recherche

La partie recherche dans l'interface permet de faire des recherches un peu complexe (contient, plus grand que, commence par...) suivant ce qu'on recherche (nom, propriété).

J'ai implémenté 2 manières d'utiliser la recherche : 

* directement dans la barre de recherche au format texte en tapant les champs (avec des suggestions) et valeurs. Cette barre est accessible directement en tapant sur la touche **/**.
* une recherche avancée qui guide avec le choix du champ, l'opérateur et la valeur

Tout n'est pas encore fini, mais plutôt très avancé côté interface et sera finalisé en octobre.

<img src="/assets/img/2023-10_search-general.png" width="1300">

<img src="/assets/img/2023-10_search-advanced.png" width="1300">


<br>

### III.2.c Affichage

J'ai commencé à améliorer toutes les petites choses de l'interface qui ont besoin d'une passe de peaufinage, amélioration, le travail va continuer sur les 3 prochains mois.

<br>

### III.2.d Planning

Au niveau du frontend, il reste à finir pour la release : 

* workflows : planifié en décembre
* recherche : planifiée en octobre
* import des fichiers CSV : code fait, intégration en octobre/novembre
* gestion des rôles : planifié en novembre
* diverses améliorations d'interface/design
* documentation
* traduction


<br>

# IV. Conclusion

Le projet est sur la fin pour la première release, après plus de 2 ans de développement, j'ai vraiment hâte de vous mettre tout ça entre vos mains \o/.


**David Durieux - Leader du projet FusionSuite**
