---
layout: post
title: 'Single- versus Multi-Tenant Web Security, Part 2: Performance and Cost'
canonical_url: 'https://www.reblaze.com/blog/single-versus-multi-tenant-web-security-part-2-performance-and-cost/'
description: The previous article discussed the data protection and privacy advantages of a dedicated single-tenant security architecture. This article continues this theme and discusses performance and cost.
published: true
excerpt: The previous article discussed the data protection and privacy advantages of a dedicated single-tenant security architecture. This article continues this theme and discusses performance and cost.
createdOn: Thu Apr 01 2021 07:05:55 GMT+0000 (Coordinated Universal Time)
author: Spiros Psarris
mainImage: "/images/Single-_versus_Multi-Tenant_Web_Security,_Part_2__Performance_and_Cost.png"
thumbnail: "/images/Single-_versus_Multi-Tenant_Web_Security,_Part_2__Performance_and_Cost.png"
permalink: /blog/:title/
redirect_from:
- "/post/single-versus-multi-tenant-web-security-part-2-performance-and-cost"
- "/single-versus-multi-tenant-web-security-part-2-performance-and-cost"
---
Curiefense is a single-tenant security solution; each protected service has a dedicated Curiefense instance that filters its traffic. In contrast to this, most security solutions today are multi-tenant, and so people tend to think that this is an acceptable approach.

In the [previous article in this series][1], we looked at the data protection and privacy advantages of a single-tenant web security solution, compared to the more typical multi-tenant model. As shown in Figure 1, in a multi-tenant architecture, data is decrypted and processed in an external multi-tenant scrubbing center, then re-encrypted and sent to the target origin server. For organizations which have migrated to the cloud, the web application is often within a VPC (Virtual Private Cloud), as shown here. This type of deployment can expose applications to data leakage, downtime from DDoS attacks that target fellow tenants, and weak compliance links in their data governance chain.

<div align="center">
  <img width="80%" src="/images/multi-tenant-1-1024x576.jpg" /><br>
  <em>Figure 1: Typical multi-tenant web security architecture </em>
</div>

By contrast, a single-tenant web security architecture eliminates these vulnerabilities since the web security solution runs on dedicated resources within the customer’s environment.

<div align="center">
  <img width="80%" src="/images/single-tenant-1024x576.jpg" /><br>
  <em>Figure 2: Single-tenant web security architecture </em>
</div>

These topics were discussed in-depth in Part 1. Now in Part 2, we’ll look at the performance and cost advantages of a single-tenant web security architecture.

## **Why Performance Is Important**
When people talk about web performance, they are generally talking about speed, as measured by metrics like page load time, time to first byte (TTFB), time to start render, time to title, time to interactive, and DNS lookup time.

Today’s Internet users are impatient. Already in 2006, the average online consumer expected pages to load in [no more than 4 seconds][2]. Today, however, nearly half of us expect a maximum load time of 2 seconds, and 18% of us expect a page to load immediately. To make matters worse, the average web user perceives load times as 15% slower than in reality, while later on, they remember that same load time as 35% slower than the actual measured time.

Web application owners go out of their way to optimize performance because a poor UX (user experience) has been shown to have a direct impact on business metrics such as bounce rates, time on site, conversion rate, visitor retention, and even SEO performance. A few statistics that bring home the potential impact of poor performance on the bottom line are:

* While the [average bounce rate][3] of pages that load within two seconds is 9%, that metric jumps to 38% for pages that load in five seconds.
* [Conversion rates][4] drop by 4.42% on average for every second of load time within the first five seconds.
* As early as 2006, Google found that added latency of [one-half of a second][5] reduced traffic and revenue by 20 percent. AWS ran similar tests, introducing delays in increments of 100 ms, and discovered that “even very small delays would result in substantial and costly drops in revenue.” Since then, Internet users have become even more restless, and small amounts of added latency can increase bounce rates significantly.

## **Single-Tenant Web Security and Performance**
The last thing a web application owner wants is for its web security solution to slow down performance. But that’s exactly what can happen in a multi-tenant web security model.

<div align="center">
  <img width="80%" src="/images/multi-tenant-issues-1024x576.jpg" /><br>
  <em> Figure 3: Performance degradation for a multi-tenant web security architecture </em>
</div>

First, as shown in Figure 3, data packets travel in two legs from the user to the origin server: from the client to the external security infrastructure, and then from the infrastructure to the server. Except for the (very rare) situation where the infrastructure is geolocated exactly in-between the user and the origin, this extra routing will add latency and degrade performance.

Second, the data packets are decrypted for processing by the security solution, and then encrypted again for transmission to the web server. As discussed in the first article in this series, this additional decryption/re-encryption can have an impact on data privacy. Here, we note that it also adds more processing time, which again will degrade performance.

Last but not least, in a multi-tenant web security solution, the customer (i.e., the web application owner) has no control over resource sharing and load balancing among the various tenants. In Part 1, we noted how a DDoS attack targeting a fellow tenant could bring down other tenants’ applications as well. But even if that more dramatic scenario does not occur, a customer’s workloads may experience delays while the security platform deals with fluctuating demand across multiple tenants.

In the single-tenant web security model shown in Figure 2, these performance issues are completely eliminated. The web security solution runs within the customer’s environment, so there is no need for extra routing or additional encryption/decryption activities. And because it runs on dedicated infrastructure, the web app owner has complete control over scalability and load balancing so that the expected performance levels can be upheld. (A good security solution will handle all of this automatically.)

## **Single-Tenancy and Lower Cost**
Cloud providers charge for resource usage, including bandwidth. Although the various providers have different cost structures, in general, they:

* Charge ingress fees when traffic enters the cloud infrastructure
* Charge egress fees when traffic leaves the cloud infrastructure
* Waive fees for traffic flow within the infrastructure

A single-tenant web security solution that runs within the customer’s environment can reduce costs significantly compared to a multi-tenant external solution.

First, the single-tenant internal solution runs on resources deployed from within the customer’s account. The optimized and load-balanced solution consumes minimal resources; the customer has full visibility into the resource usage and pays the cloud provider directly. In contrast, the external solution runs on resources controlled by the solution vendor, who bills the customer for usage. In some cases, the vendor may mark up the underlying resource usage cost—an incremental charge that is not necessarily visible to the customer. But even if the markup is zero and the customer pays only its relative share of the solution’s total resource costs, these costs may still be higher than in the single-tenant model due to the overhead introduced by the multi-tenant architecture. For example, additional infrastructure is required for running and administering the multi-tenant system.

Second, the internal single-tenant solution does not create any additional data ingress. Incoming traffic only enters the cloud environment once, as it would even if no security solution was being deployed. In the external solution, traffic first enters and leaves the solution’s environment before entering the origin server’s environment. This additional data ingress and egress incurs extra costs.

If, as is often the case, the customer is using a CDN, then the cost advantages of an internal single-tenant architecture are even greater. The single-tenant solution is most likely integrated with the cloud provider’s CDN service. If the customer uses this, it will benefit from the provider’s pricing policies such as waiving fees to fill CDN caches. Conversely, many external security solutions use their own CDNs and the customer must pay a fill-fee every time a user requests a resource that’s not currently cached.

## **Conclusion**
In [Single- versus Multi-Tenant Web Security, Part 1][6], we described the data protection and privacy advantages of a single-tenant web security architecture compared to a multi-tenant architecture. In this article, we showed how the single-tenant web security model supports better performance and lower costs than the multi-tenant model.

A great deal of development effort and expertise is invested to reduce page load times and other performance delays that detract from the user experience. A multi-tenant web security solution can undermine these efforts by introducing latency due to extra traffic routing and processing for encryption/decryption. These performance issues are completely bypassed in the single-tenant security model.

In addition, the single-tenant model gives the customer complete visibility into bandwidth and other resource usage and pays for those costs directly. In the multi-tenant security solution, the customer pays the vendor for infrastructure usage “blindly”—with no insight into whether infrastructure resources are being used efficiently or if a markup charge is being applied.

[1]:	https://www.curiefense.io/post/single-versus-multi-tenant-web-security-part-1-protection-and-privacy
[2]:	https://www.oreilly.com/library/view/time-is-money/9781491928783/ch01.html
[3]:	https://royal.pingdom.com/page-load-time-really-affect-bounce-rate/
[4]:	https://www.portent.com/blog/analytics/research-site-speed-hurting-everyones-revenue.htm
[5]:	http://glinden.blogspot.com/2006/11/marissa-mayer-at-web-20.html
[6]:	https://www.curiefense.io/post/single-versus-multi-tenant-web-security-part-1-protection-and-privacy