---
title: How Curiefense Works
layout: post
canonical_url: 'https://www.reblaze.com/blog/how-curiefense-works/'
description: "Curiefense represents a new approach to web security: traffic filtering done directly within the service mesh. Here’s how it works."
published: true
createdOn: "Thu Nov 12 2020 21:51:27 GMT+0000 (Coordinated Universal Time)"
author: Spiros Psarris
mainImage: "/images/how_curiefense_works.png"
thumbnail: "/images/how_curiefense_works.png"
permalink: /blog/:title/
redirect_from:
- "/post/how-curiefense-works"
- "/how-curiefense-works"
---

<p>Curiefense represents a new approach to web security: traffic filtering done directly within the service mesh. Here’s how it works.</p>
<h2>A Curiefense Deployment</h2>
<p>
    In the diagram, <strong>User</strong> represents a source of traffic. This could be a person using a browser, a mobile application calling an API, a search engine spider seeking to index a site, or even a hostile bot attempting a
    vulnerability scan. Whatever its nature and motive, the User is trying to communicate with the <strong>Web Service.</strong> This represents the protected site, app, service, etc.<br />
</p>
<p>
    The Web Service is using Envoy as a sidecar. In turn, Envoy is using Curiefense as an HTTP filter. Thus, Curiefense can analyze all traffic attempting to pass through Envoy on its way to the Web Service, and can block hostile requests.
    <br />
</p>
<p>
    As it processes the incoming requests, the Curiefense instance pushes data to <strong>Metrics</strong> and <strong>Logs DB</strong>. Metrics is a store of traffic data and metrics that is made available to the
    <strong>Dashboard</strong> for visual display and reports. (By default, Prometheus metrics and Grafana dashboards are used, but other options can be used instead.) Logs DB is a comprehensive store of data (headers, payloads, tags,
    disposition, etc.) for all requests.&nbsp;<br />
</p>
<p><strong>Web UI</strong> is the web console for Curiefense users. It has two primary capabilities:</p>
<ul>
    <li>
        It provides a visual interface for the traffic data in Logs DB. Users can query and see traffic details at any scale, whether to examine large tranches of traffic or to quickly drill down into individual requests. All requests are
        available here (not only the ones that were blocked); this allows users to understand their traffic streams, and how it is being handled.
    </li>
    <li>The Web UI also provides editing capabilities for Curiefense’s configuration: its security rulesets, policies, and so on. When an admin uses the Web UI to update a configuration, it is pushed to the Config Server.<br /></li>
</ul>
<p>
    The <strong>Config Server</strong> distributes configurations to all Curiefense instances. (More on this in a moment.) It receives updates and instructions from both the Web UI and a REST API, which isn’t shown explicitly in the
    diagram. Everything that can be done through the web console can also be done through the API, via curl and/or a cli tool.&nbsp;<br />
</p>
<p>
    Along with configuration updates from admins, Config Server also receives input from Curiefense’s adaptive mechanisms. The platform uses Machine Learning to update and refine its security posture as the threat environment changes. It
    does this by:
</p>
<ul>
    <li>Continually analyzing its metrics and traffic data to detect new or evolving threats.</li>
    <li>Continually updating its security posture in response to its incoming <strong>Threat Intelligence Feeds</strong> (which contain IP reputation, threat signatures, and so on).&nbsp;</li>
    <li>
        Constructing behavioral profiles of legitimate users for its protected Web Services. Traffic sources which deviate from these and attempt divergent behavior will be detected, flagged, and if the admin desires, automatically blocked.
        <br />
    </li>
</ul>
<p>
    Whenever the Config Server updates a configuration, it pushes the data out to <strong>Cloud Storage</strong>. The Curiefense instance regularly polls Cloud Storage; if its defined configuration has changed, it pulls the new
    configuration and updates itself.&nbsp;<br />
</p>
<p>
    A typical service mesh will have many Web Services, many Envoy proxies, and many Curiefense instances, all of which can be served by one Cloud Storage bucket. Note too that a single Config Server can push changes to many Cloud Storage
    buckets. Thus, an admin can create multiple environments (e.g., prod/devops/qa), and has the ability to control them all from one central location.
</p>
<h2>Summary</h2>
<p>That’s an overview of how Curiefense works. The important things to take away from this are as follows:</p>
<ul>
    <li>Each Curiefense instance plugs directly into Envoy.</li>
    <li>All traffic filtering occurs inside the service mesh. No third party processes the traffic, and no third party has access to it. Curiefense provides absolute privacy.</li>
    <li>Curiefense’s security posture is built from administrative configurations, external threat feeds, internal analysis of the threat environment, and custom behavioral profiles.</li>
    <li>Curiefense can be driven by UI, API, or both. Admins can set up and control multiple environments centrally or separately, as desired.&nbsp;<br /></li>
</ul>
<p>In later articles, we’ll take deeper dives into the various components of Curiefense, along with other topics such as threat detection.</p>
<p><br /></p>
