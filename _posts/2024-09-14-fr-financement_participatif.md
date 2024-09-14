---
layout: post
title: Financement participatif
categories: news
lang: fr
---

Comme annoncé dans les deux dernier rapports du mois, le financement participatif vient d'être lancé.

<a href="https://www.kickstarter.com/projects/ddurieux/free-software-fusioninventory-30-andand-fusionsuite-10">
  <img src="/assets/img/kickstarter.png" width="413">
</a>


# I. Introduction

Ce financement participatif concerne deux projets en même temps : 

* FusionInventory
* FusionSuite

Les ambitions, et donc les gros travaux, sont déjà engagés depuis plusieurs mois, voire même plusieurs années.

<br/>

# II. Les projets

<br>
<br>

# II.1. FusionInventory

FusionInventory a commencé sa transformation.

L'agent est en cours de réécriture complète, en langage RUST.

La version sera la version 3.0.

Cet agent permet de réaliser plusieurs opérations au niveau de votre parc informatique : 

 * inventaire automatisé des ordinateurs et serveurs
 * découverte du réseau
 * inventaire du réseau (switch, imprimantes...) via SNMP
 * déploiement d'application & lancement de commandes, scripts...

Cette version sera une version compilée en langage machine et sera plus rapide, robuste et évitera d'avoir un programme interprété sur les ordinateurs (meilleur au niveau sécurité).

La partie serveur (qui pilote l'agent et/ou reçoit les informations) était un plugin dans GLPI. Il a été [abandonnée](https://fusioninventory.org/news/2024/03/27/plugin-fusioninventory-gsit-glpi-support-status.html).

Il existe/va exister au moins deux serveurs : 

 * intégré dans GSIT (fork de GLPI)
 * intégré dans FusionSuite (cf le paragraphe suivant)

<br/>

# II.2. FusionSuite

FusionSuite est un logiciel, commencé en 2021 et développé à 60 % environ.

C'est une application web & mobile qui permet de gérer :

 * ses assets : des ordinateurs, des écrans, des tables, des voitures, des fusées... (c'est vous qui choisissez ce que vous souhaitez gérer)
 * ITIL : tickets de support, changements...
 * sécurité : CVE des applications

Un workflow configurable assez poussé sera également de la partie, permettant de réaliser des opérations via des déclencheurs internes ou externes.

<br/>


# III. A quoi va servir ce financement

Actuellement, je travaille sur ces 2 projets sur mon temps libre.

C'est frustrant, car je ne peux pas aller aussi vite que je le souhaiterai.

Ce financement va me permettre de travailler à 100 % sur ces 2 projets pendant 1 an et donc de faire de longues session de code ou d'écriture de documentation; cela fera gagner beaucoup de temps et finir la **version 3.0 de FusionInventory** et la **version 1.0 de FusionSuite** plus rapidement.

Ça inclura également la documentation à écrire, faire le support à la communauté...

<br>

# IV. Où est-ce que ça se passe?

Toutes les informations du financement sont sur ce lien [kickstarter](https://www.kickstarter.com/projects/ddurieux/free-software-fusioninventory-30-andand-fusionsuite-10).


**David Durieux - Leader du projet FusionSuite**
