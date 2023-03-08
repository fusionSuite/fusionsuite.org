---
layout: post
title: December 2022 and January 2023 - Monthly report
categories: news
lang: en
---

Here is the report for December 2022 and January 2023.

# I.Introduction

<br>

Focus on configuration and customization!

Presentation of the 2022 retrospective and the 2023 roadmap/planning ;)

I still grouped 2 months, because the month of January was busy with the preparation of the presentation.

We will detail all this, and other things, in the rest of the report.

<br>

# II. Project events

<br>

# II.1. Live coding on Twitch

Several times a week, I continue to stream live coding from the project on my [Twitch](https://www.twitch.tv/ddurieux) channel.

Don't hesitate to drop by to say hello!

<br>

# II.2. Presentation of the 2022 retrospective and 2023 roadmap/planning

On January 12, I presented the 2022 retrospective and 2023 roadmap/planning.

The slides of the presentation are available in the section **Presentation**, or directly on the link [retrospective presentation and roadmap 2023](https://fusionsuite.org/presentation/2023-01/presentation.html).

You can check out the 2023 roadmap below, in black *FusionInventory* (quite related with FusionSuite) and blue *FusionSuite*.

<img src="/assets/img/planning_2023.png" width="1300">

A little useful information, we are going to do a user test around June in order to have the first user feedback and which will allow us to adjust the interface before the release in September/October.

<br>


# III. Development

<br>

## III.1. Back-end

<br>

### III.1.a REST API Documentation

REST API documentation improved, some parts were wrong.

I have a topic on this so I can dynamically test the API documentation on every code commit to check for consistency with the code.
This subject is not simple, but it is progressing, I hope to have something functional by this summer.

<br>

### III.1.b Personality display management in the frontend

In the backend, it has been added (not yet fully finalized), the personalized management of the display for the frontend, namely:

  * menu customization
  * personalization of items according to the types

To see the renderings, go further down in the frontend part.

There is still some REST API code, testing, and documentation left.

<br>


## III.2 Frontend

<br>

### III.2.a Property management

The addition of management and configuration of properties has been added (configuration part).
It allows you to add properties and set them.

<img src="/assets/img/frontend_properties_202302.png" width="1300">


<br>

### III.2.b Added display of items with the timeline

Some types require having a timeline, such as support tickets, change management...

You can get a preview of the version, which is still in development:

<img src="/assets/img/frontend_timeline_202302.png" width="1300">


### III.2.c Type management

Type management has been added to configure the display of items.

It allows you to add the desired properties, group them in sections, choose in which menu to put it...

<img src="/assets/img/frontend_types_202302.png" width="1300">

<br>

### III.2.d Menu management

The menu has finally been worked with personalized management.

It contains 2 sections:

* the *Business* view: displays items grouped in fully customizable menus (categories, icons)
<br><img src="/assets/img/frontend_menu_business_202302.png">

* the *Personal* view: allows you to bookmark items from the business view
<br><img src="/assets/img/frontend_menu_personal_202302.png">

For a few days, the configuration part in the Business menu does not please me too much, I am thinking of putting a button to switch FusionSuite to *Configuration* mode to completely separate it from the standard use part. To be continued in future reports.

<br>

# IV. Conclusion

The project is going well, the frontend part is progressing well too, given the stability and simplicity of the backend, it can be done really quickly (much faster than I thought and that's really cool).

**David Durieux - FusionSuite project leader**
