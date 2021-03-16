---
layout: post
title: "Introducing Curiefense"
description: "Curiefense is a new open-source cloud-native application security platform. It integrates security directly into modern service architectures, and offers multiple benefits that were not previously available in this form."
published: true
excerpt: "Curiefense is a new open-source cloud-native application security platform. It integrates security directly into modern service architectures, and offers multiple benefits that were not previously available in this form."
createdOn: "Mon Nov 09 2020 17:56:04 GMT+0000 (Coordinated Universal Time)"
author: ""
mainImage: "https://uploads-ssl.webflow.com/5fa1500e10bda4bfdcb1b209/5fab730f54e5911ddcef4864_isometric_white_bg-06-06.png"
thumbnail: "https://uploads-ssl.webflow.com/5fa1500e10bda4bfdcb1b209/5fab730f54e5911ddcef4864_isometric_white_bg-06-06.png"
---

<p>Curiefense is an open-source cloud-native application security platform. It offers protection for all forms of web traffic: sites, apps, services, and APIs.&nbsp;<br /></p>
<p>
    Curiefense integrates security directly into modern service architectures. Traditionally, HTTP traffic filtering has been done by a separate (and usually external) product or service. Curiefense moves it inside the perimeter, and bakes
    it into the infrastructure itself—directly into Kubernetes containers, Istio service meshes, and more.&nbsp;<br />
</p>
<p>The platform has many aspects worth discussing. It is:</p>
<ul>
    <li>An extension to <a href="https://www.envoyproxy.io/">Envoy</a>, the popular edge and service proxy.</li>
    <li>An all-in-one web security solution.</li>
    <li>A solution that runs inside your perimeter, ensuring absolute privacy for your users and customers.</li>
    <li>An extensive and unified software suite made by developers, for developers.</li>
    <li>An open source platform for the cloud-native community to build upon.</li>
</ul>
<h2>An Envoy extension</h2>
<p>
    Envoy is a proxy and communication bus with a large and growing number of uses in modern service architectures: edge gateways, service meshes, hybrid networking bridges, and more. The Envoy team continues to expand its capabilities, as
    seen in their recent announcement of the <a href="https://blog.envoyproxy.io/envoy-proxy-on-windows-containers-193dffa13050">Alpha version of Envoy Proxy on Windows Containers</a>.<br />
</p>
<p>Curiefense is integrated with Envoy, extending its capabilities to include web security. Anywhere that Envoy runs, traffic filtering can be added—whether as an ingress gateway, sidecar or reverse proxy, load balancer, etc.&nbsp;</p>
<h2>An all-in-one web security solution</h2>
<p>
    Curiefense defends against a wide variety of attacks and threats: injection attacks, cross-site scripting, account takeovers, API abuse, and many more. It’s no longer necessary to assemble different security technologies (WAF, DDoS
    mitigation, bot management, UEBA based on Machine Learning, etc.) to get complete protection: Curiefense provides it all.
</p>
<h2>A solution that runs inside your perimeter</h2>
<p>
    Traditional cloud security solutions run outside of the network on their own infrastructure. If you use one of these solutions, your traffic will be decrypted, processed, and possibly saved, on that external infrastructure. Worse, that
    external infrastructure is probably being shared with an unknown number of other organizations. This is <em>far</em> from ideal.<br />
</p>
<p>
    Reblaze (the company behind Curiefense) has, from its inception, used a different approach for its web security platform. Every Reblaze deployment runs in a unique VPC, dedicated to that particular customer. Thus, there are no shared
    environments or privacy issues. However, depending on the customer’s architecture, this can still require a few extra resources, such as a VM to run Reblaze.&nbsp;&nbsp;<br />
</p>
<p>Curiefense solves all of these issues and moves web security directly into your infrastructure. No external environments or outside resources are needed; everything happens within the perimeter.<br /></p>
<p>
    This provides complete privacy: no traffic or data is decrypted outside your network. No third party processes it. No third party has access to it. And by eliminating external latency and the need for extra resources, Curiefense also
    provides the best performance possible.&nbsp;&nbsp;
</p>
<h2>A suite made by developers, for developers</h2>
<p>
    Modern practices such as DevOps, immutable infrastructure, and others have transformed the workflows and productivity of many organizations. Unfortunately, many security solutions have not kept up. Often, CI/CD can be throttled by a
    frustrating inefficiency: every time a significant delivery occurs, a WAF (or other security component) must be manually retuned and reconfigured to protect the new app or API feature, or whatever.<br />
</p>
<p>
    Curiefense is developer-friendly from its foundations. It is fully controllable via its web console or via API. (For that matter, the UI itself uses the API.) It supports versioned configurations, multiple and branched environments, and
    more; everything you need to automate your web security and make it part of your pipeline.
</p>
<h2>An open source platform</h2>
<p>Curiefense is available under Apache License Version 2.0.&nbsp;<br /></p>
<p>
    Our desire is to benefit individuals and organizations, and most of all, the cloud native community itself. We are hopeful that the community will augment our (already extensive) roadmap for Curiefense by offering us their opinions,
    ideas, suggestions, and feedback, and help us make Curiefense a better tool for everyone.
</p>
<p>
    ‍<br />
    For more about our vision for Curiefense, see the <a href="https://www.curiefense.io/manifesto">Manifesto</a>.
</p>
