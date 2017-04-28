---
title: Questions and Myths About PhoneGap
date: 2012-06-21 19:22:28 Z
categories:
- app
tags:
- App
- Guest Post
author: Andrew Trice
status: publish
type: post
format: html
---

When technology teams are making decisions of whether or not to adopt a mobile strategy revolving around PhoneGap, lots of questions arise. This is natural - investing in any technology is a big decision, and the proper course is to evaluate its strengths and weaknesses. Phonegap is a relatively new concept to many IT organizations, so there are many unanswered questions and misunderstandings about PhoneGap and [Apache Cordova](http://incubator.apache.org/cordova/).  In this post, I'll try to answer a few of these questions, clear up a few misunderstandings, and dispel some of the myths. Before I get started, I want to highlight two previous entries on the PhoneGap blog:

* [PhoneGap Explained Visually](https://phonegap.com/2012/05/02/phonegap-explained-visually/) provides a clear definition of what makes up a PhoneGap application. Read this for a better understanding of what PhoneGap is, and how you use it.
* [PhoneGap Beliefs, Goals and Philosophy](https://phonegap.com/2012/05/09/phonegap-beliefs-goals-and-philosophy/) provides insight into the motivation, goals, philosophy, and "why" PhoneGap was created. Read this for a better understanding of why the PhoneGap/Cordova teams do what they do.

Now, on to the questions...

**Question: What is the difference between PhoneGap and Apache Cordova?** PhoneGap is a distribution of Apache Cordova.  Apache Cordova is the technology that powers a PhoneGap application, however a distribution of an open source technology may eventually contain tools that enhance the developer workflow with Cordova, or tie into other tools and services.  PhoneGap is still free and open source, and is powered by Cordova.   You can read more about [the relationship of PhoneGap and Apache Cordova in this post by Brain Leroux](https://phonegap.com/2012/03/19/phonegap-cordova-and-what%E2%80%99s-in-a-name/), lead of the PhoneGap project within Adobe.

**Question: Why is the [RoadmapProjects](http://wiki.apache.org/cordova/RoadmapProjects)** [PhoneGap Roadmap](http://wiki.apache.org/cordova/RoadmapProjects) so short? I'm often asked this question, encountered by enterprise decision makers who wonder why there isn't a three to five year product roadmap outlining the directions of the project. Instead of using a longer term roadmap, PhoneGap/Cordova uses a short term roadmap that advances product development based upon market forces and feedback from current users.  This is roughly about six months out, with an emphasis on delivering features that will provide immediate benefit for developers. Due to the rapid changes in the mobile landscape this may include support for new platforms or consolidation based upon mobile OS changes. In retrospect:

* 5 years ago, the iPhone did not exist
* 3 years ago, the iPad had not been introduced to world, and there were no commercially successful tablets on any platform
* 3 years ago, the dominant operating systems were RIM with 42% market share, Apple with 24% market share, Microsoft with 19% (Windows Mobile, not Win Phone 7), Palm with 8.3%, and Google (Android) with 2.5%,   As of January 2012, Google has 48.6% market share, Apple has 29.5%, RIM has dropped to 15.2%, Microsoft has dropped to 4.4%, and Palm is no longer in existence.   Sources:
  * [December_2009_U.S._Mobile_Subscriber_Market_Share](http://www.comscore.com/Press_Events/Press_Releases/2010/2/comScore_Reports_December_2009_U.S._Mobile_Subscriber_Market_Share)
  * [April_2012_U.S._Mobile_Subscriber_Market_Share](http://www.comscore.com/Press_Events/Press_Releases/2012/6/comScore_Reports_April_2012_U.S._Mobile_Subscriber_Market_Share)
* 5 years ago, 11% of all adults had smartphone devices, compared to 49.7% today.  Sources:
  * [2012 SmartPhone Penetration](http://blog.nielsen.com/nielsenwire/online_mobile/smartphones-account-for-half-of-all-mobile-phones-dominate-new-phone-purchases-in-the-us)
  * [2009 SmartPhone Penetration](http://blogs.forrester.com/consumer_product_strategy/2010/01/2009-year-of-the-smartphone-kinda.html)

Based upon the rapid rate of change of the mobile landscape, a three to five year roadmap is not practical. In addition, mobile OS development companies such as Apple, Google, Microsoft and RIM do not provide multi-year roadmaps that could be used as reference in a long term PhoneGap/Cordova roadmap. The open source Cordova project roadmap, available at [http://wiki.apache.org/cordova/RoadmapProjects](http://wiki.apache.org/cordova/RoadmapProjects) highlights all ongoing efforts.  Major efforts include command line tools for PhoneGap, Cordova JS, and the PhoneGap Plugin Project.  There are no dates associated with these yet, however they are ongoing, and contribute to a more standardized and canonical API, and are listed in the project roadmap.

**Question: How much does a PhoneGap app cost to develop and maintain compared to a native app?** There is no cost associated with using PhoneGap or Apache Cordova.  The PhoneGap SDK is free for anyone to use or extend. Any comparison of long-term development cost of HTML, hybrid, or native development is very subjective based upon the application that is being built.  Adobe does not provide metrics for these approaches, as they can be vastly different based upon the nature of the application, developer skills, and number of supported platforms. For a broader view, I suggest looking to independent research firms such as Forrester or Gartner for this answer.  A recent report by Forrester indicates that HTML/Hybrid applications do, in fact, cost less over time.  This report suggests to start with web and hybrid approaches.

* "Forrester says that enterprise development shops that plan on writing distinct native apps for each platform should plan on a budget 150% to 210% higher than what might be reasonably expected."
  * Source: [ReadWriteWeb.com](http://www.readwriteweb.com/mobile/2012/01/hybrid-html5-apps-are-more-les.php)
  * Based upon this [Forrester Report](http://www.forrester.com/Building+Mobile+Apps+Start+With+Web+Move+To+Hybrid/fulltext/-/E-RES61154?objectid=RES61154)

It should also be noted that many, if not all assets used within a PhoneGap application can be easily repurposed for a standard web-based applications, targeting either desktop or mobile browsers.   Properly authored PhoneGap applications are portable back to desktop or mobile browsers with little to no modification.

**Question: Who are the PhoneGap/Cordova contributors and who leads the open source project?** The core PhoneGap/Cordova contributors are listed online at [http://incubator.apache.org/projects/callback.html](http://incubator.apache.org/projects/callback.html) This list is comprised of members from [Adobe](http://www.adobe.com/), [IBM](http://www.ibm.com/), [Microsoft](http://www.microsoft.com/), [RIM](http://www.rim.com/) and [ICS](http://www.ics.com/). - I apologize in advance if I've missed anyone.  The PhoneGap team will also be voting soon to add members from [Intel](http://www.intel.com/) to the Apache core team.  The majority of the core contributors are from Adobe, and the direction of the project is largely lead by Adobe; however, the core team votes/forms a consensus upon new features and project direction, and all of those features are rooted in requests from users or market changes.  The PhoneGap lead within Adobe is [Brian LeRoux](https://twitter.com/brianleroux).  However, input is not only limited to Adobe - we strongly encourage you to [get involved, become a committer,](http://incubator.apache.org/cordova/) and help push Cordova forward. If you count every JIRA issue logged, every wiki update, every open source PhoneGap plugin, and every message on the Apache mailing list, the number of contributors is in the hundreds - if not thousands. There is no easy or accurate way to measure the makeup of this base, as it has evolved over several open source repositories.

**Question: What is the industry reputation of PhoneGap?** PhoneGap has recently received several awards worth noting.  Here are two of the most recent:

## PhoneGap Named 2012 Technology of the Year By InfoWorld:

* [Adobe Blog Announcement](http://blogs.adobe.com/conversations/2012/01/adobe-phonegap-named-2012-technology-of-the-year-by-infoworld-test-center.html)
* [InfoWorld Article](http://www.infoworld.com/slideshow/24605/infoworlds-2012-technology-of-the-year-award-winners-183313#slide2)

## PhoneGap Named Best Cross-Platform Development Tool By Code Project:

* [Adobe/Phonegap Blog Annoucement](https://phonegap.com/2012/06/12/adobe-phonegap-named-best-cross-platform-development-tool-by-codeproject/)
* [CodeProject Press Release](http://www.codeproject.com/PressReleases/5777/CODEPROJECT-ANNOUNCES-FOURTH-ANNUAL-MEMBERS-CHOICE.aspx)

PhoneGap is also the leader for developer mindshare of cross platform technologies according to independent research firm Vision Mobile: [http://www.visionmobile.com/product/cross-platform-developer-tools-2012/](http://www.visionmobile.com/product/cross-platform-developer-tools-2012/)

![](/uploads/2012/06/mindshare-index.png)

![](/uploads/2012/06/intentshare-index.png)

Also worth noting in these charts is that AppMobi is built on top of PhoneGap/Cordova, but is visualized separately.

**Question: Are there any PhoneGap usage metrics available?** I spoke with the engineering teams to get some insight into PhoneGap adoption rates.  There are no publicly reference-able statistics yet; however, much of this will be available once PhoneGap is promoted to a top-level project within Apache. As of September 2011 (9 months ago), 4% of all apps in the iTunes Store were built with PhoneGap.  We believe this number has grown, but don't have the reports to prove it yet. Currently, there is an average around 100,000 downloads of the PhoneGap SDK per month. This is indicative of a significant developer base.

**Myth: Adobe has not invested in PhoneGap because it was contributed to the Apache Software Foundation** Adobe is committed to the development and success of PhoneGap/Cordova.  It is important to understand that PhoneGap has always been open source, and contribution of PhoneGap to the Apache Software Foundation was to provide a larger support base for the project.  Adobe is involved with many open source initiatives in the area of HTML and web standards development, which you can learn more about at: [http://html.adobe.com/opensource/](http://html.adobe.com/opensource/).

Contribution of PhoneGap to the Apache Software Foundation is not indicative of any lack of investment. The PhoneGap team is also involved with the W3C Web Applications Working Group ([http://www.w3.org/2008/webapps](http://www.w3.org/2008/webapps/)) and the W3C Device APIs Working group ([http://www.w3.org/2009/dap](http://www.w3.org/2009/dap/)) to help drive APIs that will be used in future standards specifications. Adobe does not disclose financial investment into projects or future product roadmaps, however you can see evidence in Adobe's investment in PhoneGap in the following:

* Acquisition of Nitobi (the creators of PhoneGap) in November 2011
* Integration of PhoneGap into Adobe Creative Suite Projects:
  * [https://phonegap.com/2012/04/24/adobe-dreamweaver-cs6-supports-phonegap-build/](https://phonegap.com/2012/04/24/adobe-dreamweaver-cs6-supports-phonegap-build/)
* Creation of the PhoneGap Build Service:
  * [https://build.phonegap.com/](https://build.phonegap.com/)
* PhoneGap and HTML-centric products and tools:
  * [http://html.adobe.com/toolsandservices/](http://html.adobe.com/toolsandservices/)

It is also important to understand that Adobe is not the only company invested in the success of PhoneGap/Cordova.  Below is a brief list of other large-scale enterprises that have invested in PhoneGap/Cordova:

* **[Facebook](http://facebook.com)** uses Apache Cordova in their mobile SDK.  You can learn more about this at: [https://developers.facebook.com/docs/guides/mobile/](https://developers.facebook.com/docs/guides/mobile/)
* _* **[](http://SalesForce.com/)**[SalesForce.com](http://SalesForce.com/)_[*](http://SalesForce.com/) uses Apache Cordova in their mobile development SDK.  You can read more about the [Salesforce.com](http://Salesforce.com/) SDK at: [http://wiki.developerforce.com/page/Mobile_SDK](http://wiki.developerforce.com/page/Mobile_SDK). You can view how [Salesforce.com](http://Salesforce.com/) is using PhoneGap/Cordova in their Github repository at: [https://github.com/forcedotcom](https://github.com/forcedotcom)
* **[IBM](http://www.ibm.com)** not only has several core committers to the Cordova project, IBM's Worklight platform is built on top of PhoneGap/Cordova: [http://www.worklight.com/](http://www.worklight.com/)
* **[Microsoft](http://www.microsoft.com)** has several core committers to Cordova project, and is involved with the development of PhoneGap/Cordova for windows devices.
* **[RIM](http://www.rim.com)** has several core Cordova committers, and is involved with creating tools for PhoneGap/Cordova development, such as the Ripple device emulator: [http://ripple.tinyhippos.com/](http://ripple.tinyhippos.com/)
* **[SAP](http://www.sap.com)** has partnered with Adobe to leverage PhoneGap for the mobile development solutions: [http://www.news-sap.com/sap-drives-openness-and-choice-for-millions-of-mobile-app-developers/](http://www.news-sap.com/sap-drives-openness-and-choice-for-millions-of-mobile-app-developers/)

In addition to the large-scale companies listed above, smaller firms are also building businesses and product lines around the Cordova toolset, including:

* **[AppMobi](http://www.appmobi.com)** - AppMobi produces a mobile development suite based upon Apache Cordova.
* **[Icenium](http://www.icenium.com)** - Icenium also produces a mobile development suite based upon Apache Cordova.

If you have any other questions or concerns, please let us know.  We would love to answer them for you.
