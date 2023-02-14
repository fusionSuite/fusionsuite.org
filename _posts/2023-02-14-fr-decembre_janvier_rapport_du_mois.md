---
layout: post
title: Decembre 2022 & janvier 2023 - Rapport du mois
categories: news
lang: fr
---

Voici le rapport de décembre 2022 et de janvier 2023.

# I. Introduction

<br>

Focus sur la configuration et la personnalisation !

Présentation de la rétrospective 2022 et la roadmap/planning 2023 ;)

J'ai encore regroupé 2 mois, car le mois de janvier fut bien chargé avec la préparation de la présentation.

On va détailler tout ça, et d'autres choses, dans la suite du rapport.

<br>

# II. Evènements du projet

<br>

# II.1. Live coding sur Twitch

Plusieurs fois par semaine, je continue de streamer du live coding du projet sur ma chaîne [Twitch](https://www.twitch.tv/ddurieux).

N'hésitez pas à passer faire coucou !

<br>

# II.2. Présentation de la rétrospective 2022 et roadmap/planning 2023

Le 12 janvier dernier, j'ai fait la présentation de la rétrospective 2022 et roadmap/planning 2023.

Les slides de la présentation sont disponibles dans la section **Présentation**, ou directement sur le lien [présentation rétrospective et roadmap 2023](https://fusionsuite.org/presentation/2023-01/presentation.html).

Vous pouvez consulter la roadmap 2023 ci-dessous, en noir *FusionInventory* (assez lié avec FusionSuite) et en bleu *FusionSuite*.

<img src="/assets/img/planning_2023.png" width="1300">

Petite information utile, on va faire un test utilisateur autour de juin afin d'avoir les premiers retours d'utilisation et qui permettra d'ajuster l'interface avant la release en septembre/octobre.

<br>


# III. Développement

<br>

## III.1. Backend

<br>

### III.1.a Documentation API REST

La documentation de l'API REST a été améliorée, certaines parties étaient fausses.

J'ai un sujet là-dessus afin de pouvoir tester dynamiquement à chaque commit de code la documentation API pour vérifier la cohérence avec le code.
Ce sujet n'est pas simple, mais il avance, j'espère avoir quelque chose de fonctionnel d'ici cet été.

<br>

### III.1.b Gestion de l'affichage personnalité dans le frontend

Dans le backend, il a été ajouté (pas encore totalement finalisé), la gestion personnalisée de l'affichage pour le frontend, à savoir : 

 * personnalisation des menus
 * personnalisation des items suivant les types

Pour voir les rendus, se rendre plus bas dans la partie frontend.

Il reste un peu de code, des tests et de la documentation de l'API REST.

<br>


## III.2 Frontend

<br>

### III.2.a Gestion des propriétés

L'ajout de la gestion et configuration des propriétés a été ajouté (partie configuration).
Elle permet d'ajouter des propriétés et de les définir.

<img src="/assets/img/frontend_properties_202302.png" width="1300">


<br>

### III.2.b Ajout d'affichage des items avec la timeline

Certains types requièrent d'avoir une timeline, comme les tickets de supports, la gestion des changements...

Vous pouvoir avoir un aperçu de la version, qui est encore en développement :

<img src="/assets/img/frontend_timeline_202302.png" width="1300">


### III.2.b Gestion des types

La gestion des types a été ajoutée afin de configurer l'affichage des items.

Il permet d'ajouter les propriétés souhaitées, les regrouper dans des sections, de choisir dans quel menu le mettre...

<img src="/assets/img/frontend_types_202302.png" width="1300">

<br>

### III.2.b Gestion des menus

Le menu a enfin été travaillé avec la gestion personnalisée.

Elle contient 2 sections : 

* la vue *Business* : affiche les items regroupés dans des menus, entièrement personnalisables (catégories, icônes)
<br><img src="/assets/img/frontend_menu_business_202302.png">

* la vue *Personnelle* : permet de mettre en favoris les items de la vue business
<br><img src="/assets/img/frontend_menu_personal_202302.png">

Depuis quelques jours, la partie configuration dans le menu Business ne me plaît pas trop, je pense mettre un bouton pour basculer FusionSuite en mode *Configuration* pour la séparer totalement avec la partie utilisation standard. A suivre dans les prochains rapports.

<br>

# IV. Conclusion

Le projet continue bien, la partie frontend avance bien aussi, étant donné la stabilité et simplicité du backend, ça peut être fait vraiment rapidement (bien plus que je ne le pensais et c'est vraiment cool).

**David Durieux - Leader du projet FusionSuite**
