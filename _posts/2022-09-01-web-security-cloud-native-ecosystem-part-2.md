---
layout: post
title: 'Web Security and the Cloud Native Ecosystem, Part 2'
canonical_url: 'https://www.reblaze.com/blog/curiefense/web-security-and-the-cloud-native-ecosystem-part-2/'
description: Cloud native architectures have new security risks. Here we discuss these challenges, and show how Curiefense addresses them.
published: true
excerpt: Cloud native architectures have new security risks. Here we discuss these challenges, and show how Curiefense addresses them.
createdOn: Thu Sep 01 2022 20:25:00 GMT+0000 (Coordinated Universal Time)
author: Spiros Psarris
mainImage: "/images/Web_Security_on_Service_Meshes,_Part_2__Making_It_Inherent.png"
thumbnail: "/images/Web_Security_on_Service_Meshes,_Part_2__Making_It_Inherent.png"
permalink: /blog/:title/
---

In a previous article, we discussed some of [the benefits of the cloud native ecosystem][1], especially as represented by the [Cloud Native Computing Foundation][2] (CNCF). As the major cloud service providers have expanded their platforms’ capabilities, developers can reduce their workloads by taking advantage of the services they offer. Adding to this, the open source CNCF ecosystem has created a growing number of mature, powerful solutions that include a large number of features out of the box.

These new capabilities have facilitated two additional trends: the growing popularity of containers and microservice architectures. These too have made it much easier to develop and ship applications.

However, these benefits are accompanied by new risks, especially in the area of security. While legacy architectures tended to have well-defined perimeters, modern architectures based on containers and microservices will often (by design) expose much of their ‘interior’ components to the outside world. 

In these situations, the old “castle and moat” security paradigm doesn’t apply. And security solutions that are designed to defend perimeters don’t work very well when there are no perimeters to defend.

However, with new challenges come new solutions. In this article, we’ll look at how the cloud native ecosystem is providing new security capabilities, including how Curiefense can be used to secure modern architectures.

## Requirements
Effective web security requires a number of different elements.

* **Scope**: Traffic must be filtered at multiple levels.

* **Per request**. Many types of attacks are contained within individual requests. For example, content filtering should be performed to detect attempts at code injection. (This is the traditional role of a WAF.)
* **Per requestor**. A security solution must maintain an awareness of everything that has happened within a user session, analyzing all requests within their context. For example, a credential stuffing attack consists of requests (failed login attempts) that individually appear to be innocuous. The hostile nature of the requestor is only realized when considering the overall traffic that it generates.
* **Across all requests**. A security solution must be aware of all incoming traffic as a whole. For example, many DDoS attacks consist of (seemingly) benign requests that appear to be originating from a large number of sources. 

**Visibility**: This too is required at several levels.

* **Real** time: Security managers must be able to understand everything that is happening within their traffic stream as it arrives. (This is especially important when an attack occurs.)
* **Recent**: When recent traffic is analyzed, False Positive and False Negative alarms can be found, and the solution’s configuration can be optimized (e.g., by fine-tuning ACLs) to prevent them from occurring in the future.
* **Historical**: Analysis of data over longer periods can reveal trends and patterns.
* **Customizable reporting**: Traffic data must be available in reports that managers can build and customize according to their needs.

**Monitoring, alerting, and reporting**. Security managers usually want to be notified immediately when incidents occur.

**Centralized control**: A security solution should provide a single, central dashboard for management, regardless of the simplicity or complexity of the architecture being protected.

**Automation**: A security solution must be able to autoscale, load-balance, failover, and otherwise be responsive to changing conditions.

**Vendor-agnostic**: This is inherent in the concept of being “cloud native.” A security solution should be able to secure any web infrastructure, whether it is hosted on a public cloud, private cloud, on-prem, or any combination of these.

**Flexibility**: A robust security solution must be able to protect sites, web applications, and APIs equally well. This implies that it should not rely on detection technologies with limited scope. (For example, bot detection that relies on CAPTCHAs will not effective for API traffic.)

**Separation from business logic**: Developers should not need to worry that any changes to their security configuration would affect their code. As much as possible, application logic should be insulated from traffic processing.

## Leveraging Cloud Native Software
Although some of the items listed above are specific requirements for a security solution, the others are more general. It’s possible to take advantage of existing CNCF software to gain many of these capabilities automatically. For example, Prometheus provides event monitoring and alerting, while Grafana provides customizable dashboards.

Other capabilities will depend on the chosen architecture. For example, using CNCF software, it’s straightforward to run applications and services within a service mesh. (In a service mesh, application instances do not communicate directly with each other; instead, each has a proxy in a sidecar, and all ingress and egress traffic passes through it.) Or, another popular choice is to use an ingress controller, where incoming traffic passes through the ingress point and gets routed to the appropriate destination.

For both of these examples, [Envoy proxy][3]—a CNCF Graduated Project—can be used. Envoy provides many of the requirements listed earlier (such as automation, vendor-agnosticism, etc.), along with some additional nice-to-haves like [built-in RBAC][4]. 

When used as in the examples above, all traffic passes through it; therefore, it’s an ideal location for traffic inspection. Lastly, it is designed to accept HTTP filters, so its functionality can be extended to include web security. 

## Adding Web Security to Cloud Native Architectures
Curiefense adds traffic inspection and filtering to Envoy. It includes content filtering, layer-7 DDoS protection, bot mitigation, rate limiting, flow control, ACLs, and other security modules. Legitimate traffic passes through, while hostile traffic is blocked.

Curiefense fulfills the requirements listed earlier; it integrates with Envoy and provides web security with the necessary scope, visibility, centralized control and visibility, and so on. As part of the CNCF ecosystem (Curiefense is currently a Sandbox Project), it works well with tools such as Prometheus, Grafana, Helm, and others.

## Conclusion
As the CNCF community continues to grow, cloud native applications are becoming increasingly popular, accompanied by a greater reliance on cloud resources and containerization. All of this means traditional security models are no longer adequate, and security rules need to be enforced at locations where traffic is handled.

Service meshes and ingress controllers have entry points defined for services that must be secured. When Envoy is used in these roles, it is the logical place to perform traffic filtering. 

As organizations move increasingly toward cloud native and cloud-agnostic applications, they are realizing they need to shift their approach to web security. Curiefense helps to do this, providing a comprehensive suite of web security tools that integrates with Envoy and the rest of the CNCF ecosystem.

[1]: https://www.curiefense.io/blog/web-security-cloud-native-ecosystem-part-1/
[2]: https://www.cncf.io/
[3]: https://www.envoyproxy.io
[4]: https://www.envoyproxy.io/docs/envoy/latest/intro/arch_overview/security/rbac_filter.html
[5]: https://www.curiefense.io/