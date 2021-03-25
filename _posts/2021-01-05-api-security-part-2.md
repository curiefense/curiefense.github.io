---
title: API Security, Part 2
layout: post
description: Curiefense includes a number of security mechanisms for defending APIs
  against hostile traffic. This article discusses API Discovery, Identity-Based Filtering,
  Mobile Client Authentication, Behavior Enforcement, and Rate Limiting.
published: true
createdOn: "Tue Jan 05 2021 04:50:01 GMT+0000 (Coordinated Universal Time)"
author: Spiros Psarris
mainImage: "/images/blog-api-security-part2.png"
thumbnail: "/images/blog-api-security-part2.png"
redirect_from:
- "/post/api-security-part-2"
---

<p>
    The previous article (<a href="https://www.curiefense.io/post/api-security-part-1">API Security, Part 1</a>) discussed some of the challenges in protecting APIs from hostile traffic, and gave an overview of Curiefense’s approach. Now in
    this article, we’ll discuss these security mechanisms:
</p>
<ul>
    <li>API Discovery</li>
    <li>Identity-Based Filtering</li>
    <li>Mobile Client Authentication</li>
    <li>Behavior Enforcement</li>
    <li>Rate Limiting<br /></li>
</ul>
<h2>API Discovery</h2>
<p>(This feature is pending in the next release of Curiefense.)&nbsp;</p>
<p>
    The Profiling mechanism (discussed <a href="https://www.curiefense.io/post/an-intuitive-system">here</a>) includes a default ruleset to identify API usage. If you customize it to match your APIs, as shown in the UI screenshot above, it
    creates an easy way to identify incoming calls.
</p>
<p>This has several uses, including:</p>
<ul>
    <li>The ability to assign specific security policies only to API traffic.</li>
    <li>The ability to use Curiefense for performing API Discovery. You can look at your Grafana dashboard and easily see all the incoming API traffic in one snapshot.&nbsp;<br /></li>
</ul>
<h2>Identity-Based Filtering</h2>
<p>Curiefense can block API calls based on the identity of the caller. Examples:</p>
<ul>
    <li>Anonymous proxy and VPN users</li>
    <li>Tor users</li>
    <li>Calls originating from a public cloud IP</li>
    <li>Calls originating from an ASN on the current Spamhaus DROP list</li>
</ul>
<p>Curiefense can also exempt API calls from filtering based on defined characteristics. Example: calls coming from internal IPs.<br /></p>
<h2>Mobile Client Authentication</h2>
<p>
    Mobile/native apps present an interesting situation. On the one hand, they are API clients, and so they will be secured by the usual filtering of API traffic. However, we realized that these apps present an opportunity for additional
    protection.
</p>
<p>
    As a result, Curiefense offers an optional SDK for iOS and Android apps, which are rebuilt and published with the SDK embedded. In use, the SDK signs the application, authenticates the device, hardens all communication, and verifies
    user identity.&nbsp;
</p>
<p>This provides a reliable, secure mechanism to verify that the packets are originating from a legitimate user, and not from an emulator or other bot.<br /></p>
<h2>Behavior Enforcement&nbsp;</h2>
<p>This category includes several different mechanisms, including rate limiting, API session flow control, and behavioral profiling / API abuse prevention.<br /></p>
<h2>Rate Limiting</h2>
<p>You can configure Curiefense to block all API calls that exceed a specific limit within a certain period of time.&nbsp;</p>
<p>(“Limit” usually refers to the number of calls made by a traffic source, but it can also be defined as the number of calls made with a specific header, cookie, argument, attribute, etc.)</p>
<p>This mechanism protects APIs against a wide variety of attacks, including:&nbsp;</p>
<ul>
    <li>DDoS</li>
    <li>ATO (Account Takeover) attempts using credential stuffing, brute-force credential discovery, and so on</li>
    <li>payment card validation and discovery</li>
    <li>data and content scraping&nbsp;</li>
    <li>input fuzzing</li>
    <li>enumeration</li>
    <li>API reverse engineering</li>
    <li>Every other attack that relies upon a significant volume of calls</li>
</ul>
<h2>Coming Up Next</h2>
<p>In the final article in this series, we’ll discuss API session flow control, behavioral profiling, content filtering, hostile bot detection, and deep packet inspection.<br /></p>
