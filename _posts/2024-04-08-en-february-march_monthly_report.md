---
layout: post
title: February & March 2024 - Monthly report
categories: news
lang: en
---

Here is the report of the month for February and March 2024

# I. Introduction

<br>

Over the last 2 months, particular attention has been paid to the frontend (web interface).

Improving the interface is necessary, as well as its standardization so that the user can use it in good conditions, and that the code is as simple as possible so that corrections can be made easily!

We will detail all of this.

<br>

# II. Project events

<br>

# II.1. Conference in May in Lyon (France) for the JDLL

The 25th edition of [JdLL](https://www.jdll.org) will take place on May 25 and 26, 2024 in Lyon.

For the occasion, I submitted a conference entitled **Designing free software (FusionSuite) for 3 years without being released yet: obstacle course**, and you can imagine that it was accepted. So I will be on May 25 to give the conference in Lyon, I will give you more information next month.

<br>

# III. Development

<br>

## III.1. Backend

<br>

### III.1.a Miscellaneous corrections

With the focus on the frontend, the backend received some fixes, identified through intensive use of the frontend.

The corrections are manual and not yet in the repository, because they require adding tests.

Despite more than 3,000 tests, there are still cases that I had not anticipated, I remain human :D

There may be a few more fixes in April on the backend with the addition of numerous frontend tests.

<br>

## III.2 Frontend

<br>

### III.2.a Fields

A reflection on the different types of fields (string, integer, drop-down list, boolean, etc.) was carried out at the beginning of February with the aim of managing all the configurations of these fields and having **standardization** of these fields throughout the application.

A component for each type was coded, then integrated into all pages (creation and editing of types, properties, items, and even the login page).

The result is really great. There is still work to be done on these fields, notably the End-to-End testing part, with [Cypress](https://www.cypress.io/), which is progressing well but is not yet finished. I'll try to finish these tests by the end of April and push this into the code repository.


Here is what it corresponds to:

*In viewing mode*
<img src="/assets/img/frontend_fields_visualisation.png" width="752">

*In edit mode*
<img src="/assets/img/frontend_fields_edition.png" width="762">

<br>

### III.2.b Buttons & page headers

Ah the buttons!

Same as for the fields, there was a need to standardize the buttons and have their layout almost always the same.

The page headers have also been revised to provide useful and easily readable information. I'm not completely satisfied yet, so there will still be changes.

Below are some screenshots of these buttons and headers.


*List of items*
<img src="/assets/img/buttons_list.png" width="1300">
<br>
<br>
*Item creation page*
<img src="/assets/img/buttons_newitem.png" width="1300">
<br>
<br>
*Item viewing/editing page*
<img src="/assets/img/buttons_item_detail.png" width="1300">
<br>
<br>
*Viewing/item modification page, but with the item in soft delete*
<img src="/assets/img/buttons_softdelete.png" width="1300">

<br>


# IV. Conclusion

The interface is progressing well, I should be able to write the FusionSuite user documentation within 2 or 3 months \o/

It's starting to look like a finalized application!

**David Durieux - FusionSuite project leader**
