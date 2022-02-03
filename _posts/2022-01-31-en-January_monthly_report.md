---
layout: post
title: January 2022 - Monthly report
categories: news
lang: en
---

Like for the FusionInventory project, I write each end of the month or begin next month a report about the project. The goal is to inform you what's append in the month (code, community, documentation...) and give too the directions for next days/weeks/months.

So let's go ;)

# I. Announce and presentation of the project

After weeks of works to prepare the presentation of the project, read and fix part of the presentation by our 2 partners, I have presented the project in live on Twitch platform on January 12, 2022.

About 230 people have following this live presentation. It seems to have had a very nice effect ;)

Many users/companies has contacted me (directly or on the Discord server) to offer help on the project.

Snax44 and Laurent Lienhard has joined the project. They write documentation of the project, and Laurent has created docker dev versions in the goal to quickly test the product (1 docker for the backend and 1 docker for the frontend, see below).


# II. Development

## II.1. Backend

### II.1.a. REST API

This month, so after the end of the POC, the first task has been to stabilize and add tests the REST API. The works is not finished but big part has been made. It's possible that REST API endpoints can change again (like we had `/cmdb/type` and now have `/config/type`).

I add libraries into the REST API functions to validate the data received: name of keys (for example check if it has the keys right `name`, `type_id`), type of values (like string, integer, boolean...). This new system is more powerful than code I used in the POC. In case of the validation not pass, an exception is throwing and return explicit return message with the associate HTTP code error.


### II.1.b. Rules

Like you can saw on the presentation, the rules are very important.

I have begun to design and write the rules played when *add* and *update* item.

We will have 2 kind of rules:

* update a field
* run a script

This is the description of the *run a script*.

When an item is added or updated, a script can be called and running. Couple examples of scripts:

* send an email notification
* send a Slack notification
* create a host in Zabbix (monitoring solution)

Like you can see, these rules will be used to communicate outside of FusionSuite.

The first script (Zabbix add host) is written (it's PHP code) and works nicely.

The documentation for the developers is written (it's a draft for the moment).

I will write an article on the website in couples days with all information. I will be happy if users write scripts for perhaps other usages and integrate these scripts into the future first release.

It will give me too the usages needed and perhaps can forces me to modify some parts of these rules (probably i didn't think of everything and all possible usages you can have).

## II.2. Frontend

The frontend has not been yet updated since the POC. I prefer stabilizing the backend first and not modify the frontend code too often, because it will takes too many times.

But yes there is a *but*, the works about the design start at the beginning February by Sarah, ergonomist of our partner [Probesys](https://www.probesys.com/). Thanks to them!


## II.3. Docker images

Laurent Lienhard has created the FusionSuite docker for the backend and the frontend. **It's the dev version, so it's not working nicely for the moment**. You can find them on his [repository](https://github.com/LaurentLienhard/FusionSuite-Docker).



# III. Tests campaign

In the year and before the release, couple tests campaign will be planned to focus and test specific parts (some features to hard test by the users) of FusionSuite.

The first campaign can be planned for May - June (not yet exactly defined). It will be announced when the dates (planned for 2 or 3 days) will be confirmed.

# IV. Communication

Couple news about the communication ;)

## IV.1. Discord server

The discord server, shared with FusionInventory team is always opened, and couple features are discussed on it. If you want speak with us, come on...


## IV.2. Youtube

The video of the presentation, recorded on the Twitch on January 12 will be soon published on our Youtube channel. I currently write subtitle in French, hope the automatic translation in other languages will be ok. If you want to translate yourself, please contact us, it will be a pleasure to give access to subtitles and integrate the translation.

## IV.3. Website

The website has been released on January 12.

Last week, I added a news section where inform you about the project, like this January monthly report.

The documentation has started to be written few hours after announcing of the project by snax44, and will be soon available on the website.

The REST API documentation (technical documentation for the developpers) is published as draft for the moment. The url is available [here](https://fusionsuite.org/documentation/restapi/). It's a draft and need time to be more consistently.



# V. Conclusion

The project is gaining momentum is it fills me with joy.



**David Durieux - Leader of FusionSuite project**
