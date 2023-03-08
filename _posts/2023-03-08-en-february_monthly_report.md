---
layout: post
title: February 2023 - Monthly report
categories: news
lang: en
---

Here is the February 2023 report.

# I.Introduction

<br>

Several parts are under development, they will not be integrated into the code repository for several weeks.

Indeed, these parts have common pieces of code and I need to move forward on each to be sure of the good cohesion between them. I will nevertheless present their current state in this monthly report.

<br>

# II. Project events

<br>

# II.1. Live coding on Twitch

Several times a week, I continue to stream live coding from the project on my [Twitch](https://www.twitch.tv/ddurieux) channel.

Don't hesitate to drop by to say hello!

<br>

# III. Development

<br>

## III.1. Back-end

<br>

### III.1.a Custom display management in the frontend

The development made it possible to improve and correct several problems, several tests were also added.

We are at the end of this part, even if there are still some possible modifications in terms of item displays.

Two displays have been introduced currently:

* *standard* display: the display of properties in a panel
* *timeline* display: the display of properties in timeline format, usable for tickets, changes...

After reflection, several other displays should be added in the coming months/years and we must be able to manage them easily, that is to say without making large database modifications each time.

For display ideas, here are a few:

* view *network bay/servers*
* view *network diagram*
* view *security with CVEs...*
* ...

<br>

### III.1.b OpenTelemetry

In the backend, and later the frontend will also be included, OpenTelemetry has been implemented.

Thanks to this system, the metrics can be sent to an APM (Application Performance Monitoring) tool allowing the health of FusionSuite to be monitored in real time.

There are 4 modes available, configurable in the configuration file, namely:

* *OTLM_DISABLED*: traces disabled
* *OTLM_NORMAL*: traces on the main key components of the backend, very resource-efficient
* *OTLM_DATABASE_QUERIES*: normal traces + traces of all queries on the database, more resource intensive and can slow down queries on the backend by a few milliseconds
* *OTLM_DEVELOPMENT*: extreme traces, usable for development and makes backend requests extremely slow


Here is a display of APM (Jaeger) with an *OTLM_NORMAL* level. The queries are not yet all optimized on this view.

<img src="/assets/img/jaeger_20230308.png" width="1300">

<br>

### III.1.c FusionInventory

As planned on the schedule (presentation last January), work on the FusionInventory agent has started in earnest.

As a reminder, modification of the data format and implementation of the REST API protocol for standardized and simplified exchange with the server.

The server precisely, **FusionSuite!!!** the code has started, the inventory is already partially recoverable, and the first bricks of data update done (in a laptop item for the moment).

Work continues on the data format on the agent side and as soon as it is more advanced (in a few days), I will be able to write the big parts of inventory management in FusionSuite.

<br>

## III.2 Frontend

<br>

### III.2.a Task/workflow management

The specifications and the beginning of the code have been done, there is still work to be done for this management of rules and workflows.

I put you an image of the trend, it's far from being finalized, so you just have to see the general principle of flows.


<img src="/assets/img/workflow.png" width="1300">


<br>

# IV. Conclusion

Several related parties, so many parallel projects. I hope to be able to merge the code in the code repositories within 2 months. We will then have almost all the essential bricks for the end of year release.

**David Durieux - FusionSuite project leader**