---
layout: post
title: February 2022 - Monthly report
categories: news
lang: en
---

This is the monthly report of February 2022, 45 days after announcement of the projet.

Many things done and it's really cool!

So let's go ;)

# I. Development

<br>

## I.1. Backend

<br>

### I.1.a. Rules

I started speech about rules in the last monthly report and so I will continue for this month.

The first implementation of rule actions (actions played after modifications in the backend) is on the code repository.

The code works and when creates an item (for example, a server), an email is sent, a host is created into Zabbix monitoring solution (and the Zabbix id is stored in a property of the server in FusionSuite).

Many tests are added for this part, but need little modifications to be tagged as stable!

One element in specification, not yet added) is the possibility to execute the actions in asynchronous to keep quick execution of add/update/delete an item. We can have an action script takes many seconds to execute.

<br>

### I.1.b Cli

Code has been written to have a *cli* for helping the administrator to manage tasks.

The *cli* can be used, for the moment, to:

* create and manage connection to database. It's possible to create many databases connections and switch from on to another very simply.
* install the backend (create database structure and fill data).

For the cli usage, there are 2 modes:

* interactive mode (cli ask questions, display help)
* non-interactive mode, with arguments to pass to the command (useful when integrate into automated scripts)


The documentation has been written too: [cli documentation](https://fusionsuite.org/documentation/administration_tasks/backend/installation_update/2_installation/).

<br>

### I.1.c Database types

I have enhanced the tests to run on many databases and many versions.

The tested and supported databases, for the moment, are:

* MySQL: 5.7 / 8
* MariaDB: 10.4 / 10.5 / 10.6 / 10.7
* PostgreSQL: 11 / 12 / 13 / 14

The cli part is not yet added for SQLite.

For MS SQLSERVER, I have troubles with UTF-8 support and so not have found the right method to use it correctly. If someone has skills on it, contact us (find information on the website).

<br>

### I.1.d User params

The database part and endpoint has been started to be implemented in the backend to manage the userparams (needed for the frontend).

<br>

## I.2 Frontend

Much information and news about the frontend this month ^_^.

<br>

### I.2.a Tests


Begin add tests of the frontend to check security dependences, success build of the website.

<br>

### I.2.b Ionic 6 / Angular 13

I have upgraded the framework we use to Ionic 6 and Angular 13. Better performances and new features we will be able to use.

<br>

### I.2.c Design

The design works has been started with Sarah, ergonomist working at our partner [Probesys](https://www.probesys.com/). After 3 sessions about item list, the first implementation has started.

This is the before/after design on items list:

<iframe width="560" height="315" src="https://www.youtube.com/embed/cOiVJwYPWlw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### I.2.d User params

User params are currently to be added, like order of columns, display or not a column, number of elements to display (pagination).

The code works, can be saved into the backend and loaded when load the frontend.

This part will be finished in March.

<br>

### I.2.e CSV Import

The CSV import feature has been written. It permits to load a CSV file, define the properties to fill for each column (the *import model* will be stored in userparams, not yet coded) and import into the backend.


The feature works nicely.

<img src="/assets/img/post_20220228_csvimport.png" width="1300">

<br>

## I.3 Job offer (in France) by Probesys

Our partner Probesys has opened a job offer for a developer to works on FusionSuite. It's for french people, and you can find all details on [website](https://www.probesys.com/articles/probesys-recrute-une-leaddev-pour-fusionsuite).


<br>

# II. Tests campaign

Liking introduced in January, the first tests campaign is planned in May - June. I guess the inscriptions will be communicated in the next monthly report (so end of March).

<br>

# III. Communication

<br>

## III.1. Website/more team people

The website has been updated, *Maël Jeuffrard* and *Laurent Lienhard* has been officially added to the team ^_^. Welcome to them!

<br>

## III.2. Documentation

The documentation continues to be written. We had splitted it in three parts:

* End user guide
* Administration tasks
* Developer


You can find at the [URL](https://fusionsuite.org/documentation/).

<br>

# IV. Structure for the project


I'm thinking about creating a structure for the FusionSuite project (foundation, association..).

The reasons is to:

* permit receive donations
* redistribute donations to the libraries/projects we use in the frontend and backend (often forgotten in donations by users, but very important to support them for their works)
* pay a security company (or perhaps find a company offers that) to audit the code in the end of year to be most secure possible
* pay trips for presentation or have a booth in trade shows
* ...

No provisions of service planned with this structure, it will be the role of partners ;)

<br>

# V. Conclusion

The jobs continues and begin to works in all parts of the project and the tool, YEAH



**David Durieux - Leader of FusionSuite project**
