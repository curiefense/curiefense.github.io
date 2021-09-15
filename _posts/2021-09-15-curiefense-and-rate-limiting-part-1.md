---
layout: post
title: 'Curiefense and Rate Limiting, Part 1'
canonical_url: 'https://www.reblaze.com/blog/curiefense-and-rate-limiting-part-1/'
description: Rate limiting is a vital, but often under-appreciated, part of cybersecurity. Curiefense includes an extensive featureset that goes beyond the capabilities offered by many commercial solutions.
published: true
excerpt: Rate limiting is a vital, but often under-appreciated, part of cybersecurity. Curiefense includes an extensive featureset that goes beyond the capabilities offered by many commercial solutions.
createdOn: Wed Sep 15 2021 07:45:00 GMT+0000 (Coordinated Universal Time)
author: Spiros Psarris
mainImage: "/images/the_curiefense_waf.png"
thumbnail: "/images/the_curiefense_waf.png"
permalink: /blog/:title/
---
Rate limiting is a vital, but often under-appreciated, part of cybersecurity. Many security solutions include rate limiting features, but often, these are rudimentary. [Curiefense](https://curiefense.io/) includes an extensive featureset that goes beyond the capabilities offered by many commercial solutions.

In this article, which is Part 1 of a short series, we‘ll look at some of the major threats that create a need for robust rate limiting. Later in Part 2, we‘ll dig into Curiefense’s implementation, and look at use cases and examples of specific applications.

## What is Rate Limiting?

At its core, rate limiting is a simple concept; to prevent users from accessing protected resources too frequently.

In this context, “user” refers to any traffic source, whether legitimate or hostile. However, when a rate limit is exceeded, this usually indicates hostile intent.

For example, it is common to enforce rate limits for a login page. Most legitimate users will login successfully in one attempt; some will occasionally require two, or perhaps three, attempts. But a “user” who sends twenty or thirty login requests within a short time is almost certainly a threat actor who is trying to gain unauthorized access.

When a rate limit is exceeded, a security solution can execute an action. The most common action is to block the traffic source for a configured length of time. In some situations, other actions can make sense.

## When is Rate Limiting Useful?

Rate limiting protects against attacks that are based on high numbers of requests. Here are some of the most common.

**Credential Stuffing**. Even today, many web users will still use the same credential set (e.g., an email address and password) across multiple sites. Threat actors know this, and they frequently take advantage of it.

When a site is breached, hackers can often harvest a large number of credential sets from its backend. Later, they will send bots to other sites, which will attempt to “stuff” these stolen credentials into login forms. Usually, some of these login attempts will be successful, and each one allows an ATO (Account Takeover) attack.

However, credential stuffing requires the bots to access a login page over and over, as they try different credential sets. This means that rate limiting can be used to detect and block them.

**Dictionary attacks**. This is similar to credential stuffing, except that the threat actors try to brute-force a login form by guessing credentials (often by systematically submitting different variations until some are found that work). Again, the large volume of requests means that rate limiting is an appropriate defense against these attacks.

**Input fuzzing**. Hackers sometimes try to find vulnerabilities in a web application by submitting large numbers of requests with invalid inputs.

**Payment card discovery and validation**. This is common in industries where online payments are accepted. Bots will stuff payment card numbers into forms to see which ones are valid.

**Enumeration attacks**. Some web applications will return results based on arguments included in URLs (such as `http://www.example.com/results?inputarg=value`). Hackers abuse this by repeatedly submitting requests that systematically enumerate through the range of possible argument values. This is often used in content scraping.

**Content scraping and data theft**. Along with enumeration attacks, there are other ways for hackers to systematically iterate through a site or web application in an attempt to copy all of its data. Scraping is a tremendous problem in some industries; for example, scraping attacks are rampant in ecommerce, where monitoring a competitor’s prices can provide an advantage.

**Inventory Denial**. Hostile actors send inventory denial bots to certain kinds of web applications (especially ecommerce, travel sites, and some others). These bots begin transactions (e.g., they place items in shopping carts, they start to make travel reservations, and so on), while never completing them. This removes the items from available inventory, which prevents legitimate customers from buying. In certain industries, when a web application cannot detect inventory denial activity, it will be continually plagued with these bots.

## Achieving Effective Rate Limiting

In theory, all of the above attacks can be detected by monitoring the rate at which each user submits incoming requests.

In practice, it’s a little more complicated. Correctly choosing and setting configuration parameters is vital, since rate limiting that is overly permissive will allow attacks through, while overly-strict configurations will create false positive alarms. There are also other issues to consider, such as attackers which rotate IP addresses in order to appear as different users and thus, try to avoid rate limiting restrictions.

In Part 2 of this series, we’ll look at how Curiefense tackles this problem.

