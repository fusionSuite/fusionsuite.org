---
layout: post
title: August 2022 - Monthly report
categories: news
lang: en
---

This is the monthly report of August 2022.

# I. Introduction

<br>

August was a good month and many parts of the software continues to be added at a good pace.

The base of the software begins to be a rock.

<img src="/assets/img/IMG_0791-1024x768.jpg" width="1024">

*Credit: [https://www.thiscobhouse.com](https://www.thiscobhouse.com)*


# II. Development

<br>

## II.1. Backend

<br>

### II.1.a Docker env for developers

Marien has added code for developers to run the backend into a docker (container).

<br>

### II.1.b Roles and permissions

Near to be finished, David has added code to manage roles and permissions.

The role is defined by:

 * a name
 * a permission for structure (types, properties, roles, rules...) with possible values: **grant**, **none**, **custom**
 * a permission for the data (all items): **grant**, **none**, **custom**


If the permission for structure is *custom*, have a sublevel of permissions. For each endpoint (*config/type*, *config/properties*...), we define:

 * view permission: **grant**, **none**, **custom**
 * create permission: **grant**, **none**
 * update permission: **grant**, **none**, **custom**
 * soft delete permission: **grant**, **none**, **custom**
 * delete permission: **grant**, **none**, **custom**


If some of these permissions are defined in *custom*, we have a third and last level of permissions. The ids of the endpoint (for examples the type *Organization*, the type *Users*, the property *address*) are defined:

 * view permission: **true** / **false**
 * update permission: **true** / **false**
 * soft delete permission: **true** / **false**
 * delete permission: **true** / **false**

For the roles, it will not be possible to create a role & permissions with more permissions the current user have. It's a security behavior.


For the data, if defined as *custom*, we define the permissions of all items of a type (*Organization*, *Users*, *Laptop*, *Tickets*...):

 * view permission: **true** / **false**
 * create permission: **true** / **false**
 * update permission: **true** / **false**
 * soft delete permission: **true** / **false**
 * delete permission: **true** / **false**
 * option to manage properties of items as custom, if not defined, use the view and update permission defined for the items of the type.


If the properties of items is defined as *custom*, you must define permissions to each property of the type of items to:

 * view permission: **true** / **false**
 * update permission: **true** / **false**


With an example, it can be better to understand:

You can have tickets, refuse to create it, but can view and update it only, and not have permission to view the property related to the location.


**We have defined 1 user = 1 role**. We started thinking to have 1 role per organization (so multiple roles per user), but not sure yet about that.


The code is near to be finished and more than 200 tests added.

<br>


### II.1.c Performances of the database

Many big parts begin to be added in the backend, David has coded a script that analyze all queries to detect queries not used indexes correctly or missing, in the goal to optimize them. With the simplicity of the database schema, putting the right indexes is simple.

This task will be executed many times in the development process to optimize as possible the queries.

Only with the tests, we execute more than 25 000 SELECT request in the DB in 1 minute.

Performance tests have begun to be written, but we will explain them in a future monthly report ;)

<br>


### II.1.d FusionInventory inventory

The specifications about the new FusionInventory protocol (version 3: JSON format and containers structure) continues, but require again couple weeks.

<br>


### II.1.e First bugs

Marien works on the frontend, he discover some problems in the backend to get data in specific cases. Code and tests will be added in the September month to manage these cases.

<br>

## II.2 Frontend

<br>

### II.2.a Docker env for developers

Marien has added code for developers to run the frontend into a docker (container).


<br>

### II.2.b Organizations

Marien has coded the pages to view, create and delete organizations.


<img src="/assets/img/Screenshot_2022-09-04_at_08-23-05_Organizations.png" width="1116">


<br>

### II.2.c Users

Marien has coded the pages to view, create and delete users.

<img src="/assets/img/Screenshot_2022-09-04_at_09-01-00_New_user.png" width="1116">


<br>

### II.2.d Interactive messages

Interactive messages have been added when do an action and the software need to prevent the user for some reasons: 

* item created successfully
* item updated successfully
* item deleted successfully
* any error messages from the backend (no rights, field missing...)

<br>

### II.2.e Translation

Marien has started the translation of the interface and added the command to extract strings to be translated in the *Makefile*.

<br>

### II.2.f Internal improvement

Marien has made modifications to re-organize the code for:

* manage backend API version (currenctly *v1*)
* backend API queries
* the authentication
* the data models like items/users/organizations, the properties (typescript interfaces)

This reorganization will help to manage all items and types of items in FusionSuite (laptop, tickets, contracts...).

<br>

### II.2.g Menu

We written specification about the menu [issue #60](https://github.com/fusionSuite/FusionSuite/issues/60). Like we can have many and many type of items, try to make a list and dispatch them the best possible to have a simple menu.

<br>

### II.2.h End to End tests

Marien has begun implement tests on the frontend.

This kind of tests starts a browser engine (chrome, firefox...) and does the actions like a normal user and check if actions works well (fill a form, click on a button, check the interactive message...).

These tests will prevent problems for the user when the developers add/update pieces of code.

Quality of FusionSuite is one of the priority ^_^

<br>


# V. Conclusion

Many changes, and the works continues.

<img src="/assets/img/Worker.svg" width="300">

Thanks to our partners [PROBESYS](https://www.probesys.com/) and [dcs EASYWARE](https://www.dcsit-group.com) for the time spent on the project.


**David Durieux - Leader of FusionSuite project**
