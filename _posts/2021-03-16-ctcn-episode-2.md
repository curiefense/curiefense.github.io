---
layout: post
title: "How Appfleet Fits into the Cloud Native Ecosystem"
description: "The Cloud Native Ecosystem continues to develop and expand its reach as more and more entrepreneurs see pain points in the developer landscape and seek to fill those gaps."
published: true
excerpt: ""
createdOn: "Tue Mar 16 2021 13:42:55 GMT+0000 (Coordinated Universal Time)"
author: "Justin Dorfman"
mainImage: ""
thumbnail: "/images/blog-how-appfleet-fits-into-the-cloud-native-ecosystem.png"
---

<iframe src="https://player.fireside.fm/v2/sO31L4lC+8O-k1eqE?theme=dark" width="740" height="200" frameborder="0" scrolling="no"></iframe><br>

The Cloud Native Ecosystem continues to develop and expand its reach as more and more entrepreneurs see pain points in the developer landscape and seek to fill those gaps.  And that’s exactly what [Dmitriy Akulov](https://twitter.com/jimaek) did when he came up against a couple roadblocks time and time again.  To scratch his own itch, he founded [Appfleet](https://appfleet.com/) which has very quickly gained some real traction and is showing itself to be a very valuable tool for developers worldwide.

We had a chance to interview him for [episode 2](https://podcast.curiefense.io/2) of the Committing to Cloud Native podcast and were able to nerd out a bit about what he’s building and why it matters.

--

**What is Appfleet?**

In essence, Appfleet is a service that allows you to deploy docker applications much closer to your users than is normally practical, and on a global basis.  The tool allows websites, services, APIs and the like to be deployed to the edge which brings with a range of reliability and performance improvements.  Akulov described it as a CDN, but for actual goals where you can your whole service natively in every location across the globe.

It’s super simple to use.  A developer will compile their application in a docker container and then submit it to Appfleet using their API.  They will then use the front-end interface to toggle exactly where they want the application deployed.  It could be in one specific locations, it could be in a couple of hotspots, or alternatively it could be deployed everywhere at once.  Appfleet takes care of all the nitty-gritty behind the scenes, making it a completely seamless experience for the user.  It’s a complete platform with all the bells and whistles you could want.

**The Journey So Far**

As mentioned, Akulov built this to solve a problem he was facing, but quickly discovered that it had commercial value that warranted starting a company around it.  He was heavily inspired by Heroku and set out to build a tool that was easy to use for developers but was still beautifully designed in the way that we normally think about consumer apps.  The additional insight that created product-market fit was a realization that he needed to build something that would work with the legacy systems that are already out there.  Instead of having to re-build everything, a developer could dockerize their solution and plug it into Appfleet straight away, removing any unnecessary friction from the process.

The company has just recently emerged from a long beta period where about 200 users of different sizes, from around the world tested the tool and provided useful feedback.  Most notably, they had some beta users from Google who pushed the company to think more seriously about machine learning and AI applications on the edge, something that Appfleet has now started to implement.

Since coming out of beta, the company has around 100 people with production use cases at present, and the number is growing incredibly fast.  It really is set to become a significant player in the cloud native space.

**What’s Next for Appfleet?**

It’s clear that Akulov wants to keep expanding, and the signs of growth are there for all to see.  His vision to build a big cloud edge platform that can support a wide range of use cases, getting applications as close to the end users as possible.  They have the capability to support all protocols and eventually want to get to a point where they can deploy databases, DNS servers and all sorts of other things on the edge because they are not limited by HTTP.

There are plans to build some open-source tools within the Appfleet ecosystem to nurture a community around these ideas, so that’s another exciting development to keep an eye out for.

The market here seems to be almost infinite and it’s very possible that the major cloud providers will come knocking on Akulov’s door in the near future if they continue to enable the range of use cases that they’re aiming at.

**Dmitriy’s Spotlight**

Every podcast we take a moment to appreciate some amazing work coming out of the community and Akulov hit a home run by mentioning [Envoy](https://www.envoyproxy.io/) which is a great tool that they use on Appfleet to do zero-downtime deployments on single instances.

--

All in all, we had a great conversation and there was so much more than what we could squeeze into this post.  So be sure to [listen to the whole podcast here](https://podcast.curiefense.io/2) for the full experience.  It’s jam-packed with value and should give you a great introduction to Appfleet and the amazing things they’re building there.

And if you’re going to give Appfleet a try, be sure to use our podcast code [CTCN20](https://appfleet.com/) to get a recurring 20% discount for your first 12 months.

