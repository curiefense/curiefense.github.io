---
title: API Security, Part 3
layout: post
canonical_url: 'https://www.reblaze.com/blog/api-security-part-3/'
description: This article continues the discussion of API security mechanisms, including session flow control, behavioral profiling, content filtering, hostile bot detection, and deep packet inspection.
published: true
createdOn: "Thu Jan 21 2021 06:01:10 GMT+0000 (Coordinated Universal Time)"
author: "Spiros Psarris"
mainImage: "/images/api_security__part_3.png"
thumbnail: "/images/api_security__part_3.png"
permalink: /blog/:title/
redirect_from:
- "/post/api-security-part-3"
- "/api-security-part-3"
---

<p>
    The first article in this series (<a href="https://www.curiefense.io/post/api-security-part-1">API Security, Part 1</a>) discussed some of the challenges in protecting APIs from hostile traffic, and gave an overview of Curiefense’s
    approach. The second article (<a href="https://www.curiefense.io/post/api-security-part-2">API Security, Part 2</a>) discussed these security mechanisms:
</p>
<ul>
    <li>API Discovery</li>
    <li>Identity-Based Filtering</li>
    <li>Mobile Client Authentication</li>
    <li>Rate Limiting</li>
</ul>
<p>In this third and final article, we’ll discuss these additional mechanisms:</p>
<ul>
    <li>API Session Flow Control</li>
    <li>Behavioral Profiling and API Abuse Prevention</li>
    <li>Content Filtering</li>
    <li>Hostile Bot Detection</li>
    <li>Deep Packet Inspection<br /></li>
</ul>
<h2>API Session Flow Control</h2>
<p>Most APIs have a natural, organic flow to them. For legitimate users, there will usually be some calls that occur early in a session, then others will occur afterwards. Many calls will have a specific sequence to them.</p>
<p>For example, a mobile app might begin with a lot of GET calls, as it initializes and retrieves data. Then once initialization is complete, it might send a POST call containing the user’s login details.</p>
<p>Often, attackers will not follow this sequence. For example, a hostile bot might attempt an ATO (account takeover) by jumping straight into a series of POST calls as part of a credential stuffing attack.</p>
<p>Curiefense can block out-of-sequence calls to an API. The screenshot above shows an example that will not permit a POST call unless it was preceded by a GET to /login.html, followed by a GET to /static/login-form.js.</p>
<p>In a later release, Curiefense will not only allow admins to define flow control sequences, it will also analyze past behavior and recommend new sequences for enforcement.</p>
<h2>Behavioral Profiling and API Abuse Prevention</h2>
<p>
    Curiefense has optional modules that use Machine Learning (ML) and UEBA (User and Entity Behavioral Analytics) to learn behavioral patterns and other biometric characteristics of legitimate users. Attempts at anomalous usage can be
    blocked, or merely flagged for monitoring.&nbsp;
</p>
<p>
    After an initial period of learning and accumulation of usage data/metrics, Curiefense’s ML-based UEBA can detect complex, application-specific attacks: everything from inventory denial attacks on travel and ecommerce applications to
    SMS spam being sent through telecom APIs.<br />
</p>
<h2>Content Filtering</h2>
<p>Curiefense admins can set up security policies that define acceptable content for API calls (their headers, payloads, etc.).</p>
<p>
    These policies are flexible. Admins can <strong>ban</strong> calls with defined characteristics, or <strong>allow</strong> calls with defined characteristics, or <strong>require</strong> calls to have defined characteristics, or any
    combination of the above across an API.
</p>
<h2>API Schema Enforcement</h2>
<p>Content filtering can be used for API schema enforcement. In the current version of Curiefense, partial semantic schema validation is available by creating PCRE definitions for parameter properties.&nbsp;</p>
<p>A later release of Curiefense will offer full validation via <em>cloud functions</em>: custom Lua code that can be executed during processing.<br /></p>
<h2>Hostile Bot Detection</h2>
<p>Many traditional security solutions offer bot management only as an add-on module, if it is available at all. We believe this is unfortunate, because almost all web attacks today involve bot activity in one form or another.&nbsp;</p>
<p>So, when designing Curiefense, we wanted bot management and hostile bot detection to be inherent capabilities of the platform.</p>
<p>
    Curiefense allows users to exempt specific bots (e.g., search engine spiders) from filtering if desired. It also includes features for detecting hostile automated traffic, such as consumption of data feeds containing geolocations and
    IPs known to be used by malicious bots.&nbsp;
</p>
<p>
    One of our design goals was to provide human detection that doesn’t require users to do anything (like solving a CAPTCHA puzzle, for example). As a result, Curiefense includes challenge mechanisms to invisibly recognize bots which are
    using headless browsers or emulators, and they take only a few milliseconds to accomplish at the beginning of a session.&nbsp;
</p>
<p>Behavioral profiling and API abuse prevention (which were described earlier) also play a large role in bot detection, since most attacks today involve bots to varying degrees.&nbsp;<br /></p>
<h2>Deep Packet Inspection (WAF)</h2>
<p>Along with everything else described so far, Curiefense includes—of course!—a WAF.&nbsp;</p>
<p>This defends against injection attempts (of SQL, code, and commands), XSS, out-of-limit arguments, malicious payloads, protocol exploits, cookie and session poisoning, and more. Basically, everything that a WAF should defend against.</p>
<p>
    Out of the box, Curiefense includes an extensive database of threat signatures. In addition to this, users can also construct custom API filters to allow or block requests based on their content (as described earlier), and then assign
    these filters to various scopes (from globally across the API down to specific destination endpoints).&nbsp;
</p>
<p>Automation features include regular updates to the threat signature database, and a default security profile that protects every path/endpoint which hasn’t been explicitly configured.&nbsp;</p>
<p>More info: <a href="https://www.curiefense.io/post/the-curiefense-waf">the Curiefense WAF</a>.<br /></p>
<h2>Conclusion</h2>
<p>
    API security is simultaneously one of the most challenging and most important tasks in cybersecurity today. Today’s threat environment includes a wide variety of methods for compromising systems via their APIs; meanwhile, legacy
    security solutions often rely on techniques (such as browser environment identification) which are not applicable to APIs.
</p>
<p>
    We designed Curiefense from the ground up to provide APIs with robust protection. It offers the same range of security technologies to services and microservices as it does to sites and apps, and it offers additional API-specific
    mechanisms as well.&nbsp;
</p>
<p>We believe that Curiefense already offers API security that is at least equal to, and often better than, most solutions available today. However, we aren’t done yet; as mentioned above, there are more features coming.&nbsp;</p>
<p>Please feel free to send us your ideas, feedback, and feature requests. We’d love to hear from you!</p>
<p><br /></p>
