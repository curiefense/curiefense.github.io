---
title: An Intuitive System
layout: post
description: To filter HTTP traffic, Curiefense uses an intuitive tag-based system.
  It's flexible and powerful, but still straightforward to understand and use. Here's
  how it works.
published: true
createdOn: "Tue Nov 17 2020 01:56:49 GMT+0000 (Coordinated Universal Time)"
author: Spiros Psarris
mainImage: "/images/blog-an-intuitive-system-1.png"
thumbnail: "/images/blog-an-intuitive-system-1.png"
redirect_from:
- "/post/an-intuitive-system"
---

<p>A key element of every security system is its ease of use. One of Curiefense’s core principles (as discussed in the <a href="https://www.curiefense.io/manifesto">Manifesto</a>) is simplicity:&nbsp;<br /></p>
<blockquote>
    <em>
        Simplicity is a vital ingredient in security. Complex systems tend to be abandoned, and complicated processes tend to be avoided. Even worse, a complicated system can be misconfigured, leading to an illusion of security when in fact
        there are vulnerabilities.<br />
        <br />
        Our goal is to keep Curiefense effective and simple to use, whether it is an API call, UI interaction, automation procedure, or a foundational concept. Simplicity boosts participation and promotes action. We will always choose to
        work harder to keep it as simple as possible, regardless of the complexity beneath the surface.
    </em>
    <br />
</blockquote>
<p>
    Simplicity does not imply a lack of sophistication. On the contrary, Curiefense is designed to provide security powerful enough to handle threats (not only today’s, but also tomorrow’s), while still remaining understandable and
    straightforward to use.<br />
</p>
<p>In this article, we’ll discuss a high-level overview of Curiefense’s traffic filtering. We’ll start with this diagram:</p>
<p><br /></p>
<figure class="w-richtext-figure-type-image w-richtext-align-fullwidth" style="max-width: 1600px;">
    <div>
        <img
            src="/images/blog-an-intuitive-system-2.png"
            width="auto"
            height="auto"
            loading="auto"
        />
    </div>
    <figcaption><em>Two stages of real-time traffic processing</em></figcaption>
</figure>
<p><br /></p>
<p>
    On the left are traffic sources, generating HTTP requests. The requests’ intended destination is the web resource (the site, app, service, or API) at the far right. To get there, they must pass through Curiefense and withstand its
    scrutiny. Only legitimate traffic is allowed through to the protected resource.<br />
</p>
<p>The diagram illustrates two stages of Curiefense: <strong>Profiling</strong> and <strong>ACL Profiles</strong>. We’ll add more stages in a moment, but let’s discuss these two first.</p>
<h2>Profiling</h2>
<p>When Curiefense receives a request, it attaches internal tags to it. The tags will be the basis of subsequent processing in the ACL Profiles.<br /></p>
<p>At this stage, no security policies are being enforced. Curiefense is merely creating a comprehensive profile for this request, by attaching all tags that are applicable to it.<br /></p>
<p>The tags have several sources:</p>
<ul>
    <li>Automatic generation</li>
    <li>External feeds</li>
    <li>Internal Profiling Lists<br /></li>
</ul>
<p><strong>Automatic generation</strong>: Curiefense generates many tags automatically. For example, every request receives tags containing its IP address, ASN, geolocation, and several others.<br /></p>
<p>
    <strong>External feeds</strong>: You can subscribe Curiefense to multiple data feeds, and specify tags to be associated with them. For example, the Spamhaus project <a href="https://www.spamhaus.org/drop/">provides</a> DROP and
    EDROP&nbsp; “drop all traffic” advisory lists of IP addresses and AS numbers, consisting of netblocks that are used by professional spam or cyber-crime operations (for dissemination of malware, trojan downloaders, botnet controllers,
    etc.). Curiefense can attach an appropriate tag (perhaps “spamhaus”) to every incoming request originating from one of these hijacked/leased IPs. You could also subscribe to a feed containing IP addresses currently being used by VPNs,
    and attach a “vpn” tag to requests originating from one of them. And so on.
</p>
<figure class="w-richtext-figure-type-image w-richtext-align-fullwidth" style="max-width: 2206px;">
    <div><img src="/images/blog-an-intuitive-system-3.png" loading="lazy" width="auto" height="auto" /></div>
    <figcaption><em>The UI for subscribing to an external feed (in this example, Spamhaus DROP) and specifying the tag(s) to attach to requests which match it.</em></figcaption>
</figure>
<p>
    ‍<br />
    Out of the box, Curiefense includes a substantial number of preloaded lists. (Currently, there are 18; more will be added soon.) These are automatically updated each day.
</p>
<p>‍<strong>Internal Profiling Lists</strong>: These are created by Curiefense administrators; they contain sets of criteria and the tags to attach when those criteria are matched. Some examples:</p>
<ul>
    <li>Attach “internal” to requests from IPs used by internal teams</li>
    <li>Attach “forbidden” for all HTTP methods except for GET and POST</li>
    <li>Attach “debug” when the query string includes a <strong>debug</strong> parameter which is <strong>true</strong>.</li>
    <li>Attach “goodcookie” when the value of a specified cookie matches a regex of valid content. (Or when it <em>doesn’t</em> match a regex describing forbidden content.)<br /></li>
</ul>
<p>
    Profiling lists are a powerful tool. They allow you to define and attach tags depending on the content and characteristics of incoming requests: their headers, cookies, queries, paths, methods, geolocation, and more, with matching
    conditions specified as regex. For a full description, see the <a href="https://docs.curiefense.io/console/document-editor/profiling-lists">Curiefense documentation for Profiling Lists</a>.<br />
</p>
<p>Once all tags are attached, it’s time to use them. That’s done with ACL Profiles.</p>
<h2>ACL Profiles</h2>
<p>Curiefense uses a request’s tags to enforce security policies. These are defined in an ACL (Access Control List) Profile. An ACL Profile defines the actions to take when certain tags are found, arranged in a sequential order.<br /></p>
<p>Here’s an example in the Curiefense UI:</p>
<figure class="w-richtext-figure-type-image w-richtext-align-fullwidth" style="max-width: 2214px;">
    <div><img src="/images/blog-an-intuitive-system-4.png" loading="lazy" width="auto" height="auto" /></div>
    <figcaption><em>A sample ACL&nbsp;Profile in the Curiefense UI</em></figcaption>
</figure>
<p>‍</p>
<p>Tags are arranged in columns. The columns are evaluated from left to right; if a request matches a tag in a column, the action for that column is taken.</p>
<p>For the example above, this is how each request will be processed;</p>
<ul>
    <li>If the request is tagged with <strong>spamhaus,</strong> <strong>vpn</strong>, or <strong>tor</strong>, block it.</li>
    <li>If the request is tagged with <strong>internal</strong>, allow it and exempt it from further processing.</li>
    <li>If the request is Google's crawler (having been tagged with <strong>googlebot</strong>), exit the ACL process and send the request to the WAF for further evaluation.</li>
    <li>
        If all tags have been evaluated but no matching ACL actions were found, subject the requestor to a <a href="https://docs.curiefense.io/reference/the-challenge-process">bot challenge</a> to verify this is a human user and not a bot.
        If the requestor fails the challenge, block it; otherwise, send the request to the WAF for further evaluation.
    </li>
</ul>
<p>In the diagram above are two additional columns, which aren't used in this example. Their actions are:</p>
<ul>
    <li>Send the request to the WAF for evaluation without a bot challenge.</li>
    <li>Block the request.<br /></li>
</ul>
<p>
    A live deployment of Curiefense will usually have multiple ACL Profiles that are more extensive than the example described here, with different Profiles assigned to different paths/URLs throughout the protected application. Here’s a
    <a href="https://docs.curiefense.io/console/document-editor/acl-profiles"> full explanation of ACL Profiles and their capabilities</a>.<br />
</p>
<p>In the example, you probably noticed that ACL Profile actions often result in the request being sent to the WAF for further evaluation. WAF processing occurs after ACL Profiles, as shown here:<br /></p>
<figure class="w-richtext-figure-type-image w-richtext-align-fullwidth" style="max-width: 1600px;">
    <div>
        <img
            src="/images/blog-an-intuitive-system-5.png"
            width="auto"
            height="auto"
            loading="auto"
        />
    </div>
    <figcaption><em>WAF evaluation occurs after ACL Profiles</em></figcaption>
</figure>
<p>
    The Curiefense WAF enforces a number of rulesets, and blocks requests which do not meet them. This includes a wide variety of protective mechanisms against attacks such as SQL injection, code/command injection, cross-site scripting, and
    so on.<br />
</p>
<p>
    In addition, custom rulesets can be defined for any combination of headers, cookies, and arguments. This includes content filtering: a request can be blocked if it contains certain content, or conversely if it <em>doesn’t</em> contain
    certain content. A later article will cover the Curiefense WAF in more detail.&nbsp;<br />
</p>
<p>Now it’s time to complete the diagram by adding the one remaining stage of processing.</p>
<h2>Rate Limiting</h2>
<figure class="w-richtext-figure-type-image w-richtext-align-fullwidth" style="max-width: 1600px;">
    <div>
        <img
            src="/images/blog-an-intuitive-system-1.png"
            width="auto"
            height="auto"
            loading="auto"
        />
    </div>
    <figcaption><em>Rate&nbsp;Limits are enforced before ACL&nbsp;Profiles</em></figcaption>
</figure>
<p>After tags are attached, but before ACL Profiles are evaluated, Curiefense enforces Rate Limits. These are rulesets which define the frequency and timing with which a traffic source is allowed to access a given resource.&nbsp;<br /></p>
<p>This has many uses, including:</p>
<ul>
    <li>Protecting login forms against credential stuffing and other brute-force attacks</li>
    <li>Protecting checkout pages against payment card validation</li>
    <li>Protecting sites against scraping</li>
    <li>Protecting shopping pages (products, travel reservations, etc.) from inventory denial attacks<br /></li>
</ul>
<p>Rate Limiting rules are straightforward to set up, but they are quite powerful in their capabilities. A later article will explore Curiefense’s Rate Limiting capabilities in more detail.</p>
<h2>Conclusion</h2>
<p>
    This has been an overview of Curiefense’s real-time traffic processing. The main takeaway is this: Curiefense operates according to an intuitive tagging system. Each incoming request receives a set of tags describing its
    characteristics, and then the tags are evaluated to determine the action that is taken.&nbsp;<br />
</p>
<p>There are many more capabilities of Curiefense that we didn’t have a chance to discuss above; they will be covered in future articles. Stay tuned!</p>
<p><br /></p>
