---
title: Adding Web Security to Envoy
layout: post
canonical_url: 'https://www.reblaze.com/blog/adding-web-security-to-envoy/'
description: As Envoy Proxy continues to grow and becomes more widely adopted, a natural next step is to add security capabilities. Curiefense leverages Envoy's extensibility and flexibility to provide traffic filtering for a wide variety of use cases.
published: true
createdOn: "Tue Mar 02 2021 06:06:37 GMT+0000 (Coordinated Universal Time)"
author: Spiros Psarris
mainImage: "/images/blog-adding-web-security-to-envoy.png"
thumbnail: "/images/blog-adding-web-security-to-envoy.png"
redirect_from:
- "/post/adding-web-security-to-envoy"
---

<p>As <a href="https://www.envoyproxy.io/" target="_blank">Envoy</a> continues to grow and becomes more widely adopted, a natural next step is to leverage its inherent extensibility to add security capabilities.</p>
<p>
    Robust security is obviously a vital requirement for any cloud-native organization today. Threat actors are well-financed, highly skilled, and relentless. Meanwhile, organizations continue to deploy more apps, services, and APIs, thus
    continuing to expand their attack surfaces.
</p>
<p>
    The commercial market offers many security solutions which can filter and block hostile requests within incoming traffic. However, these are all proprietary, closed-source products. For users who prefer open solutions, this situation is
    obviously not ideal.&nbsp;
</p>
<p>
    To make matters worse, most proprietary solutions run outside of the user’s perimeter. This means that the traffic stream must be routed to the vendor’s infrastructure, decrypted, analyzed, and then re-encrypted before it can be sent to
    the user’s environment. Not only does this introduce additional latency, it also exposes the user’s data and metrics to a third party, creating a severe compromise of privacy.
</p>
<p>Envoy gives us an opportunity to solve all these problems.</p>
<p>
    Envoy is ideally positioned to perform as a web security mechanism. It can filter traffic at various scales; it can be used as an ingress gateway for an entire environment, or to filter traffic for individual microservices, or anything
    in-between. It does so with an L3/L4 architecture, processing traffic on a byte-by-byte basis—which allows application-layer processing to be added on top.&nbsp;
</p>
<p>Most importantly, it’s extensible. It’s designed to be easily augmented with additional capabilities, such as web security.&nbsp;</p>
<p>
    However, adding security is a non-trivial undertaking. Today’s threat environment is broad and diverse; an Envoy security extension would need internal logic that could analyze traffic in multiple ways, in order to identify the many
    different types of possible attacks. This analysis would need to be stateful, not only within sessions but also across traffic sources. (While some attacks—for example, SQL injection—can be detected within individual requests, other
    types of attacks are waged using a series of requests that individually seem to be benign.)&nbsp;
</p>
<p>Also, the threat environment is constantly evolving. Therefore, this extension would need to consume threat intelligence feeds, and be able to automatically update its security posture as new threats emerged.&nbsp;</p>
<p>
    Furthermore, Envoy is known for having best-in-class observability, so a security extension should be consistent with this. Users should be able to see everything that is happening within their environments, and to understand all the
    traffic-filtering decisions that are being made, and why.&nbsp;
</p>
<p>Lastly, this extension would need to support cloud-native practices, and work well within the ecosystem. Ideally, it would be open source.&nbsp;&nbsp;<br /></p>
<h2>Curiefense: a security extension for Envoy</h2>
<p>Curiefense (<a href="https://www.curiefense.io/">https://www.curiefense.io/</a>) is an OSS Envoy extension designed according to these requirements.&nbsp;</p>
<p>
    Curiefense (named after the famous scientist <a href="https://www.curiefense.io/marie-curie" target="_blank">Marie Curie</a>) adds a broad set of automated web security tools to Envoy: WAF, DDoS protection, bot management, API security,
    rate limiting, session flow control, and more. It includes capabilities that rival, and in many cases exceed, those of commercial closed-source security solutions.
</p>
<p>
    Using an Envoy extension to filter traffic makes external third-party solutions unnecessary, because security can be baked into the environment itself. This means that cloud-native organizations will no longer need to compromise on
    issues such as latency, openness, vendor lock-in, or privacy.&nbsp;&nbsp;&nbsp;
</p>
<p>
    Curiefense is being submitted for sandboxing within the CNCF ecosystem. The project is meant to provide a GitOps platform that is open, extensible, adaptive and evolving—one that provides robust security while still preserving total
    privacy for its users.&nbsp;
</p>
<p>
    We’re eager to <a href="https://github.com/curiefense/curiefense/discussions">receive feedback, opinions, and ideas from the community</a>, to help us make Curiefense a better tool for everyone. Feel free to reach out via our
    <a href="https://github.com/curiefense/curiefense/">GitHub</a>.
</p>
<p><br /></p>
<p><br /></p>
<p><br /></p>
