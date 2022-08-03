---
layout: post
title: July 2022 - Monthly report
categories: news
lang: en
---

This is the monthly report of July 2022, and for months since March.

# I. Introduction

<br>

## I.1. Forced break for several weeks

I haven't written a monthly report since the last written in April due to many reasons:

* in April, I hurt my back and I was in a lot of pain for 7 weeks, so not possible to code the project in this time
* not really news to communicate

<br>

## I.2. Tests campaign postponed

I had defined do a first test with users in May, but with the delay of the code, it is postponed to end of year.

<br>

## I.3. New developer from Probesys

Like I said in last monthly report, our partner *Probesys* searched somebody to develop on the project.

Good news, they find him and it's Marien.
Marien works for many years on [freshrss](https://freshrss.org/)

Welcome to him in the project and he have beginning to help us since June.

<br>

## I.4. Planning


In consultation between the team and partners in July, we had defined a new planning (it can be changed):

* first test campaign in the end of year (tickets and maybe the inventory with FusionInventory)
* first stable release begin 2023


# II. Development

<br>

## II.1. Backend

<br>

### II.1.a. Introduction

Many parts are done or in review to be integrated (it will be done in couple days).

I will explain each part, because it's the base of the FusionSuite and it's important.

All codes and features added come with many tests, to test works and test not works; the goal is to be have think to the most cases possible. 

For the moment, we have a little more than 1700 tests (and very large number of assertions, but not quantified), and run them in less than a minute :D

<br>

### II.1.b Properties

In FusionSuite, you will be able to create types (laptop, ticket, smartphone, switch, router, car...).

For theses types, you probably need to manage properties, for example *serial number*, *buy date*, *in location?*...

So you can create properties and attach them to the type.

For the properties, many fields and types of properties are possible.

For fields, we have: 

* name
* internalname
* valuetype: *boolean*, *date*, *datetime*, *decimal*, *integer*, *itemlink*, *itemlinks*, *list*, *number*, *password*, *passwordhash*, *propertylink*, *string*, *text*, *time*, *typelink*, *typelinks*
* regexformat
* unit: the unit of the value, for example seconds, Kio, Gio...
* default: the default value
* description
* setcurrentdate: works only for following *valuetype*: *date*, *datetime*, *time*
* canbenull

Like you can see, properties can be adapted to very many of cases you can need.

<br>

### II.1.c id_bytype

Our database has a table where all items are.

You can have tickets, laptops... in same table.

For performances, the partitioning will help to keep it performant (will be documented later).

But the problem is that a ticket can have some missing IDs between two tickets, because id can be used by a laptop or another item.

For that, we keep the primary id of the item and add a new id, name id_bytype and it is incremented by type.

Thus, for two consecutive tickets, the second will always be `+1` compared to the first ticket.

<br>

### II.1.d Tree items

For many requirements, like organizations, tickets categories... we need have items organized in a tree.

After some times of search, we have decided to use the `Materialized paths` method to be performant in the queries.

In the type configuration, two new fields are available:

 * tree
 * allowtreemultipleroots

Both are boolean to say if yes or no.

The `allowtreemultipleroots` permit to have a tree (so in this case, trees) to have multiple root. For example, have often it in tickets categories (many first level).

Then, in the items, you define the parent id when create the item and it generate the treepath in the database.

We have managed this `treepath` in the database to be able to have a maximum 63 levels in the tree.


<br>

### II.1.e Organizations and users

We managed the items based on organizations.

The organizations are a tree type, with only one root. All items, types, properties will need to be defined on an organization and can be tagged to be visible into sub organizations.

The users have also an organization and sub-organization visibility parameter defined.


The organizations and users are, in fact, items and defined by a type. Like this, it's like others items and you can attach properties you want on these types. For example, you can define a user manager of an organization, an address...

<br>

### II.1.f. Next features

The next features to be added are:

* rights management: manage display, create, update, delete and purge on item and on each property
* history of all changes
* audit: store all connections, create & delete data


<br>

## II.2 Frontend

<br>

### II.2.a Tickets interface designed

Marien (from Probesys), has designed an interface for the tickets. It's not the final version because can still evolves, but it's the vision we want: simple, efficient in creation and update...


<img src="/assets/img/Screenshot_2022-07-04_at_11-13-19_Ticket.png" width="1300">



<br>

### II.2.b Frameworks changed

After discussions with Marien and the POC he made, we decided together to give up Ionic/Angular because it's too heavy.

We use mainly *Angular* now. The works made before can be used because the code uses angular.


<br>

# V. Conclusion

Many changes, and the works continues.

The next monthly report will be available begin September about August month works.


**David Durieux - Leader of FusionSuite project**
