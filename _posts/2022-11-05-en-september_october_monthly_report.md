---
layout: post
title: September and October 2022 - Monthly report
categories: news
lang: en
---

Here is the report for September and October combined.

# I.Introduction

<br>

I gather September and October in a single report, the 2 months have been quite busy.

Among the big events, we can cite the *withdrawal of the company Probesys* from the project, my *COVID which confined me to bed for a while*,
the backend code and *advanced ticket management code in the frontend*.

We will detail all this later in the report.

<br>

#II. Project events

<br>

## II.1. Removal of Probesys from the project

In September, several meetings took place between me (David Durieux) and Probesys.

At the end of September, they decided to abandon the project for various reasons of their own.

We decided to meet again from time to time in order to discuss the evolution of the FusionSuite project and the ticket management software that they are going to develop.

I thank them for the work done on the project.

<br>

# II.2. Live coding on Twitch

Several times a week, I stream live coding from the project on my [Twitch](https://www.twitch.tv/ddurieux) channel.

I wondered if it was interesting for people and in the end it seems so, and for several reasons:

* for developers, they can see the code writing and development process
* for (future) users, what FusionSuite will look like
* intervene to add features while I'm coding (it happened twice in October on tickets)
* I can ask for opinions on a design, colors...
* discuss the project

I'm very happy to stream, it creates a pretty strong link with the community, don't hesitate to come ;)

<br>

# II.3. Project anniversary on January 12, 2022

The FusionSuite project will blow out its first candle on January 12th.

I'm preparing a live with a presentation of the work of the past year, the difficulties, the schedule changes, a demo of the development version.

<br>


# III. Development

<br>

## III.1. Back-end

<br>

### III.1.a New cli option: database reset

For end-to-end testing of the frontend, we needed to be able to simply drop all the tables and replay the install.

This command is now integrated into the `php bin/cli reset` cli.


<br>

### III.1.b Roles and permissions

As specified in the August report, this functionality is finished and has been integrated.


<br>


### III.1.c Audit type log

Audit logs have been integrated into the backend. All additions, modifications, deletions, connections (ok or fail) are logged in the database and accessible via the REST API.

Here is the [documentation link](https://fusionsuite.org/documentation/restapi/#api-LogAudits-GetLogAudits) to query the backend.

<br>


### III.1.d New type option: unique name

There are certain types of items that must have a unique name, for example user accounts.

This option has been added in the type configuration.

While writing this paragraph, I realize that there has been a mistake in the REST API documentation. Correction to be expected.

<br>


### III.1.e Token request (login) and token refresh

The endpoint to log in and to refresh the token was complex, even more so because it was in the same endpoint.

These 2 features have been separated into 2 endpoints.

For the refresh of the token, we have improved security by requiring the valid JWT token (signature) even if expired (this is also why we need to refresh the token) as well as the refresh token .

[REST API documentation](https://fusionsuite.org/documentation/restapi/#api-Authentication-PostRefreshToken) available.

The refresh token is a bit light in number of characters, a Pull Request will be made to make it more complex.

<br>

### III.1.f Management of passwords and password hashes

A Pull Request is in progress to manage the passwords (encrypted) in the database, as well as the password hashes (for the user account password for example).

<br>

### III.1.g A word about testing

We currently have a total of **2257 tests**.
Execution takes about 2 minutes (there are pauses due to date/time tests).

The backend is coded in *PHP* and the tests in *Javascript*.

Fun fact, we have more code for the tests (58%) than the code itself (34%), inevitably the use of frameworks (Slim & Eloquent) helps to reduce the backend code.


<br>

##III.2 Frontend

<br>

### III.2.a End-to-end testing

End-to-end tests that simulate a user in the browser have been implemented. We use [Cypress](https://www.cypress.io/).

<br>

### III.2.b HTTP Interceptor and token refresh

Currently, the TOKEN provided by the backend during login expires after 20 minutes for security reasons.

When it expires and a request is made, it returns an error related to the token, and the role of the HTTP Interceptor is to request a new token again using the refresh token. Once the new token is received, the request is sent back to the backend with this valid token.

The system works perfectly and it is transparent for the user.

<br>

### III.2.c Ticket management

Ticket management is under development.

Below is a video of the work in progress.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9_Bv43gFNaI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard- write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>


#IV. Conclusion


Despite the departure of Probesys, the project is progressing well on the frontend and ticket management.

All the work on the backend side since the last few months (API management, dynamic types, dynamic properties...) allows us to quickly progress on the code and the integration on the frontend side.

The dynamic is good ^_^

**David Durieux - FusionSuite project leader**