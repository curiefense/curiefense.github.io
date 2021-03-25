---
title: The Curiefense WAF
layout: post
description: Curiefense’s WAF protects against a wide range of attacks. It includes
  an extensive database of threat signatures, and users can create custom security
  policies as well. Here are its capabilities and how to use them.
published: true
createdOn: "Thu Nov 19 2020 21:51:27 GMT+0000 (Coordinated Universal Time)"
author: Spiros Psarris
mainImage: "/images/blog-the-curiefense-waf-1.jpeg"
thumbnail: "/images/blog-the-curiefense-waf-1.jpeg"
redirect_from:
- "/post/the-curiefense-waf"
---

<p>In a previous article, we discussed <a href="https://www.curiefense.io/post/an-intuitive-system">Curiefense’s tag-based real-time traffic processing</a>:<br /></p>
<figure class="w-richtext-figure-type-image w-richtext-align-fullwidth" style="max-width: 1600px;">
    <div>
        <img
            src="/images/blog-an-intuitive-system-1.png"
            width="auto"
            height="auto"
            loading="auto"
        />
    </div>
    <figcaption><em>Four stages of real-time traffic processing</em><br /></figcaption>
</figure>
<p>
    In the diagram, requests enter from the left and proceed through several stages of evaluation. Those which do not violate any security policies or otherwise exhibit anomalous behavior are allowed through to the protected web resource on
    the right.
</p>
<p>The last stage of evaluation is the WAF. In the previous article, this was discussed briefly; in this article, we’ll take a closer look.<br /></p>
<p>
    WAF is an acronym for Web Application Firewall. Often this term is used rather broadly (and imprecisely) to describe a security solution that performs various types of traffic filtering. We’ll use the term here in its narrower, more
    precise sense: a firewall that blocks malicious HTTP requests.
</p>
<h2>Scope of Protection</h2>
<p>
    Curiefense’s WAF protects against a wide range of attacks: SQL injection, code and command injection, directory traversals, file access attempts, cross-site scripting (XSS), and more. It can detect any malicious activity which can be
    discerned by inspecting an individual request and its contents (its headers, arguments, etc.)&nbsp;<br />
</p>
<p>Traditionally, WAFs have been used to protect sites and web applications. Curiefense’s WAF can also protect services and APIs, and offers the same set of capabilities for them as it does for sites and apps.</p>
<h2>The tldr; Curiefense’s WAF in a nutshell</h2>
<p>
    Curiefense includes an extensive and regularly-updated database of threat signatures. By default, it filters every incoming request that matches a signature. However, it is possible to exempt requests from evaluation against one or more
    specific signatures.<br />
</p>
<p>
    Here’s an example of why this can be useful. When an incoming HTTP request has a parameter that contains an apostrophe, this usually indicates an attempt at SQL injection. Therefore, Curiefense includes a threat signature that will
    block this request. However, in some situations, an apostrophe might be valid within certain input parameters. Thus, an administrator can configure Curiefense to exempt those parameters from being evaluated against that signature.<br />
</p>
<p>
    In addition to these built-in threat signatures, Curiefense users can create a wide variety of additional filters. This includes content filtering; users can supply regex patterns which define the allowable structure and content of
    request parameters.<br />
</p>
<p>This capability can be quite powerful. A request that does not match these custom filters can be blocked automatically, or subjected to further scrutiny, depending on the configuration.<br /></p>
<p>
    Curiefense’s WAF policies are combined into WAF Profiles, which can be assigned to any scope of paths/URLs within the protected web service. In a typical deployment, there will be a few specific Profiles customized for individual URLs,
    several additional Profiles for broader paths, and one that applies by default to every URL not otherwise specified.<br />
</p>
<p>That’s the Curiefense WAF in a nutshell. In the remainder of this article, we’ll discuss its traffic filtering in more detail.</p>
<h2>Approach</h2>
<p>Curiefense uses both negative security and positive security models:&nbsp;</p>
<ul>
    <li><strong>Negative security</strong> blocks traffic that matches defined characteristics of malicious traffic, and allows the rest.</li>
    <li><strong>Positive security</strong> allows traffic that matches defined characteristics of legitimate traffic, and blocks the rest.<br /></li>
</ul>
<p>
    Each model has strengths and weaknesses. For example, negative security cannot protect against zero-days, while positive security has a higher risk of producing false-positive alarms. Therefore, Curiefense uses both, to leverage their
    advantages while avoiding their disadvantages. Here’s how it does this.
</p>
<h2>Capabilities</h2>
<p>As mentioned above, Curiefense includes an extensive database of threat signatures. They are viewable in the UI, as shown in the following example. (This particular one detects a specific type of SQL injection.)<br /></p>
<figure class="w-richtext-figure-type-image w-richtext-align-fullwidth" style="max-width: 1600px;">
    <div>
        <img
            src="/images/blog-the-curiefense-waf-2.jpeg"
            width="auto"
            height="auto"
            loading="auto"
        />
    </div>
    <figcaption><em>Curiefense includes an extensive list of signatures. This is one of many for detecting various types of SQL injection.</em></figcaption>
</figure>
<p>By default, a request which matches any of the threat signatures will be blocked. (This is part of Curiefense’s negative security model.)<br /></p>
<p>Additional security policies can be defined by administrators. Some of these also use negative security, such as enforcement of maximum limits for the length and number of headers, cookies and arguments.&nbsp;<br /></p>
<p>Other policies use positive security, such as those which define the allowable content of specific parameters (headers, cookies, and/or arguments). Requests which do not match these policies can be blocked.<br /></p>
<p>Some policies use a hybrid approach. For example, regex patterns can be defined for specific parameters, and used as follows:</p>
<ul>
    <li>If a parameter matches its assigned regex pattern, that parameter is deemed to be legitimate. It is exempted from evaluation against the WAF Signatures.</li>
    <li>If a parameter does not match its regex pattern, that pattern will be evaluated against the WAF Signatures, except for any Signatures that were specifically excluded for that parameter.</li>
    <li>If a parameter does not have a pattern defined, it will be evaluated against all WAF Signatures.&nbsp;<br /></li>
</ul>
<p>To illustrate this, here’s a sample set of WAF security policies (known as a WAF Profile) in the Curiefense UI:<br /></p>
<figure class="w-richtext-figure-type-image w-richtext-align-fullwidth" style="max-width: 1600px;">
    <div>
        <img
            src="/images/blog-the-curiefense-waf-3.png"
            width="auto"
            height="auto"
            loading="auto"
        />
    </div>
    <figcaption><em>A sample WAF&nbsp;Profile.</em></figcaption>
</figure>
<p>If this Profile were active for a URL, and an incoming request was received for that URL, Curiefense would iterate through all of the request’s parameters—through every header, cookie, and argument—and evaluate each one as follows:</p>
<ul>
    <li>If that parameter had a length more than 1024, or it exceeded the allowable number of that type of parameter, the request would be blocked. No further processing would occur.&nbsp;</li>
    <li>
        If the parameter did not have a Matching Value defined (which in the example above means it was any parameter other than a <em>sessionid</em> header or a header beginning with <em>user_</em>), it would be evaluated against the
        threat signature database. If it matched one of the signatures, the request would be blocked and no further processing would occur. Otherwise, processing would continue with the next parameter.
    </li>
    <li>
        If the parameter had a Matching Value definition, and matched it (which in the above example, means it was either a 12-digit <em>sessionid</em> header or an 8-character <em>user_*</em> header), the parameter would be passed, and
        processing would continue with the next parameter.
    </li>
    <li>
        If the parameter had a Matching Value definition but did not match it, Curiefense would respond (depending on its configuration) by either blocking the request (which is the case for the <em>sessionid</em> header in the example), or
        by evaluating the parameter against all threat signatures, except for any signatures listed in the Exclude Sig field.<br />
    </li>
</ul>
<p>
    Note that Curiefense allows the above processing to be bypassed if desired. The “Ignore Alphanumeric Input” option instructs the WAF to treat parameters as benign if they contain only alphanumeric characters. This saves processing time,
    and it can be useful in situations where extensive content filtering is not needed.&nbsp;&nbsp;<br />
</p>
<p>For more information on configuring the Curiefense WAF, see the <a href="https://docs.curiefense.io/console/document-editor/waf-profiles">documentation</a>.</p>
<h2>Other Features</h2>
<p>
    As shown in the UI screenshot, individual filter rules are combined into a WAF Profile. Profiles can be assigned to paths throughout the protected web service, from globally down to individual URLs. Paths can be specified using regex,
    which makes it straightforward to administer even complicated deployments.<br />
</p>
<p>Lastly, as with every other type of configuration within Curiefense:</p>
<ul>
    <li>All WAF administration can be done via REST API as well as through the UI.&nbsp;</li>
    <li>All configurations are maintained in a version history. Users can revert to a previous configuration at any time.</li>
</ul>
<h2>Final Notes</h2>
<p>
    A WAF processes requests, and filters them based on their contents. Many attacks are out of scope for WAF filtering, because the individual requests themselves seem benign. For example, a credential stuffing attack consists of requests
    that are not overtly malicious—they contain no injection attempts, no attempts to access system files, and so on.&nbsp;<br />
</p>
<p>Curiefense can handle those types of attacks as well, because it has a robust set of threat detection capabilities that go far beyond WAF filtering. We’ll discuss those capabilities in future articles.<br /></p>
