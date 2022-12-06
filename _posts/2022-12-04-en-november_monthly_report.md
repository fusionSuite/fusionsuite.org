---
layout: post
title: November 2022 - Monthly report
categories: news
lang: en
---

Here is the November report.

# I.Introduction

<br>

Improved tests, change management, puzzles on tests launched by github.

We will detail all this, and other things, in the rest of the report.

<br>

# II. Project events

<br>

# II.1. Live coding on Twitch

Several times a week, I continue to stream live coding from the project on my [Twitch](https://www.twitch.tv/ddurieux) channel.

It's always a pleasure to stream code development. This month it was quite abstract because centered on the backend.

In December, most of the work will be on the frontend, and especially during the Christmas holidays, so it will be more visual ^_^

Don't hesitate to drop by to say hello!

<br>

# II.2. Project anniversary on January 12, 2023

The FusionSuite project will blow out its first candle on January 12th.

I talked about it in the previous report, but I confirm the information:

* date: **Thursday, January 12 at 8:00 p.m. (France timezone)**
* location: on [Twitch](https://www.twitch.tv/ddurieux)

<br>


# II.3. Provision of servers by our partner DCS EASYWARE

Our partner [DCS EASYWARE](https://www.dcsit-group.com/) has provided us with 5 servers to begin performance testing and possible configurations, namely:

* application performance tests under load (SQL queries, code optimization...)
* load balancing tests, with each possible type of distribution
* High Availability (HA) tests

For the last 2 points, it will be easy to set up once in production at home, because the backend has been designed and architected for a normal mode (1 server), but also for these modes, useful for larger environments.

I will tell you about it in a next report of the month ;)

<br>

# III. Development

<br>

## III.1. Back-end

<br>

### III.1.a Improved testing

A lot of time has been spent on improving the tests:

* renaming test folders *RESTAPI*
* implementation of the *lint* (eslint) of the tests to have clean code (even for tests)

This represents tens of thousands of modified lines, but we have rather clean tests (2400 tests).

<br>

### III.1.b Github actions

Lots of hours wasted (about 20 ;/ ) in solving github actions.

Github actions are the tests run when you commit to the repository to check that you haven't broken anything.

In November, a new system image was released by Github (Ubuntu 22.04).
We used to run php-fpm tests in the `home` folder and it is now protected in this new version.

After many tests, in the end the only solution is to move the backend files to `/var/www/` so that *php-fpm* can access the files.

<br>


### III.1.c PHP 7.4

In November, **PHP 7.4 passed EOL**.

This version has been removed from the backend, so PHP 8.0 and 8.1 are recommended (required actually).

<br>


### III.1.d Change management

Change management has been implemented, this is the history of changes.
When you change the name of an item, its property...


These changes are only accessible by retrieving an item with its id.

When retrieving multiple items, the changes will not be in the data.

The historical data is:

* userid: user id
* username: the login of the user (useful in case the user is deleted from the database)
* model_type: this is the model/endpoint
* model_id: the id of the item
* property_name: the name of the property in the case of a modification of the property of an *item* model
* property_id: property id
* set_by_rule: say if it was modified by a rule or not
* message: the message, for example *admin changed "priority" to "high"*
* old_value: the old value
* new_value: the new value
* created_at: the date/time when the modification took place


After several days of reflection, during the final deletion, it was decided to put in *old_value* the list of all the fields of the item. This will allow an admin to be able to find the information that was there before deletion. I've had this several times, and it's really helpful.

I don't know yet if there will be an admin page specifically for this or if it will remain manual in the database.

<br>


### III.1.e Eloquent Upgrade

Eloqent has been upgraded to version 9.x, the tests all pass so no side effects detected.


<br>

## III.2 Frontend

<br>

### III.2.a Introduction

Efforts were made in November on the backend to stabilize and add the changes, so very few changes on the frontend.

<br>

### III.2.b December program

Tickets have been coded quite a bit over the past few months.

I realize that the code is quite large, so it will be split into several parts, namely:

1/ setting up the conversation part in a specific component, because it is also used for the history (types, computers, etc.)
2/ property management code (+ history)
3/ type management code (+ history)
4/ code for importing templates (tickets...)
5/ ticket code


<br>


# IV. Conclusion

The project is going well, we will pass a stage in December by advancing on the frontend following the stabilization and management of changes in the backend.

**David Durieux - FusionSuite project leader**
