---
layout: post
title: March / April / May / June 2023 - Monthly report
categories: news
lang: en
---

Here is the report for the months of March, April, May and June 2023.

# I.Introduction

<br>

There hasn't been a report of the month for 4 months, not that the project isn't progressing, on the contrary, but these last few months have been extremely busy for me (personally and professionally).

Without further ado, let's kick off this report with quite a bit of information.

<br>

# II. Project events

<br>

# II.1. Live coding on Twitch

Several times a week (but not necessarily every week, I told you, it's busy anyway :p), I continue to stream the project's live coding on my channel [Twitch](https:// www.twitch.tv/ddurieux).

<img src="/assets/img/twitch_01.png" width="600">


Don't hesitate to stop by to say hello and to show you the advanced work!

<br>

# II.2. Ongoing tests

The portal, still in design, is evolving quite a bit.

Exclusive testing with our partner [DCS EASYWARE](https://www.dcsit-group.com/) is currently underway.

This relates to:

  * change management configuration
  * first feedback from the interface, to start adapting / correcting certain parts
  * use of the [REST API](https://fusionsuite.org/documentation/restapi/) backend and documentation for FusionSoftwares (see point II.4)

<br>

# II.3. Community testing

The portal is therefore still in design / development, it is still progressing quite a bit, but it is still really early for you to test it.

A first session will be organized for those who wish in August. We will talk about it in the report at the beginning of August for registrations.

A ready-made version on our servers will be assigned to you personally.
A common version with the other testers will be made available to you.

The purpose of these tests is to discover the interface / the use, and to give us feedback on the difficulties, the possible improvements... in order to make FusionSuite usable at best ** for its first release, still planned end of this year**.


<br>

# II.4. FusionSoftwares

The site hasn't launched yet (or even made the logo), so I'll talk about that right here.

The FusionSoftwares project, presented in January, was only due to start in August.

Under the impetus of our partner [DCS EASYWARE](https://www.dcsit-group.com/), our partner's resources have been allocated to this project and it has already made quite a bit of progress.

As a reminder, **FusionSoftwares** aims to collect software, software versions, CVE... and to centralize the data.

Then the users, scripts... will come to get this data and will be able to process it. In our case, a script in FusionSuite will tag the software reassembled by FusionInventory so that technicians / administrators can see obsolete software and/or software containing vulnerabilities in their fleet.

<br>

# III. Development

<br>

## III.1. Back-end

<br>

### III.1.a Modification of prerequisites

PHP 8.0 will be obsolete on November 26, the required versions will be PHP 8.1 or 8.2.

The documentation has been updated, the prerequisites in the backend as well, as well as the tests.

<br>

### III.1.b Improved REST API documentation

The API documentation (for developers) has been improved to be more readable (modification of styles).

There are still parts to improve, to restructure, work that will be done soon.


<br>

### III.1.c Improved code quality

A branch is in progress to bring the code to the maximum level of [PHPStan](https://phpstan.org/).

This ensures better code and prevents several bugs.


This branch should be finalized in September (there are currently 800 issues left out of the 2000 identified at the beginning).


<br>

### III.1.d Improved item properties

Several item property improvements have been made:

* improved and fixed default values for *itemlinks* and *typelinks*
* added *allowedtypes* for *itemlink* and *itemlinks*, which allows to define the types of items allowed in these properties
* modification of *internalname* where the generation now uses a *uniqid* in order to avoid collisions and therefore errors


<br>

### III.1.e Managing display settings

Endpoints on the REST API have been added in order to be able to store and manage the display in the frontend:

* menu management
* management of personalized menus
* management of panels (in the display/modification of items page)

TODO

<br>

### III.1.f Workflows / FusionInventory

The specifications have been done, it took much longer than expected, but is an essential part of FusionSuite.

The code started at the beginning of July and should be finalized at the end of July.

These workflows are composed as follows:

* *trigger*: these are triggers
   * *create*: triggered when creating item
   * *update*: triggered when modifying an item (modifying name, properties)
   * *softdelete*: triggered when deleting item
   * *delete*: triggered when permanently deleting an item
   * *datetime*: triggered at a scheduled date and time (event)
   * *webhook*: triggered by a simple web request (usually another software)
   * *fusioninventory*: triggered during a FusionInventory inventory (inventory that arrives in the backend)
* *engine*: these are bricks that perform various operations on the data
   * *checkcriteria*: allows you to check such and such a value (in an item, item property, or in the inventory FusionInventory)
   * *getdata*: allows you to take a value and store it in a variable that can be used in the workflow
   * *renamedata*: allows you to modify a value (from a *getdata*) via a fixed value, a regex...
   * *searchitem*: allows you to search for an item via search parameters (field, operator, value)
   * *foreachfusioninventoryitem*: allows processing after this block for each inventory item (for example when you have several hard drives)
* *actions*: allows you to modify the data in the database... :D
   * *actionscript*: allows to launch an action script (send mail notification, send slack notification, create host in Zabbix...)
   * *createitem*: allows you to create a new item
   * *updateitem*: allows you to modify an item
   * *fusioninventoryanothertype*: allows you to continue processing the FusionInventory inventory for another item (for example, after the computer, we will process the processors)
   * *associateitemtoproperty*: allows you to associate an item with the property of another item previously managed by another workflow
   * *createevent*: allows you to create an event at a date time and which will be used for the *datetime* trigger seen previously


<br>

## III.2 Frontend

<br>

### III.2.a Menu management


With the code in the backend for menu management, they are now developed in the frontend.

There are 3 menu sections, fully configurable:

* *personal*: these are the menu items that you can define as personal, they will be accessible by default when you log in
* *business*: these are the grouped items that will be defined by the administrator via the interface
* *configuration*: these are the items for configuring FusionSuite, accessible via specific rights

<hr>

Assignment of an item type (here laptops) in the *Assets* menu:
<img src="/assets/img/menu_config.png" width="1300">

<hr>

Display of the 3 menus:

<img src="/assets/img/menus.png" width="1000">

<hr>

Visualization of the personal menu in smartphone format:

<img src="/assets/img/menu_custom_mobile.png" width="466">


<br>

### III.2.b Management of item panels

For each type of item (tickets, laptops...), it is possible to create several panels and put certain properties in them. This is done through a drag and drop in the item type configuration:

<img src="/assets/img/panels_config.png" width="1300">


<hr>

In the item, we have the properties classified in the panels:

<img src="/assets/img/panels_item.png" width="1300">


<br>

### III.2.c Workflow management

Workflow management has been specified, work on the interface has started to evolve, here is what it looks like now:

<img src="/assets/img/workflow_20230706.png" width="1300">

These workflows are managed in the configuration of each type.


<br>

# IV. Conclusion

Again sorry for the delay of this report, the development has been privileged to the communication. See you at the beginning of August ^_^.


**David Durieux - FusionSuite project leader**