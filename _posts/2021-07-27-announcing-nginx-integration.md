---
layout: post
title: 'Announcing NGINX Support'
canonical_url: 'https://www.reblaze.com/blog/curiefense-now-supports-nginx/'
description: Curiefense v1.4 is now available. This is a milestone release; along with a number of updates and additions, Curiefense is now integrated with NGINX.
published: true
excerpt: Curiefense v1.4 is now available. This is a milestone release; along with a number of updates and additions, Curiefense is now integrated with NGINX.
createdOn: Tue Jul 27 2021 00:00:00 GMT+0000 (Coordinated Universal Time)
author: Spiros Psarris
mainImage: "/images/curiefense-v-1-4-0-released.png"
thumbnail: "/images/curiefense-v-1-4-0-released.png"
permalink: /blog/:title/
---
[Curiefense v1.4.0](https://github.com/curiefense/curiefense/releases/tag/v1.4.0) is now available. This is a milestone release; along with a number of updates and additions, Curiefense is now integrated with [NGINX][1].

NGINX is the world’s most popular web server, and it has other uses as well. Now users can add built-in web security and traffic filtering to their environments.

[Curiefense][2] is the first fully integrated, all-encompassing web security solution in NGINX. Key highlights of this release include:

* An all-in-one web security suite that includes WAF, L7 DDoS mitigation, bot management, session flow control, rate limiting, API protection, and more.
* Free for all users, with no additional add-ons or subscriptions required.
* All processing is performed within the user’s perimeter. (Most solutions decrypt and filter traffic on external infrastructure, which adds latency and creates potential compromises in data privacy. Curiefense is hosted *within* the user’s environment.)
* Open source availability and extensibility, as opposed to a closed source/black-box solution.
* GitOps and developer-friendly platform, drivable by both web console UI and REST API. 
* Full traffic visibility and real-time metrics, with open and extensible dashboards and traffic logs.

[Reblaze][3] launched Curiefense last November, on Marie Curie’s birthday. The GA release occurred in March, and offered support for Envoy Proxy, including containerized deployments such as Kubernetes and service meshes such as Istio.

Now with Curiefense version 1.4, NGINX--which is used by more than 400 million sites--is also fully supported. Users can now make Curiefense’s comprehensive suite of security technologies an inherent part of their environments, blocking hostile traffic while maintaining high performance and complete privacy.

For an overview of Curiefense, see the video Introduction to Curiefense v1.4:

<center>
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/DcQPEu76YkI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

<br>

For more in-depth coverage, see the instructional content on the [Curiefense YouTube channel][4]. 


[1]: https://nginx.org/en/
[2]: https://www.curiefense.io/
[3]: https://www.reblaze.com/
[4]: https://www.youtube.com/channel/UCG_XSaj_YX_26nD3Hvm_6OA