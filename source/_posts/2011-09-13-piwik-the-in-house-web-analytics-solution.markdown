---
layout: post
title: "Piwik - the in-house web analytics solution"
date: 2011-09-13 18:57
comments: true
categories: [Ruby Studio, web]
---

{% img right http://i.imgur.com/WJ3WNb.png?1 %}

All piblic websites need a way to track their visitors and while Google Analytics remains
the de-facto standart for web analytics, in certain cases customers prefer alternatives.
There might be several reasons to opt for an alternative, to name but a few:

- the customer might not trust Google or generally any external service with their web data
- the customer might want features that are missing from Google analytcis, such as real-time analytics
- the customer might want a more sophisticated API without quota limits to pull their data

Granted we still use and recommend Google analytics as the primary solution here at Ruby Studio,
we looked for possible alternatives in an effort to accomodate these user cases.

For live tracking the popular choice is [Woopra](http://www.woopra.com/), and we still use it on some of our
projects on customer request, however it has the downside of loading too much javascript too slowly and recent
tests we’ve made indicate that Woopra code takes about as much to load and process as all the rest
of our code and assets for a particular page put together. Some tweaks and hacks are possible for
performance improvement, but overall it remains too slow and hence not a primary choice for us.

Ideally we would have picked a Ruby based solution, so we considered [RailStat](http://www.railstat.com/),
but we decided it’s not yet mature enough for production, its feature set is still somewhat limited and
there seems to be no active development. We’ll be keeping an eye on it for the future.

So eventually our choice fell on [Piwik](http://piwik.org/). An open source project with rich feature set,
slick ajax-y interface, actively developed and maintained, with good market penetration (used on more than
150 000 sites). It also has a simplified, but fully working Live analytics module, allows extensive
customization and provides a rich API. Performance seems also quite good, the speed of getting and parsing
the tracking javascript seems on par with Google analytics, the impact on the webapp performance is minimal.

So we will be offering Piwik as an option for web analytics to our customers in 3 varieties:

- as part of our unified analytics service at [analytics.rubystudio.net](http://analytics.rubystudio.net).
This service will be used by multiple customers and web projects; user accounts for access and website
permissions will be set at per customer basis.
- as a separate Piwik instance, hosted by us, but not shared with other customers or web sites,
and the customer will receive full administration rights for the instance.
- as a customer-hosted solution. We can install and configure a Piwik instance for our customers
on their own servers or at their chosen hosting provider, and in this case the customer retains
all the privileges and responsibility of maintaining and hosting the software on their own
