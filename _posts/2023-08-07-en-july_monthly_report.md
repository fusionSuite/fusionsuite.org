---
layout: post
title: July 2023 - Report of the month
categories: news
lang: en
---

Here is the report for the month of July 2023.

# I.Introduction

<br>

During this month of July, the focus was on workflows, validation of the data schema of FusionInventory agent 3.0, preparation of user tests.

Here is the menu of this report.

<br>

# II. Project events

<br>

# II.1. FusionInventory 3.0 Agent Validation

The increased development of workflows, in this month of July, made it possible to have the first FusionInventory inventories with the agent in version 3.0 integrated into FusionSuite. This works perfectly and with the information you want.

The inventory works well, but obviously not yet optimized. Additional attributes can be added in the inventory agent and taken into account in FusionSuite very easily.

These tests thus make it possible to validate the new protocol (REST API) and the new data structure (in JSON format) of the inventory of FusionInventory 3.0 \o/

I was waiting for these tests to validate the new format and thus continue the code on the 3.0 agent, so very good news!

<br>

# II.2. Community tests, registrations

It is now time to launch the first user test.

<img src="/assets/img/yeah.gif" width="500">


There are several important points to consider:

   * this is **a development version**, so not everything is implemented/finalized
   * **this is NOT a beta version** and a lot can still change
   * need feedback on the application to see the choices made and the modifications to be made to reach version 1.0
   * you must have a *github* account for issues
   * a discord account can be a plus, but not required. A *private* chat channel between testers and developers will be available
   * the test will last 3 days, i.e. **from August 31 to September 2 inclusive**
   * each tester will have a personal instance (individual test)
   * all testers will have access to a global/shared instance (group testing)
   * testers will have access to a development version of the FusionInventory agent in version 3.0, for Windows only
   * the languages used for tester feedback are only *English* and *French* (github & discord)
   * many data will be collected for analysis and improvement:
     * NGINX web logs
     * error logs (in NGINX database & error files)
     * backend telemetry
       * in *OTLM_NORMAL* mode on the first day
       * in *OTLM_DATABASE_QUERIES* mode the other 2 days (slightly slower response times)


If you agree with this information and would like to participate, please send me <a href="mailto:david@durieux.family?subject=First FusionSuite test registration&body=I would like to participate in this first test of FusionSuite and FusionInventory%0D%0A%0D%0AMy github account: %0D%0AMy discord account (optional): %0D%0AA few words about what you expect from FusionSuite: %0D%0A">an email filled in with the required information</a>.


I will confirm your registration or not within hours of receiving the email, the number of registrations being limited.

I will send you a summary by email on August 29 with the URLs of the 2 instances (one personal and one global) to use on August 31.

Thank you very much in advance for these tests, the feedback will allow us to adapt the roadmap for this end of the year before the 1.0 release.

<br>

# III. Development

<br>

## III.1. Back-end

<br>

### III.1.a Workflow

The workflow code has made good progress, unit and functional tests as well.

The code is done at 80% and the tests at 60%.

This should be finalized in August.

<br>

## III.2 Frontend

<br>

### III.2.a Type management

With the workflows, shortcuts have been added at the top in order to quickly go to the part requested in the type configuration (workflow, timeline...).

It's functional, not yet very pretty on the other hand (but it will come).

<br>

### III.2.b Workflow management

The development has progressed well.

Significant changes have been made to the code to make it simpler and more maintainable.

The code is done at 70%, the tests at 10%.

<br>

# IV. Conclusion

The workflows are the most important part of FusionSuite, the first uses show the extent of the possibilities, and it's really cool and exciting.

**David Durieux - FusionSuite project leader**