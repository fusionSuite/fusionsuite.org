---
layout: post
title: August & September 2023 - Report of the month
categories: news
lang: en
---


Here is the report of the month for August and September 2023.

# I. Introduction

<br>

I couldn't do the August one, the month of September was very busy personally, I had to postpone and group the 2 months.

Topics that we will cover in this report:

* feedback from the first test by users
* implementation of workflows
* setting up item search
* planning release

Here is the menu for this report.

<br>

# II. Project events

<br>

# II.1. Community testing

The first user test was carried out **from August 31 to September 2**.

Obviously, not everything is finalized, so some feedback was logical, others more interesting.

Here is the feedback, with my comments in italics:

* menu sidebar is nice and easy to use
* the text (of the menu for example) seems too big, you need to reduce it a little * - after checking, this is indeed the case -*
* the highlighting of the menu item you are in is difficult to read, try just putting a bar on it (underline) *- I will do some tests and will certainly ask for feedback on the Discord server -*
* the red/pink color of the configuration menu is not unanimous
* various problems in user creation in the frontend (web interface)
* the possibility to change the user password is missing *- normal, not done yet -*
* possibility of putting personalized text on the login page and at the footer, text required in certain countries
* management of encoding in relation to language
* management of the display of dates/time with the timezone * - haven't looked at this point yet -*
*currency management required
* ticket conversations don't work * - I must have broken something, I hadn't run any tests on it yet so not abnormal -*
* creation of types: put *required* in red and behind the title
* creation of types: need more space between fields
* how to manage the merger of companies, and therefore of 2 FusionSuite instances * - not yet thought about these cases -*
* authentication management via LDAP, SAML, Azure AD and OAuth * - this is planned -*
* no rights/roles management * - this is done in the backend, but not yet in the web interface -*
* migration from GLPI to FusionSuite *- planned for December -*
* interface translations * - this is done at the end, the translation can be done by the community next December / January -*
 

More related to FusionInventory:

* various Windows agent related issues have been reported and fixed
* inventory partially works in FusionSuite
* several field mapping issues * - currently being integrated and some workflow issues, see the chapter later -*


This first test allowed me to raise a few points that I had not yet thought about, it will help refine the display.

We will plan another test, rather at the end of November.

<br>

# III. Development

<br>

## III.1. Backend

<br>

### III.1.a Workflow

The workflows are a little more complex than I thought. There is already quite a bit of working code (FusionInventory, webhook, etc.) but others still require a little work. The slider between ease of use and power/complexity of workflows necessarily takes time.

Despite that, it works more in the direction I want, so that's a good point.

**The workflow part is the most important building block of FusionSuite.**

<br>

### III.1.b Search

I started to develop the item search.

This project is quite well advanced and I am currently writing tests in parallel with the code.

<br>

### III.1.c Planning

At the backend level, there are still 2 major features to complete for the release:

* workflow: planned end in December (very large chunk)
* search: planned end in October

<br>

## III.2 Frontend

<br>

### III.2.a Workflow management

The interface has evolved, we have a menu to configure each block, there is still ergonomic work to be done on it to be as simple as possible to use, but the first draft is a good working basis.

<img src="/assets/img/2023-10_workflow_general.png" width="1300">

<img src="/assets/img/2023-10_workflow_block-config.png" width="1300">

On a technical level, I had to separate all the blocks in the code to greatly simplify the code and therefore the maintenance for later.


<br>

### III.1.b Search

I started to develop the item search.

This project is quite well advanced and I am currently writing tests in parallel with the code.

<br>

### III.1.c Planning

At the backend level, there are still 2 major features to complete for the release:

* workflow: planned end in December (very large chunk)
* search: planned end in October

<br>

## III.2 Frontend

<br>

### III.2.a Workflow management

The interface has evolved, we have a menu to configure each block, there is still ergonomic work to be done on it to be as simple as possible to use, but the first draft is a good working basis.

<img src="/assets/img/2023-10_workflow_general.png" width="1300">

<img src="/assets/img/2023-10_workflow_block-config.png" width="1300">

On a technical level, I had to separate all the blocks in the code to greatly simplify the code and therefore the maintenance for later.


<br>

### III.2.b Search

The search part of the interface allows you to do somewhat complex searches (contains, greater than, starts with...) depending on what you are looking for (name, property).

I implemented 2 ways to use search:

* directly in the search bar in text format by typing the fields (with suggestions) and values. This bar is accessible directly by pressing the **/** key.
* an advanced search that guides with the choice of field, operator and value

Everything is not finished yet, but rather very advanced on the interface side and will be finalized in October.

<img src="/assets/img/2023-10_search-general.png" width="1300">

<img src="/assets/img/2023-10_search-advanced.png" width="1300">


<br>

### III.2.c Display

I have started to improve all the little things in the interface that need a pass of tweaking, improvement, the work will continue over the next 3 months.

<br>

### III.2.d Planning

At the frontend level, it remains to be finished for the release:

* workflows: planned in December
* research: planned in October
* import of CSV files: code done, integration in October/November
* role management: planned in November
* various interface/design improvements
* documentation
* translation


<br>

# IV. Conclusion

The project is nearing completion for the first release, after more than 2 years of development, I can't wait to put it all in your hands \o/.


**David Durieux - FusionSuite project leader**
