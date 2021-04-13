---
title: 'Hostile Bot Detection Part 1: Replacing reCAPTCHA'
layout: post
canonical_url: 'https://www.reblaze.com/blog/hostile-bot-detection-part-1-replacing-recaptcha/'
description: reCAPTCHA is a popular service for automatically excluding bots, but there is a growing dissatisfaction over its UX, effectiveness, and potential lack of privacy. For organizations seeking an alternative, what is available to replace it?
published: true
createdOn: "Thu Jan 28 2021 06:02:08 GMT+0000 (Coordinated Universal Time)"
author: "Spiros Psarris"
mainImage: "/images/blog-hostile-bot-detection-part1-replacing-reCAPTCHA.png"
thumbnail: "/images/blog-hostile-bot-detection-part1-replacing-reCAPTCHA.png"
permalink: /blog/:title/
redirect_from:
- "/post/hostile-bot-detection-part-1-replacing-recaptcha"
- "/hostile-bot-detection-part-1-replacing-recaptcha"
---

<p>Bot detection is crucially important for any organization with a web presence. Almost all attacks involve automated traffic in one form or another, and excluding hostile bots is a vital part of good security.</p>
<p>
    Some malicious bots are easy to detect and block. (<em>“We’re getting ping floods from a few IPs in China.”</em>) But others can be much more subtle. (
    <em>“We’re getting failed login attempts from a cellular IP in the US. Is this a user who forgot their password, or is it a bot attempting an account takeover?”</em>)
</p>
<p>
    Organizations need a reliable way to filter out bots from their traffic. Today, many use Google’s reCAPTCHA service. Its promise is very attractive—just add it to your site, and it will automatically screen out bots. Only human visitors
    will be let through.
</p>
<p>reCAPTCHA is very popular, but it is far from ideal. In fact, a growing number of organizations are removing it from their sites and apps. This is due to a number of issues, including privacy, user experience, and effectiveness.</p>
<p><strong>Privacy</strong>. Across the web today, there’s a growing backlash against the tracking of user behavior. More and more, reCAPTCHA is finding itself in the crosshairs.&nbsp;</p>
<p>
    reCAPTCHA is <a href="https://www.google.com/recaptcha/about/" target="_blank">used on four million sites</a>, including <a href="https://trends.builtwith.com/widgets/reCAPTCHA" target="_blank">40 percent of the top 10,000</a>.
    Webmasters are encouraged to install it on <em>every page</em> of their sites. This gives Google an unprecedented opportunity to collect data on browsing behavior as users move across the web.&nbsp;
</p>
<p>
    It also potentially allows the tracking and identifying of individual users. Some researchers have said that this could be happening; they note that reCAPTCHA seems to operate differently when they browse anonymously, compared to when
    they are logged into their Google accounts. If this is true, Google could be using its cookies to connect browsing-habit data with individual user accounts. Note too that web users cannot opt out of whatever reCAPTCHA is doing on the
    sites that they visit.
</p>
<p>
    We don’t know for sure if any of this is occurring, but that’s the problem. Although many people would like to understand reCAPTCHA’s behind-the-scenes behavior, Google provides few details about it. Thus, many webmasters are concluding
    that the prudent course of action is to assume the worst, and to start looking for alternatives.
</p>
<p>
    <strong>User Experience</strong>: Early versions of reCAPTCHA presented puzzles to web users. The latest version (v3) is supposed to operate invisibly most of the time. Nevertheless, it still sometimes interrupts user sessions with its
    challenges. This introduces friction and degrades the UX.
</p>
<p>
    <strong>Effectiveness</strong>: Despite the compromises described above, many organizations would still accept these drawbacks as long as reCAPTCHA could reliably exclude automated traffic from their sites. Unfortunately, this is no
    longer the case.&nbsp;
</p>
<p>
    For example, researchers have shown that <a href="https://ui.adsabs.harvard.edu/abs/2019arXiv190301003A/abstract" target="_blank">Reinforcement Learning can be used to defeat reCAPTCHA v3</a> with more than a 90 percent success rate.
    There’s even a <a href="https://github.com/dessant/buster" target="_blank">browser extension that can solve reCAPTCHAs</a>. reCAPTCHA is still effective against simple bots, but hackers who are willing to use more sophisticated tools
    can bypass it.
</p>
<h2>Seeking Alternatives</h2>
<p>
    Because of the issues surrounding reCAPTCHA, many organizations are now seeking other services to replace it. Unfortunately, most of these have problems of their own. For example, hCaptcha has a more intrusive UX, and many people object
    to its business model of farming and selling visitor brain-cycles. (It requires visitors to review machine-learning datasets.)
</p>
<h2>Curiefense: Private and Invisible Bot Filtering</h2>
<p>Clearly, something is needed that can provide the benefits promised by reCAPTCHA while avoiding its problems.</p>
<p>
    As an Envoy extension, Curiefense can build traffic filtering directly into containers, service meshes, and so on. Since bot detection is such an important component of web security today, we wanted Curiefense to provide hostile bot
    management that’s just as automated as reCAPTCHA. In other words, once it’s installed, it needs to just work.&nbsp;
</p>
<p>At the same time, we wanted it to avoid reCAPTCHA’s issues. So, Curiefense’s bot detection needs to be:</p>
<ul>
    <li>Private</li>
    <li>Invisible to the visitor at <em>all</em> times</li>
    <li>And effective.</li>
</ul>
<p>Of these goals, privacy was the easiest, since it’s inherent to Curiefense’s architecture. Unless you explicitly share Curiefense’s data with a third party, nobody else has access to it.</p>
<p>
    Invisibility is a more challenging design constraint, but we knew it was worth the effort. In fact, this approach increases security. When a web visitor can’t interact directly with a security mechanism, it makes it much more difficult
    for a threat actor to reverse-engineer it. (For that matter, attackers have no way of knowing that Curiefense is even being used.)
</p>
<p>
    That leaves effectiveness, which of course is the most important aspect, and is also a major challenge. Modern bots can be quite sophisticated, and the latest generation of tools can do a credible job of mimicking human visitors.&nbsp;
</p>
<p>In Part 2, we’ll discuss how Curiefense tackles this problem. Stay tuned!</p>
<p><br /></p>
