---
title: How PhoneGap plays an important part in our Enterprise offering
date: 2011-06-27 19:37:13 Z
categories:
- app
author: admin
status: publish
type: post
format: html
---

Hi All,

At [Worklight](http://www.worklight.com/), we are not regular PhoneGap users: rather than developing PhoneGap-based apps, we have embedded PhoneGap into our enterprise-oriented mobile platform, and are fully exposing the PhoneGap APIs to our customers.  It is our customers (or their contractors) who then use those APIs when they build enterprise-grade mobile apps on top of the Worklight [mobile app platform](http://www.worklight.com/) and tools.

I wanted to share with you some of the nice advantages that PhoneGap provides in such an enterprise context.

In order to do that I'll start with some background about enterprise development and where our platform fits in.  Our aim at Worklight is to provide enterprises with a complete solution for building, running and managing the apps they release for smartphones and tablets.  We work very hard to help companies reduce the overhead that is associated with developing mobile apps in an enterprise context.   What overhead am I talking about? Well, when a company - say a bank, an airline, an insurance provider, or any other large organization - sets out to build a mobile app, they have much more to consider than just the functionality of the app. Here are just a few examples:

* Apps in an enterprise environment, whether intended for use by customers, partners or employees, usually connect to secure back-end systems, and need to handle sensitive data. This data must be protected during transit and also on the mobile device itself.
* It is often necessary to authenticate users before allowing them to access data. This requires integration between the app and the enterprise authentication infrastructure. Some apps require that authentication is made possible even when devices are in offline mode and don't have connectivity to the enterprise authentication systems, which complicates things further.
* Companies need to maintain control over their apps even after they have been distributed to users through app stores. Consider, for example, a situation where a critical security flaw has been corrected in an app - but only after 50,000 users have downloaded it. Many IT managers want to make sure in advance that they will be able to disable a flawed version if necessary, and force their users to upgrade (even if those users don’t usually go to the app store to get updates).
* Not to mention things like creating a controlled and collaborative development environment for mobile, dealing with various data representation formats in the back-end, managing performance issues, connecting back-end systems to mobile push services, and more.

What we provide with our platform is a supporting infrastructure that helps companies deal with all that overhead in an organized manner. This includes server components, device run-time and also development tools.

Of course, targeting multiple mobile operating systems and form factors in a cost-effective manner is a major consideration for our customers, so as part of our solution we had to provide a technology for cross-platform development.

We chose PhoneGap, and we are very happy with that decision.

From a technological perspective, PhoneGap's approach has tremendous benefits for enterprise development:

* Many companies appreciate the standards-based approach to multi-platform mobile development. And even though it may take a while, HTML5 is poised to become the technology of choice, balancing cross-platform reach with rich and engaging user experience.
* A lot of development organizations already have in-house HTML/JavaScript expertise, and being able to leverage that skill set is a great plus to them. If is almost always more cost-effective to develop in HTML than in the native language of the device.
* Compatibility with JavaScript toolkits like jQuery Mobile, Sencha Touch or Dojox Mobile is also a great advantage. An open development approach that incorporates these different technologies ‘under one roof’ is one that enterprise developers find extremely valuable.
* The PhoneGap APIs for accessing device features simplify development of powerful apps that access many mobile device capabilities. Users appreciate apps that make beneficial use of things like the address book, camera, accelerometer and so forth – whether the app comes from a solo developer or from a large enterprise. In fact, many enterprises are looking for creative ways to deliver apps that make sense in the mobile context, and being able to access device capabilities is a crucial factor.
* PhoneGap's extensible architecture allows enterprises to tap the full potential of the mobile device – even beyond the services exposed by the standard PhoneGap APIs. For example, Lotte, a major Korean credit card company used our platform (and, of course, PhoneGap), to [develop a cross-platform app](http://www.worklight.com/resources/case-studies) for Android and iPhone that includes an augmented reality feature. The app has over 100 HTML screens that are shared between Android and iPhone, and platform-specific native implementations of the augmented-reality screen. Users can’t really tell that they are switching between HTML and native pages when they use the app.

Beyond the technology, we found PhoneGap to be a vibrant project, supported by a great community that continues to push the technology forward with enhancements, tutorials and examples.

So to sum it up - we wanted to say thanks to all of you in the PhoneGap community for a great framework that provides significant benefits in the Enterprise context, as our experience at Worklight has shown.

-Ron Perry (CTO at Worklight)
