---
layout: post
title: October 2023 to January 2024 - monthly report
categories: news
lang: en
---

Here is the monthly report for the months of October 2023 to January 2024. Yes, that's 4 months in one go... sorry!

# I. Introduction

<br>

After 4 months without news (we will come back of the reasons), here is this new report of the month.

But what happened?

There are multiple reasons for the slowdown at the end of 2023, both in terms of communication and code (obviously, it is a bit related):

* at the beginning of November, not enough news to justify a monthly report
* demotivation in November and first half of December; in hindsight, several reasons:
   * the fact of not having finished FusionSuite & FusionInventory in my planning forecasts demotivated me
   * 2 months of continuous rain (there is a monsoon in France now?) which does not help morale
   * the workflow code is more complex than expected and making it simple is really complicated, I paused it for a few weeks/months
* long days at work which also exhausted me a little
* a somewhat complicated personal situation
* management of the community translation of the StarCitizen game (it changed my mind)


Looking back on the development of the last few weeks, I realized all the complex parts that I have already implemented and which work very well, it is good for morale.

For the release date, we're going to try for this summer, hoping that it's good, but it's possible that it will slip a little. There are still workflows to finalize, ongoing focus on taking care of the web graphics part (frontend), finishing inventory management with FusionInventory, finishing version 3.0 of FusionInventory, documentation (but this will mainly be done at the end) , rights management in the web interface...

So yes, there is still work to be done, but things are progressing.

<br>

# II. Project events

<br>

# II.1. Database performance and load

In January, I entered a lot of data (50k users, 20k tickets).

After tests in a standard situation, the database remains responsive, which is rather good news; a test with even more data will be carried out in February.

The worst case, i.e. listing tickets by 100, highlighted performance problems: **8500 SQL queries for 8.5 seconds** of loading.
This was obviously not acceptable, but normal at this stage of the project, everything is not yet optimized.

Changes have been made to use *Eager Loading*. Thanks to the 3000 backend tests, I was able to correct the code so that all the tests returned to green, because it had broken a very large part of the tests.

Finally, we arrive at **53 requests for 0.5 seconds (500 ms)** of loading. It can still be optimized and it will be in February, but we are already in a much more viable scenario (better weather, reduction in server resources used, etc.).

This work required many days and a lot of thought to optimize as best as possible during the month of January.

<br>


# II.2. Design & use of the web interface

The backend is relatively stable and has a head start in maturity compared to the web interface.

The focus was placed at the end of December on the frontend to, first of all, correct the numerous parts which were working poorly or not at all.

There are still quite a few features to add on the web interface side.


<br>

# III. Development

<br>

## III.1. Backend

<br>

### III.1.a Modification of prerequisites

PHP version 8.3 is supported.

Version 10 of Eloquent has been integrated.

The libraries (dependencies) have been updated.

<br>

### III.1.b Search

The research part has been finalized, as have the numerous tests.

You can search for an item based on its properties. This already allows you to do most of the item searches.

Some searches will not be possible with the current code, particularly on inventories with sub-sub-sub items. I'll need to do some testing, but there are 2 possible solutions:

* via workflows, the addition or update of linked sub-elements could be copied to the main element to do research on it (a sort of summary on which we can do research)
* modify the search to authorize multiple sub-level searches with a high depth level, this could have an impact on performance (to be seen)

I will keep you informed of the results of the tests and the decision.


<br>

### III.1.c Importing templates

As you may know, or perhaps not at all in fact, in FusionSuite we create its item types, its properties...

This can be long and not necessarily simple for everyone, so this configuration can be imported via a JSON format file.

Several fixes have been made. The incident management template has been improved and tested, it serves as a reference for me. Tests have also been added to prevent errors that I may have had.

<br>

### III.1.d Performance improvement

As explained at length previously, performance has been improved in the backend, it is more responsive in data retrieval.

<br>


### III.1.e Data migration scripts

Data migration scripts have started to be written. This improves performance and features on the frontend side which are essential; It’s simpler when there’s lots of data.

I started with GSIT (9.5) and GLPI (9.5), there will be other market tools supported later.

The import of user accounts is almost finished.

I then focused on the tickets: it's the most complex. In this case, you must retrieve the life history of the ticket and inject it through the correct user account and with the correct dates. Ultimately it's a little easier than I thought, and it's 70% coded. The other types will remain (IT parks, changes, etc.), there is still work to be done, but it is rather encouraging.

<br>

## III.2 Frontend

<br>

### III.2.a Search

The research is finalized and corresponds to what I wanted (fortunately :p).

It can be used by mouse lovers as well as keyboard lovers :D

In keyboard mode, it is very quick to use filters.

<img src="/assets/img/2024-02-08-search.png" width="1300">

The search saving is missing, which will be added in the coming weeks (with the saving of columns, filters, etc.).

<br>

### III.2.b Rework of the menu in smartphone mode

The menu works quite well in desktop mode, however in smartphone mode it is unusable.

The redesign of this display has been carried out. The result is pretty clean and it's great.

Some screenshots to show you the result:

<img src="/assets/img/2024-02-08-menu-smartphone-personal.png" width="360">

<img src="/assets/img/2024-02-08-menu-smartphone-business.png" width="360">

<img src="/assets/img/2024-02-08-menu-smartphone-configuration.png" width="360">

<br>

### III.2.c New design of the login page

The login page was broken and not pretty at all.

Its design has been completely revised (desktop and smartphone).

To please you, a screenshot of this login page:


<img src="/assets/img/2024-02-08-login-page-desktop.png" width="1300">

<img src="/assets/img/2024-02-08-login-page-smartphone.png" width="360">


<br>

### III.2.d Improvement of the search page / list of items

A lot of work has been done to improve the usability of lists, actions, etc... this work is not finished and several features have not yet been implemented.

I add them little by little.

<img src="/assets/img/2024-02-08-itemslist.png" width="1300">

<br>


# IV. Conclusion

Despite a lack of motivation, the features are arriving and FusionSuite is becoming more and more mature for the release.

There is still work to be done, of course, and I am very motivated for this final stretch.

For the next report of the month, which will arrive at the beginning of April, I should have some nice screenshots of the interface to show you \o/

**David Durieux - FusionSuite project leader**
