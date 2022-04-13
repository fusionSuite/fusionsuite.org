---
layout: post
title: March 2022 - Monthly report
categories: news
lang: en
---

This is the monthly report of March 2022, several days late, sorry for that.


# I. Development

<br>

## I.1. Backend

<br>

### I.1.a. User params

The first part of user params has been implemented:

* *items list params*: management of columns to display, and the order + number of elements to display, managed by type of items
* *CSV import params*: management of the configuration of import CSV data, managed by type of items


Other user params will be implemented next weeks / months:

* *configuration of item display/creation*
* *configuration of menu*
* *configuration of the homepage*

Perhaps other user params can be needed later, but I have identified this 5 for the moment.


<br>

### I.1.b Types of properties fields

The work is actually concentred on a big part to finish, the management of properties.

The properties can be string, integer, number, boolean, float, date, datetime, itemlink and itemlinks.

For the last, *itemlinks*, need to update the REST API.

A lot of thinking about the conception of all of these fields in the database. The goal is to have fields quick to search (index, performances).

It's on a good way and will be finished for beginning of May.


<br>

## I.2 Frontend


<br>

### I.2.a User params in items list

The code has been implemented to manage params of items list, related to the work in the backend.

<br>

### I.2.b CSV import

Many modifications in the CSV import. The design has been enhanced with the work of Sarah, ergonomist working at our partner [Probesys](https://www.probesys.com/).

The first implementation of CSV works nicely.

<iframe width="560" height="315" src="https://www.youtube.com/embed/SAtcYfFf1ME" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


<br>

### I.2.c Item display / creation

With the management of property fields types on the backend, the code of the item creation / update is in work.

It will be available in May for the tests campaign.


<br>

## I.3 Job offer (in France) by Probesys

Our partner Probesys has opened a job offer for a developer to works on FusionSuite. It's for french people, and you can find all details on [website](https://www.probesys.com/articles/probesys-recrute-une-leaddev-pour-fusionsuite).


<br>

# II. Tests campaign

The first test campaign is planned the 20 and 21 May.

The goal is to test the item lists, paging, the CSV import, the item creation and item modification.

More news in couple days and the link to register.


<br>

# V. Conclusion

The jobs continues in the good way - This is the way -



**David Durieux - Leader of FusionSuite project**
