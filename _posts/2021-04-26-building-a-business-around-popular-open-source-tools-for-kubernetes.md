---
title: Building a Business Around Popular Open-Source Tools for Kubernetes
layout: post
canonical_url: ''
description: We chatted to Richard Li – someone who has accomplished building open-source tools that bring tons of value to the community and running a successful commercial business with Ambassador Labs.
published: true
createdOn: "Tue Apr 26 2021 00:00:55 GMT+0000 (Coordinated Universal Time)"
author: "Justin Dorfman"
mainImage: ""
thumbnail: "/images/ctcn-podcast-ambassador-labs-episode-7-richard-li.png"
permalink: /blog/:title/
---

<iframe src="https://player.fireside.fm/v2/sO31L4lC+ULiRC2yu?theme=dark" width="740" height="200" frameborder="0" scrolling="no"></iframe><br>
Subscribe: [Apple](https://podcasts.apple.com/us/podcast/committing-to-cloud-native/id1560888468) · [Spotify](https://open.spotify.com/show/5IvVV4G1yxTt2LnuvNNrd3?si=lvypkYk-QhmDx6GtwHh15A) · [Google](https://podcasts.google.com/feed/aHR0cHM6Ly9wb2RjYXN0LmN1cmllZmVuc2UuaW8vcnNz?sa=X&ved=0CAMQ4aUDahcKEwjYjLmU7trvAhUAAAAAHQAAAAAQAQ&hl=en) · [RSS](https://podcast.curiefense.io/rss)

When you’re trying to tread that fine line between building open-source tools that bring tons of value to the community and running a successful commercial business, you have to get many things right.  And in [episode 7](https://podcast.curiefense.io/7) of the Committing to Cloud Native podcast, we chatted to [Richard Li](https://twitter.com/rdli), who has accomplished this very successfully with Ambassador Labs.  We learned a lot from this conversation, and we think you will too.

<hr style="height: 1px; background-color: #ccc; border: none;">

## Richard’s Story

Richard picked up a prestigious education through MIT and Harvard but was an entrepreneur at heart right from the beginning.  Even through his early days at Red Hat, Rapid 7, and Duo – he applied his skills in creating things from scratch.  Eventually, he decided that he wanted to start his own thing, so he started asking around to figure out what problems people had out there.

As many of these journeys go, things shifted a number of times early on until he found the right thing.  He iterated in the metrics and monitoring space, in the service mesh space, and eventually homed in on the fast-growing Kubernetes industry that was gathering steam.  He realized that this is where he could get some real traction with his unique blend of skills and experience.

This was not an overnight idea by any stretch of the imagination.  Instead, it came through 18 - 24 months of evolution to get to the idea that would finally stick.

## Enter Ambassador Labs.

Richard’s company [Ambassador Labs](https://blog.getambassador.io/?gi=dcb89024f76c) builds open-source tools for Kubernetes and then also offers premium enterprise features as proprietary side cars for numerous clients across the space.  This didn’t happen overnight though.  The company began as Datawire and during this initial stage they built Telepresence (which brings the power of local development into your Kubernetes workflow) and the Ambassador API Gateway which was the first thing that put them on the map.  

When they decided to donate the API Gateway to the CNCF they had to change the name so they could pass on the trademark to the gateway without having to change the company name again.  So that tool became known as Emissary – Ingress and the company solidified itself as Ambassador Labs.

Today, that tool is around 4 years old, and it boasts an amazing roster of companies who use it in production.  There are numerous examples of heavy deployments running at scale.  The most interesting perhaps being the largest video streaming company in India who live-stream cricket matches.  When a match starts, activity soars from 1m requests per minute to 6m requests per minute almost instantaneously.  And the tool makes sure that everything works.  

There are around 150 part-time contributors to the project, and they are continually looking for people to join to help maintain the project in addition to contributing to the feature set.  It’s difficult to say exactly how many companies are using the tool, but Li suggests that a fair estimate would be in the tens of thousands.

In other words, it’s a powerhouse.

## Tips for Building Open-Source Projects

The two most important things for a start-up working on an open-source project, according to Li, are making it easy to install and having good documentation.  In the early days you simply don’t have the brand or scale of a larger company which allows you to ship more complicated software.  So instead, you need to make sure that developers can see good documentation and then can try it and get using it quickly.

If you get that right, and your product is actually good, then you’re off to the races.

## Building a Business on Top of Open Source

When you’re running a company and you’re working on open-source projects you essentially have to come up with two different kinds of products.  You’ve got to figure out an open-source project that provides lots of value as well as another product that people will love even more and are willing to pay money for.  It’s a balancing act because if you try to take too many features away from open source, the community gets upset, but if you don’t take enough – the commercial venture fails.

Li’s approach was to build a number of high-end enterprise features and expose those APIs in the open-source version so that if people wanted to build with them, they could.  However, if a developer didn’t want to spend the effort on that, they could pay for the proprietary sidecar and use that energy elsewhere.  This approach avoided having to fork while still creating a viable business model.

In fact, the company turned this dilemma into an advantage because the open-source community became their distribution platform.  Instead of having to use an army of salespeople to cold call developers, they could access qualified leads thanks to their open-source tools, and that helped to sustain the business.

## The Future of Ambassador Labs

To some it may seem that the rapid increase in usage of managed Kubernetes services might threaten a business like this, but Li explained that it was in fact the opposite.  By making it easier to adopt Kubernetes, it makes it easier for people to adopt their software.  A rising tide really does lift all boats here.

As a company, they are very focused on improving the app developer experience on Kubernetes with a vision that people developing on Kubernetes in the future while be using their suite of tools for their daily development.  When people understand how to adopt and use these tools, they can really improve their productivity and ship software faster.  And that’s what the company is betting on.

The nature of software development itself is changing in front of our eyes with Kubernetes being in the cloud.  In traditional software development you, as a developer, were responsible for writing code and then you had a different team who was responsible for running that code, then another team responsible for deploying that code.  Today, you’re actually responsible for the full software lifecycle for that microservice.  A full stack developer now is a full life cycle developer.  We are moving away from specialist roles and toward developers managing every part of the process.

We covered so much more in this conversation including the early days of what was then Datawire, Li’s thoughts on Argo, and plenty of other great topics.  So, if this has piqued your interest, be sure to [check out the full episode](https://podcast.curiefense.io/7).  You won’t regret it!


<hr style="height: 1px; background-color: #ccc; border: none;">

<a name="transcript">
## Transcript

**Intro:** You can argue that Kubernetes accelerated productivity in some dimensions, right? Like the Last Mile Soft Delivery, clearly Cloud beats CD ROMs any day of the week. The flip side is developing for the Cloud is way more complicated and way more responsibility and way more to understand than just building Julie windows app, using Microsoft foundation classes. Hello and welcome to Committing To Cloud Native. The podcast were we talk about the confluence of open source and the Cloud, what it means to do open source at Cloud Natives Scale. Today we have two panelists on, we have Justin Dorfman and we're joined by Tzury Bar Yochay, who is the CTO and co-founder of Reblaze. Our guest today is Richard Li, Richard is calling in from Boston, he's the co-founder and CEO of Ambassador Labs, which works on open source tools for Kubernetes. Super excited about this conversation, take it away, Justin.

**Justin Dorfman:** Hey Richard, how are you?

**Richard Li:** Great to be here, Justin.

**Justin Dorfman:** Awesome. Tzury is joining us, how are you doing?

**Tzury Bar Yochay:** I'm great, very happy to have reach on your podcast.

**Justin Dorfman:** I agree, you got him here so I really appreciate that. So for those who don't know Richard is the co-founder and CEO of Ambassador Labs, which builds popular open source tools for Kubernetes. There's one thing that is driving me crazy, we got Data Wire, we got Ambassador API Gateway, we have Emissary Ingress. Can you explain all these branches and everything to me so I am up-to-date.

**Richard Li:** Sure, yeah, it's confusing, it's life as a startup, right? So we started and funny story I'll tell you is we started our company as Data Wire and the only reason why it was called Data Wire was because my co-founder and I, we were sitting around and we said, well we're starting a company the company needs a name and we need a website. So we ended up basically just using instant domain search and just typing in random things and we ended up with Data Wire and it was a black Friday sales five bucks. So that was the name of the company and then we built these different projects; one was Telepresence, and then we built this thing called Ambassador API Gateway the reason we called it Ambassador API Gateway was because it was built on an Envoy proxy. An Envoy through the US Department Of State Hierarchy, actually reports to an ambassador. So ambassadors serve at a higher level envoy and so that's what we created. Most people started to associate us really with the Ambassador API Gateway, so we rebranded the company to Ambassador Labs. So today we're officially Ambassador Labs, our products are Ambassador API Gateway and Telepresence, but it gets more complicated because we wanted to donate Ambassador API Gateway to the CNCF. And the CNCF says, well in order to donate the technology, we need to take your trademark which is Ambassador and we said, well but that's the name of our company and they said, well the only thing you can do is to rename it and so we said, okay. So we picked a different type of ambassador called an Emissary so there's Envoy, there's Emissary, there's Ambassador all part of the team. And so now today we're Ambassador labs, we make the Emissary Ingress, we make Telepresence and that's what it is, so that's where we're consolidating. We don't really use the word Data Wire anymore and it's really Emissary, Telepresence and Ambassador Lab.

**Justin Dorfman:** I can totally relate to you on that because when I was at a company called Max CDN, our parent company was Net DNA. So everyone was just like, well is Max CDN part of Net DNA or is Net DNA in, it was such a hassle. But over time they'll eventually get that differentiation. Now, Tzury you know all about CNCF licensing and all that, maybe you want to give a little insight to your experience.

**Tzury Bar Yochay:** Well, luckily with Curiefense we did something different, so we have regulated the company and the project so we didn't have to run into this challenge. But indeed most of the people coming to open source with native approach and just wanted to use something and all of a sudden it becomes legal and paperwork and trademarks, transformations and so on. You need to take care of it beforehand and think well with naming, I would say.

**Justin Dorfman:** Yeah, that was the first time where Tzury actually sent me a dude email, or I think it was a slap message because like I signed the papers for the trademark stuff without clearing it with him. So it was funny because I was just trying to get this thing through the door because you know, time was of the essence. But what I like about working at Reblaze is that you can ask for forgiveness rather than permission. So anyways, so getting back to the new project that you donated, I read down the new stack, like a couple of days ago that you did the donation. Now, what are your expectations to getting to graduation? Like, do you see this as a long-term thing or are you looking to accelerate, getting it to the next level? Because right now it's a sandbox, right?

**Richard Li:** It's an incubation project.

**Justin Dorfman:** Oh, it's incubated.

**Richard Li:** It's in incubation, yeah. Ambassador API Gateway, or Emissary Ingress, it's been around for three or four years and there's an amazing roster of companies that use it in production. So we were just talking with the largest video streaming company in India and they livestream cricket matches and all their traffic goes through our API gateway and Envoy proxy and they were telling us how in five minutes, when the cricket match starts, they go from a million requests per minute 6 million requests per minute and it's just a horizontal pod auto scaler in Kubernetes and it just works. So we have a lot of real world heavy deployments running at scale and really for us, the biggest thing we're trying to do is really grow that community of contributors. We have about 150 part-time contributors to the project and we're really looking to create and encourage other people to step up, to be maintainers of the project as well, in addition to just contributing on a feature basis. So like Puppet Labs has a great team of engineers there, they contributed all this stuff around key native scaling. We'd love for other people, not just to contribute features but really help us maintain, grow, evolve that project.

**Justin Dorfman:** Wow, 150 contributors is pretty impressive, how long did it take you to get to 150?

**Richard Li:** So we started the project in 2017, we released the first version in June of 2017 and it started taking up pretty quickly just because people were starting to recognize the power of Envoy Proxy and people also were starting to try to deploy on Kubernetes and if you've ever tried to use Envoy proxy on its own and then much less deployed on Kubernetes, you would realize, oh, this is actually quite complicated and so we built the software to make it easy to run Envoy on Kubernetes. So I would say probably two or three years for us to get to the 150, but we started having contributors probably within six months of our initial release, contributing significant functionality.

**Justin Dorfman:** Got it, now do you work closely with the Envoy team, how does that work?

**Richard Li:** We have one of our engineers actually maintains parts of Envoy, specifically the external authorization filter, which we depend pretty heavily on. I think he also does few other components, so he's sort of our lead person and working with Envoy and then we also are part of the Envoy distributors group because we repackage Envoy. So when their security errata, we get notified about it and so last night it was a little bit of a late night because it was a kind of an exciting process to get the security patches in Envoy out and then once Envoy gets the security patches out, we then have to do all these builds to get a new release of the API Gateway out. So we talked to the Envoy community quite a bit and I would say we're really just part of the Envoy community.

**Tzury Bar Yochay:** Richard, you wrote these product, API Gateway that now goes by the name of Emissary Ingress, right? I believe it's 400, 500 organizations are using it right now.

**Richard Li:** It's a little hard to tell but we have 5,000 people in our slack and they're generally from different organizations. So we think, our best guests are probably in the tens of thousands because not everyone who installs us creates a slack account. Is it 10,000, is it 20,000, 50,000 hard to say.

**Tzury Bar Yochay:** So this a success story by all measures, I would say and given the open source aspect to the story, I would love if you can elaborate a little bit about to our listeners, to us, curious fans as well. What are the rules, the ground rules, the golden rules that you would say to build a successful open source project? What are the one or two things we must do from the very beginning that keep a project interesting to the community and to get it out and simply reach out to those achievements, I would say?

**Richard Li:** Especially if you're a startup, I think the two areas I would focus on is make it easy to install and use and then two sort of correlated to that is have good documentation. And the reason why I say if you're startup, because if you're starting you don't have a lot of marketing brand and those kinds of things and so developers just want to see that there's good documentation and they are able to try it and use it quickly. And that was a big thing, I actually wrote a lot of the original documentation for Ambassador and I put a lot of effort into it that was a big part of my job in the early days. And the exception is if you're a really big company like Google, you could ship something like STO, which is actually quite impossible to use. But you could still get a lot of people to use it, so I would say if you're a big company, you can get away with shipping very complex software.

**Justin Dorfman:** That was great.

**Richard Li:** Sorry, I had to get that in.

**Justin Dorfman:** No, we're going through an STO thing right now so it was just kind of like perfect timing.

**Richard Li:** Whenever someone says, I love STO, the first question I asked them is, have you ever tried to upgrade STO in production?

**Justin Dorfman:** That's exactly what's happening, we just had a call with a customer who's using Carry Feds and this is the exact same thing, it gets kind of crazy.

**Richard Li:** Everyone loves STO until they try to upgrade it in production, at which point they realize it's actually terrifying.

**Tzury Bar Yochay:** Yeah, it's definitely not a simple platform. So Richard, may you elaborate a little bit about having a business on top of an open source and such success open source. Where do you draw the line between the paid and the free and all those, the ecosystem around it and all sort of?

**Richard Li:** My opinion is my next company is I'm not going to do an open source company because you really have to figure out two different kinds of products and that's twice as much work as a regular kind of company, that's my opinion.

**Justin Dorfman:** That sounds like Adam from Chef, I believe he said the same thing. He's like, I'm never doing an open-source company again.

**Richard Li:** Exactly right, because you've got to figure out this open source product that has lots of value that people love and then you have to figure out another product that people will love even more and are willing to pay money for. So you really have to figure out this thing twice, and then you have all these constraints on that commercial thing, because if you try to take away too many features from the open source they seem to get upset, etc. So the approach that we've taken that has been recently successful for us has been, we have a bunch of high-end enterprise features like single sign on and rate-limiting and things like that. But what we do is we wanted to avoid forking and so what we did was we actually expose all these APIs in the open source. And we basically say, if you want to build your own authentication, rate-limiting, etc. These are a set of documented APIs that you can use and we use the exact same APIs and so if you choose not to actually put that energy into building your own implementation, you can use our implementation which just is packages proprietary sidecar onto the open source. So there's no forking and every time we need more capability in the proprietary, we will evolve these open source APIs, but you can always use these APIs yourself and so that has seemed to work reasonably well. But I would say, Tzury, there's just no easy answer, it's just complicated. Quite frankly, sometimes I go, oh my goodness, it's such a pain in the neck, we are wherever we are.

**Tzury Bar Yochay:** We are already in it Richard.

**Richard Li:** Yes.

**Justin Dorfman:** I think that's actually pretty cool that you have those APIs that are just not private. I've heard gripes from developers who write on top of, for iOS developers that are just so frustrated with Apple, that they get access to some APIs and then they don't get them. So I think that's a good way of going about it but at the same time, turning that into a profitable business, I don't know, I mean, you know better than I, and you seem pretty frustrated. But I think overall, I mean, what you're doing for the Cloud Native ecosystem seems to be helping a lot of companies that could turn into monthly recurring revenue or whatever packages you sell, or is that just not the case yet?

**Richard Li:** I would say it's a lot of work and I'm being a little facetious because we actually have a huge roster of paying customers who are paying us annual subscriptions and giving us really great feedback around our products and using more and more of our products. So we have a lot of API Gateway customers who just started using telepresence for development, we just launched a Cloud product. So there's a lot of things that we figured out with our customers help, around what are ways we can provide additional value beyond the open source. So I think in the end it's actually worth it because from a distribution perspective, we don't have an army of salespeople who are cold calling customers and say, hey, I've got an API Gateway for Kubernetes, do you want it? Which as a developer, I actually appreciate because I don't like getting emails and cold calls from people who have no idea what I'm doing, trying to sell me something that I don't need.

**Justin Dorfman:** Well, especially with how things are changing, where the developers are actually like the purchasing power. That's just what I read, I don't know if that's true or not, but you know developers are never going to answer a call from someone they don't know. I think the way that channel, being in the landscape seems to be working as you say. So it's good to know that the CNCF has that type of power to build an actual ecosystem that can sustain companies and give good jobs to developers and it's exciting to work in open source. It's just not, as you said, it's not easy.

**Richard Li:** Yeah.

**Justin Dorfman:** I want to go over your resume a little bit, it's pretty impressive. You have Red Hat, Rapid Seven, you've done product management and product marketing. Tell me a little bit about your experience at Red Hat, why did you move on to becoming an entrepreneur and so on?

**Richard Li:** Yeah, I think I've always been an entrepreneur at heart and Red Hat was a super entrepreneurial company when I got there. So I was in engineering and then I was able to move into sales and then I was able to move from sales into marketing. So I got exposure to lots of parts of an open source business that was really growing and so it was really exciting time, met a lot of really great people. And then Rapid Seven came calling and they said, well Richard, you've done some engineering, you've done some marketing, some sales so seems like you could probably do product, which requires a little bit of understanding of all of these things. So I joined Rapid Seven was fortunate enough to be part of this huge ride and then we started getting bigger and I thought, well, do I really want to run this sort of big, sort of product organization and long story short, I said, I want to do an even earlier stage startup. I was employee number 600 something at Red Hat then I was employee 60 something at Rapid Seven and then I think I was employee 30, 25, somewhere around there at Duo and I just wanted to go earlier. And so I joined Duo, learned about your stuff there and that I said, okay if I want to do something even earlier than duo, it really just means starting my own company and so that's what I ended up doing. So wasn't as conscious as I've sort of made it out, but that's sort of how things have happened and there's different things you learn at every single stage. If you're a 600 person company, you just run differently from 60 people, which is how we run differently from 20, so.

**Justin Dorfman:** Are you at 60, right now?

**Richard Li:** We are about 50 people right now, so we're closing in on 60 but not quite. But if anyone wants to apply for a job, we'll get the 60.

**Justin Dorfman:** Okay, are you the type of CEO where they could just email you directly?

**Richard Li:** Sure, I mean, we're hiring engineers, marketers, Dev REL, product growth, so you can email me richard@datawire.io. We haven't changed our domain yet because it's actually a lot of work or you could check out our job listings on the Ambassador website.

**Justin Dorfman:** Great, now I saw another thing that caught my eye O'Reilly Velocity Conference. That was one of my favorite conferences in the world when I was in the CDN space, Steve Saunders and Guy Potters are like two guys that I really look up to. What were you doing in the space, like I don't think you're working at a CDN or what part of your career got you into the Velocity Conference?

**Richard Li:** As CEO of Ambassador Labs, we started talking about ingress controllers and networking at Velocity. So I gave a talk, this was in the early days of Kubernetes, but just like sort of some of the nuances of Kubernetes networking and ingress controllers. Because even today, people get very confused about sort of why you need these things and what they're all about. So I gave a talk at Velocity and met a bunch of cool people there, so.

**Justin Dorfman:** Yeah, rest in peace velocity, I think what are they now? Like is it the Fluent Conference or something?

**Richard Li:** Yeah, and O'Reilly, didn't they kill sort of their events business for a while, I don't even know if they're bringing it back.

**Justin Dorfman:** Oh, yeah, I totally forgot.

**Richard Li:** So all these events are sort of a thing of the past.

**Justin Dorfman:** Yeah, I mean O'Reilly, to me threw the best events. My dream was to do a talk for OSCON and I got to do it luckily, but I am definitely sad that I won't be able to attend future Oz Cons. Because I think OSCON for me was just such a amazing experience because I'm so into open source and that's what everyone's going there to talk open source, but yeah, good times but everything does go on.

**Tzury Bar Yochay:** So Richard, you mentioned, starting a company I'd like to, if you can elaborate a little bit about the process of starting a company, was it a decision to become an entrepreneur and then finding a problem to solve or did you have specific problems such as the API Gateway? What was the first product, what was the first thing you worked on?

**Richard Li:** Yeah, Tzury great question. So know I'm an entrepreneur at heart. I think you're either an entrepreneur or you're not, you can work at a larger company, but you're always sort of thinking about how you create things from scratch. And so I knew after leaving DUO I wanted to start a company, I didn't know what to do, so I didn't have any ideas. So I just started talking to anyone just to try to figure out what problems they had. And so originally, I thought, oh I think the metrics and monitoring space was right for disruption. And so I actually started looking at building competitor to Data Dog, Wave Front, Signal Fuse so there were this cohort of next gen monitoring company. So looked into that, decided it was very hard to compete then I ended up discovering microservices. So sort of iterating around a service mesh and that conclusion came to be, that market was... It was too early this was 2014 for us to really get traction on a service mesh. And ultimately, we converged around Kubernetes and seeing that when you start adopting Kubernetes, there's some very essential parts that you need. You need an API Gateway because otherwise there's no way to connect your application to the internet so that's pretty foundational. You need a way to actually develop software, so that's where telepresence came into play. And so it was definitely not an overnight idea, it was definitely an evolution of our thinking over I'd call it probably 18 to 24 months before we really started have conviction around what would make sense for us.

**Tzury Bar Yochay:** And did you go bootstrap, did you raise money, how dis the process went?

**Richard Li:** I bootstraps, just myself for the first, probably year of the process and then once I had an idea of where we wanted to go, I raised a little bit of a seed round so that we could build out a team. And then from there we've been venture funded since then of raising additional rounds as we've expanded and gotten more traction and that sort of thing.

**Tzury Bar Yochay:** You mentioned Telepresence twice already during the conversation, I believe we should hang on these great products for few minutes. Do you mind elaborating about sort of Telepresence, what he does and how it's actually changed the development's life cycle?

**Richard Li:** Yeah, I think one of the things is that what developers discover is that when they start developing a microservices based application on Kubernetes, life gets very complicated. And in particular, when you have a application that is microservices based, it's really running in the Cloud, it's not running locally and that means you can't use your IDE, your debugger or any of these other tools that you're used to using. And your development loop of making a code change suddenly becomes make a code change, build a container, push the container to the registry, deploy it on Kubernetes and then test it. It's very time-consuming and it kills your productivity and so what Telepresence does is it basically creates a network connection between the remote cluster and your laptop. So your laptop is almost as if it's running in the cluster and so by doing this, you could actually run one of your services that you're developing or more of them locally on your laptop, which means you can use your IDE, your debugger, everything while that one microservice can still talk to everything else in the cluster. And there's a lot of sort of additional sophistication we've layered in, but fundamentally it's about bringing the power of local development into your Kubernetes development workflow.

**Tzury Bar Yochay:** Hybrid.

**Richard Li:** Yes, we call it hybrid, the story I like to tell is, it'd be some people run mini cube and things like that and I basically say, have you noticed now that your laptop is really hot on your lap when every time you do development, because you're basically burning all your CPU and memory. You can actually cause yourself physical discomfort during development, and we can alleviate that physical discomfort with software. So when your laptop melting down, you should switch to telepresence.

**Tzury Bar Yochay:** As they said, We'll change your development lifecycle.

**Richard Li:** Exactly.

**Tzury Bar Yochay:** It is what it is Richard.

**Justin Dorfman:** I got a question. So in the latest CNCF Cloud Native survey, 26% of respondents say they use managed Kubernetes services that's up from 23% last year. Does that threaten your business?

**Richard Li:** Not at all, we are very supportive of the managed Kubernetes providers, just because first of all, most of our customers are a lot of our customers are running in one of the managed Kubernetes Clouds. And for us, it's really about making it easier for other organizations about Kubernetes. It makes it easier for them to actually adopt our software because our software only runs in Kubernetes. It doesn't run on VMs, doesn't run anywhere else. So if you're not using Kubernetes, we provide you zero value. But if you're thinking about Kubernetes, there's a lot of things we can do.

**Justin Dorfman:** So your education background is pretty awesome, MIT and Harvard business. What did you do at MIT, tell me, did you make robots or what?

**Richard Li:** So I studied computer science at MIT. I think my special talent was figuring out how to get to know people who were much smarter than me, so that way I could succeed in the coursework. So I did build a robot competed in an autonomous robot competition. I was actually not very useful on the robot team. I think I procured snacks and assembled some Legos, but I had some very smart partners and we actually made it to the playoffs with our robot and then we lost to people who build even better robots. But we did actually quite well, but the credit is not to me.

**Justin Dorfman:** Well getting Legos and snacks, I mean, a contribution is a contribution.

**Richard Li:** Exactly, any way I could help.

**Tzury Bar Yochay:** So other product question Richard, sorry I'm very product focused today.

**Justin Dorfman:** Don't be sorry, that's what this podcast is about.

**Tzury Bar Yochay:** Do you mind elaborating about Argo, Argo one on one, What's the name? So Argo is a cloud native computing foundation project started originally by Intuit and BlackRock for continuous delivery. And what Argo does is you basically install it in your cluster and it implements a good ops workflow. So any changes you make to a source repository that Argo is aware of it, access synchronizes to your cluster. And by deploying Argo, you can actually create a true continuous delivery workflow where you can do things like make a change and make a change in your software. And it will incrementally roll it out as a Canary release over time. And so we're big fans of Argo and we've actually integrated Argo with our API Gateway so that you can do something... Like I have a new version, two to replace version one of my software and using Argo, you can create a policy that says incrementally ramp up traffic. Version two over version one over the course of 24 hours and if you detect anything, anomalous, pause that rollout and then behind the scenes, Argo will then orchestrates and control how much traffic is flowing to version two using Emissary's APIs. And so there's a whole bunch of integration that needs to happen between our API Gateway and Argo and your cluster and your container registry. And so we've been working with the Argo community to kind of integrate this all. So it's actually much easier for you to actually deploy and set up.

**Tzury Bar Yochay:** So if I understood correctly, this is basically an automated Kenari get ups machinery.

**Richard Li:** Yes.

**Tzury Bar Yochay:** Is that how to put it.

**Richard Li:** Yes, exactly and it plugs into your continuous integration system.

**Tzury Bar Yochay:** Wonderful, so Richard do you remember your first customer, again what was the first product that you actually released under a Data Wire, which is today Ambassador Labs?

**Richard Li:** We released a product called the Microservices Development Kit, that was really the first product, but I would say that we didn't get a lot of traction and in fact, I'm a little hazy about who actually ended up using it. We had a few customers; I'd say that the first sort of real customer using us that I remember very distinctly was this company called App Direct and there are sort of this e-commerce platform. They use the API Gateway and we're very excited because they even wrote a blog post about it and that was huge for us because they basically said, well this is what we're using in production for all of our traffic, and this is why we chose to use it. And so that was, I think, a seminal moment in our early company history.

**Tzury Bar Yochay:** So API Gateway was the product that made it you say. So what goes into the API Gateway and what do you think should go into the Proxy into the Envoys? This question I was asked last week, several times by prospects. Do you have any distinct thoughts on it?

**Richard Li:** Yeah, I think the way we think about it is, the data plane is entirely built around the proxy. So anything that's directly managing that traffic is all Envoy proxy and then for us Ambassadors, really a control plane for that data plane. So we're basically connecting to the Kubernetes API or monitoring the API for any changes and then based on those changes we're generating the necessary Envoy configuration to adjust your routing. So that logic around where the traffic goes and what you do with that traffic, that's really part of the control plane and so that's really part of the code that we write. And then the Envoy proxy, which we actually bundle is really that data plane and it actually takes care of the hard part of processing the different bytes are coming across the wire in a high-performance way.

**Tzury Bar Yochay:** And what type of functionality would you keep out of your API Gateway, if there are such?

**Richard Li:** I think that the thing that we've seen people run into trouble with is when people start to put too much business logic into the API Gateway. So you see this actually Netflix built an API Gateway around Java called Zulu and the power Zulu was it provided a very extensible framework for you to really put anything you want into and running at the edge. And so what happened was a lot of people started putting lots of business logic into Zulu and that really makes it very difficult to actually debug what's going on. Zulu is a piece of operational infrastructure and by putting in business logic, you make it much more fragile. And so we prefer a model and we're seeing companies sort of go to model, where a lot of that business logic actually sits in microservices that are then invoked by the API Gateway and traffic at the API Gateway. So I would say I would discourage you from adding business logic into the edge as much as you can.

**Tzury Bar Yochay:** Thank you Richard. One more question in my mind, actually this has been bugging me for the last four years, probably even five. It seems to me, no matter how I look at these Kubernetes and everything on its entire ecosystem seems like there is a lot to do with managing software management and you're writing software that actually manages other software and it's a lot of managing stock involved into what actually goes into the run time into the binary's. And this is for me making a huge distance from the simplicity of Unix philosophy, there used to be everything is a file, just keep things simple and all of a sudden, you can see the same thing with NPM, for those familiar, you want to do like Hello World, you do NPM install and all of a sudden 50 megabytes of JavaScript because it's downloaded to your laptop just to get this Hello World example in React or whatnot. And those are over complex engineering seems to be unavoidable right now because this is how things are actually made and built. But I wonder what is your take on this one?

**Richard Li:** Tzury, it's a really good question and I think with Kubernetes itself; I think the key difference is that the nature of software development has actually changed in a very fundamental way. And what I mean by that is in traditional software development, pre-cloud you really, as a developer are really responsible for writing code and then you had a different team that was really responsible for actually running that code and you have release managers who was responsible for deploying that code. And today with Kubernetes in the Cloud, the model is very different, you are actually responsible for that full software life cycle for your microservice. So I like to say full stack developer now is a full lifecycle developer and you all see this in security, right? Because security, you have this theme of shift left Dev Sec Ops and so what we're seeing is that more and more we're moving away from the specialist role where a dedicated security team is responsible for code security or a dedicated operations team is responsible for operational excellence. And we're saying, hey, developers, you need to actually manage this. This is part of your sort of software life cycle because it's cheaper to actually address the security and operational issues during development than they are post-production. And because of that, the nature of the infrastructure and software that developers need to manage has expanded dramatically and so that's actually the inherent driver of that complexity. And I think there's a lot of different things that can be done about it, we're actually working on a bunch of stuff in this area. We'll be announcing at Cube Con EU on on May 4th. But this is the fundamental challenge, the nature of software development is changing, if the tooling and infrastructure that software developers are being asked to use haven't really adapted to this new mode of work.

**Tzury Bar Yochay:** By the way, if everything is fully automated CICB everywhere everybody is using a bunch of tools and yet you see people working so hard for so many hours every day and that many days every week. It seems like I would imagine comparing a decade ago, software development to today, you would expect developers work like two hours a day, three hours a day, just writing this pure algorithm and everything else should have been automated but we are so far from there.

**Richard Li:** You can argue that Kubernetes has accelerated productivity in some dimensions, right? Like the Last Mile Soft Delivery, clearly Cloud beats CD ROMs any day of the week. But the flip side is developing for the Cloud is way more complicated in a lot of ways and way more responsibility and way more to understand than just building, gooey windows app using Microsoft foundational classes.

**Tzury Bar Yochay:** Where do you see Ambassador Labs Richard, say in five years.

**Richard Li:** So we're very focused around improving the app developer experience on Kubernetes. And so our vision is that people in five years who are developing Kubernetes are using our suite of tools to really do their daily development. Whether it's Telepresence or Ambassador or Argo or all of them, this is what we think people should be doing because we're seeing that when people actually understand how to adopt and use these tools, they can actually really improve their productivity and ship software faster.

**Justin Dorfman:** Awesome, the hardest part of doing this podcast is having to wrap up. I would love to just keep going and maybe we could do a part two sometime soon.

**Tzury Bar Yochay:** I'm all for part two Richard, there are so many questions.

**Richard Li:** It's great talking to you guys, love being on you show. Thanks for having me.

**Announcer:** Community updates, this week we have a new portal on the CNCF website. So turn your browser to community.cncf.io/curiefense, there you able to get updates on our next community meeting indeed, our first community meeting and we're looking forward to having you on there, thanks.
