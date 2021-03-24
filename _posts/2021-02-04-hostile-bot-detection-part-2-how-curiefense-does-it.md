---
layout: post
title: "Hostile Bot Detection Part 2: How Curiefense Does It"
description: "The previous article on Hostile Bot Detection discussed why it is so important, and the problems with using reCAPTCHA for this. Now in part 2, we'll discuss how Curiefense identifies and filters malicious bots."
published: true
createdOn: "Thu Feb 04 2021 16:43:09 GMT+0000 (Coordinated Universal Time)"
author: "Spiros Psarris"
mainImage: "/images/blog-hostile-bot-detection-part2-how-curiefense-does-it.png"
thumbnail: "/images/blog-hostile-bot-detection-part2-how-curiefense-does-it.png"
---

<p>In the previous article on this topic, we discussed:</p>
<ul>
    <li>Why it’s so important to have a reliable method of filtering hostile bot traffic</li>
    <li>Why reCAPTCHA has become such a popular service for providing it</li>
    <li>And the problems with reCAPTCHA, including its privacy issues, suboptimal UX, and lack of effectiveness against modern attack tools.</li>
</ul>
<p>Now in this article, we’ll discuss how Curiefense solves this problem.</p>
<h2>Multiple Detection Mechanisms</h2>
<p>Curiefense approaches bot management from multiple angles, and uses a series of filters to block malicious bots. They are:</p>
<ul>
    <li>Threat feeds</li>
    <li>Rate limiting&nbsp;</li>
    <li>ACLs (Access Control Lists)</li>
    <li>Session Flow Control</li>
    <li>Browser verification (for sites and web apps)</li>
    <li>Client verification (for mobile app traffic)</li>
    <li>Biometric behavioral analysis</li>
</ul>
<p>
    These are applied in a multi-stage sequence. To increase performance, low-overhead methods are applied first. Only traffic that passes the initial filtering is subjected to the more computationally demanding methods. It is very
    difficult for any forms of automated traffic to pass through the entire sequence.
</p>
<h2>Threat Feeds</h2>
<p>Curiefense consumes threat intelligence feeds, such as lists of IPs and ASNs currently being used by threat actors. Incoming requests from known-hostile sources can be identified and blocked.</p>
<p>Of the various mechanisms Curiefense uses, this is the simplest. It obviously won’t detect hackers who are using advanced tactics (like abusing cellular gateways to access ‘clean’ IPs).&nbsp;</p>
<p>
    But it will eliminate a large amount of easily-detected hostile requests with minimal processing. For example, if your service is getting traffic from an IP on the Spamhaus DROP list, there’s no reason to waste extra CPU cycles on
    analyzing it.
</p>
<h2>Rate Limiting</h2>
<p>Many bot attacks require a large number of requests to be sent to the targeted system. Common examples are stuffing credentials into login forms, payment card validation, and other types of brute-force attacks.</p>
<p>
    Curiefense can be configured to count requests that match specific characteristics (e.g., requests from the same traffic source, or that have a specific header, and so on). A traffic source can be blocked when it submits too many
    requests within a configured time.
</p>
<p>
    This mechanism doesn’t attempt to identify bots by their characteristics; rather, it blocks hostile traffic (whether bot or human) based on the behavior of the sender. In practice, this winds up filtering mostly bot traffic, since a lot
    of bot-based attacks are volumetric.
</p>
<h2>ACLs&nbsp;</h2>
<p>Curiefense admins can configure the system to reject traffic based on a variety of characteristics. Common examples are Tor browser users, anonymous proxy users, requests originating from a public cloud IP, and so on.&nbsp;</p>
<p>Depending on the ACLs that are chosen, typically a large portion of the excluded requests are sent by bots.</p>
<h2>Session Flow Control</h2>
<p>This is another behavioral mechanism.&nbsp;</p>
<p>
    Many applications have a natural flow to the requests that the server receives. For example, when someone visits a page in a web application, the server might receive a number of GET requests. Then as the user interacts with the page, a
    POST request is sent.&nbsp;
</p>
<p>Often, hostile bots will not follow this sequence. For example, a bot might attempt an ATO (account takeover) by going to a login page and submitting a number of POST calls, without previously sending any GETs.</p>
<p>Curiefense can be configured to enforce request sequences within a session. Any bot (or for that matter, human) who submits out-of-sequence requests can be blocked.</p>
<h2>Browser Verification (for sites and web apps)</h2>
<p>A common way for detecting bots is to verify that the visitor is using a legitimate browser (Chrome, Firefox, Safari, etc.) instead of a headless browser or emulator.</p>
<p>Threat actors know this, of course. As a result, many modern bots masquerade as human visitors using legitimate browsers. Unfortunately, many commercial security solutions cannot detect that this is being done.</p>
<p>
    Curiefense offers optional browser verification capabilities that go beyond the techniques used by most commercial solutions. For example, it injects subtle errors into the browser environment, and sees how the ‘browser’ reacts.
    Curiefense knows the exceptions that are thrown by legitimate browsers (with the claimed version, screen resolution, width, etc.). Other reactions are anomalous, and indicate that this ‘visitor’ is probably a bot.
</p>
<h2>Client Verification (for mobile apps)</h2>
<p>Mobile/native apps have no browser environment to verify. However, they present a different opportunity for client verification.&nbsp;</p>
<p>
    Curiefense offers an optional SDK for iOS and Android apps. The apps are rebuilt and published with the SDK embedded. In use, the SDK signs the application, authenticates the device, hardens all communication, and verifies user
    identity.&nbsp;
</p>
<p>This provides a reliable, secure mechanism to verify that the packets are originating from a legitimate user, and not from an emulator or other bot.</p>
<h2>Biometric UEBA analysis</h2>
<p>
    Curiefense offers an optional Biometric Behavioral Analysis capability. It uses Machine Learning and UEBA (User and Entity Behavioral Analytics) to construct behavioral profiles of legitimate users and how they interact with the
    protected applications. Attempts at anomalous usage can then be detected and blocked.
</p>
<p>
    This is similar to the Session Flow Control described earlier, but much more extensive and sophisticated. Instead of relying upon an admin to define a profile, Curiefense does it automatically, based upon a much wider range of
    parameters. They include:
</p>
<ul>
    <li><strong>Device and software data</strong> (the user’s hardware, its screen resolution and orientation, the software used, battery level, stack trace, fronts and extensions, emulator detection, window size, hidden iframes, etc.)</li>
    <li><strong>User interface and events</strong> (mouse/pointer movements, clicks, taps, zooms, scrolls, keystrokes, speed of entry, etc.)</li>
    <li><strong>Session data</strong> (requests sent, timing, frequency, etc.)</li>
    <li><strong>Consumption analytics</strong> (pages viewed, time spent, resources requested, etc.)</li>
    <li><strong>Application-specific events</strong>, and other results of user actions.</li>
</ul>
<p>
    Threat actors have no access to this data, or the profiles that are created from them. This makes the profiling extremely resistant to reverse-engineering. Note too that the only way for a threat actor to avoid this form of filtering is
    to avoid any activities that a legitimate user would not do. In other words, for hostile actors to avoid being blocked, they cannot perform any hostile actions.
</p>
<h2>Conclusion</h2>
<p>
    In the early days of CAPTCHA and then reCAPTCHA, these technologies provided useful benefits to organizations on the web. However, reCAPTCHA is no longer the best way for automatically blocking hostile bot traffic. These two articles
    have illustrated the differences between reCAPTCHA and Curiefense’s bot filtering.&nbsp;
</p>
<p>
    Curiefense detects bots without relying on any interactions with a human visitor. All of the techniques it uses are accomplished in a few milliseconds, and much of the processing (such as the browser verification) only occurs once, at
    the beginning of a session.
</p>
<p>Of course, threat actors will continue to refine their techniques and attack tools. At the same time, we’re continuing to improve Curiefense. We have a variety of new features on the way, and more are planned beyond those.</p>
<p>
    If you are a security enthusiast, devops engineers, etc. and want to know more about Curiefense, or if you’d like to file bugs or feature requests, feel free to reach out via our
    <a href="https://github.com/curiefense/curiefense">GitHub</a>. We’d love to hear from you!
</p>
