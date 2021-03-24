---
layout: post
title: "API Security, Part 1"
description: "API security is increasingly important on the web today. However, filtering API traffic is, in some ways, quite different than protecting a web application. Here's how Curiefense approaches these challenges."
published: true
excerpt: "API security is increasingly important on the web today. However, filtering API traffic is, in some ways, quite different than protecting a web application. Here's how Curiefense approaches these challenges."
createdOn: "Wed Dec 30 2020 18:30:26 GMT+0000 (Coordinated Universal Time)"
author: ""
mainImage: "/images/security-six-layers-1600.png"
thumbnail: "/images/security-six-layers-1600.png"
---

<p>API security is increasingly important on the web today, thanks to microservice architectures, mobile apps, and other growing trends. It’s a broad subject, and includes requirements such as:&nbsp;</p>
<ul>
    <li>Secure coding practices (e.g., input validation)&nbsp;</li>
    <li>Authentication, authorization, and access control</li>
    <li>Monitoring and analytics (which are necessary for API Management)</li>
    <li>API Discovery (also part of API Management)</li>
    <li>Detecting and blocking malicious/abusive calls to an API.&nbsp;</li>
</ul>
<p>The last requirement (preventing API abuse) is an especially complicated task. Endpoints are subject to a wide variety of malicious activities: hostile bots, volumetric attacks, SQL/code injection attempts, and so on.&nbsp;</p>
<p>As an Envoy plugin, Curiefense focuses on HTTP traffic filtering; it detects and blocks threats within the incoming requests sent to an endpoint. Before discussing them, let’s talk about API protection in general.<br /></p>
<h2>Challenges in Protecting APIs</h2>
<p>Many security solutions don’t protect APIs to the same degree as they do for web applications. There are a couple of reasons for this.</p>
<p>
    First, in the early days of the web, APIs were less important than they are today. Few security solutions were designed with them in mind, and so API security features tended to be added on later. With Curiefense, we didn’t have this
    problem; we had the opportunity to build in API protection from the ground up.&nbsp;
</p>
<p>
    The second issue is that APIs have some unique security requirements, compared to web apps. Some of the conventional techniques used to secure app traffic don’t work for APIs. For example, a traditional way to detect hostile bots is to
    verify the user’s browser environment—but for an API user, there is no browser to verify.
</p>
<p>Here’s how Curiefense addresses these challenges.<br /></p>
<h2>tl;dr: APIs Get Equal Treatment and Full Protection</h2>
<p>Curiefense protects all forms of traffic equally. Calls to a REST API enjoy the same security mechanisms (WAF, DDoS, rate limiting, session control, etc.) as the requests sent to a site or web app.</p>
<p>So, it defends APIs against the full spectrum of web-based attacks: SQL/code injection, XSS, DDoS, ATO (Account Takeover), app/API abuse, vulnerability scans, payment/gift card fraud, input fuzzing, scraping, etc. etc. etc.<br /></p>
<h2>Workflow and Security Mechanisms&nbsp;</h2>
<p>
    All incoming traffic (for web apps, sites, service APIs, mobile/native clients, and so on) is processed using the same tag-based workflow (discussed in-depth in a
    <a href="https://www.curiefense.io/post/an-intuitive-system">previous article</a>), customized for the type of requests being filtered.
</p>
<p>
    This means that administration is exactly the same for APIs as for web applications. All security rulesets are configured and assigned the same way, regardless of the way they are used. We wanted it to be equally straightforward in all
    use cases, whether you’re defining a policy for an individual site URL or you’re assigning rulesets to all API endpoints that match a specified regex.<br />
</p>
<p>Curiefense protects APIs using a variety of security mechanisms. The categories are:</p>
<ul>
    <li>API Discovery</li>
    <li>Identity-Based Filtering</li>
    <li>Mobile Client Authentication</li>
    <li>Behavior Enforcement</li>
    <li>Content Filtering</li>
    <li>Hostile Bot Detection</li>
    <li>Deep Packet Inspection</li>
</ul>
<p>The next two articles in this series will discuss these mechanisms in detail.</p>
<p>‍</p>
