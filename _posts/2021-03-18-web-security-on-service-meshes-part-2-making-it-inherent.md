---
layout: post
title: 'Web Security on Service Meshes, Part 2: Making It Inherent'
canonical_url: 'https://www.reblaze.com/blog/web-security-on-service-meshes-part-2-making-it-inherent/'
description: In a service mesh architecture, can legacy security solutions still be used, or will a different approach be required? What about cloud-based solutions? Is there a way to make security an inherent part of the mesh? These questions are the focus of this article.
published: true
createdOn: Tue Mar 18 2021 13:42:55 GMT+0000 (Coordinated Universal Time)
author: Spiros Psarris
mainImage: "/images/6052fc67d0c48c4af4eb1179_cybersecurity-Earth-16x9-p-2000.jpg"
thumbnail: "/images/6052fc67d0c48c4af4eb1179_cybersecurity-Earth-16x9-p-2000.jpg"
redirect_from:
- "/post/web-security-on-service-meshes-part-2-making-it-inherent"
---

In cloud native architectures, service meshes are growing increasingly popular, and for good reason; they offer many benefits, as described in the [previous article](https://www.reblaze.com/blog/web-security-on-service-meshes-part-1-introduction/) in this series. However, as with any architectural innovation, we must ask some important questions about security, such as: Can legacy solutions still be used, or will a different approach be required? What new challenges must be addressed? And what new opportunities are available?

These questions are the focus of this article.


## **Can Legacy Solutions Be Used?**

Legacy bare-metal, “rack and stack” environments present administrators and security staff with a fairly static picture. It’s possible to monitor, maintain, and scale an inventory of running services, open ports, and active nodes with minimal automation and effort. Network boundaries are well defined, with fixed points of ingress and egress.

Traditional security services and devices were designed with this type of environment in mind. A typical firewall or network security device has a physical form factor, managing security for a few hundred nodes/users in a single physical location. The ability to process ingress and egress traffic is a function of the fixed performance and features of the device, like ports and CPU. Therefore, when networks need to scale, this often requires the purchase of a new device to upgrade capabilities. Furthermore, changes in how the underlying application functions, such as opening new ports or features, often require a complex and potentially downtime-inducing configuration change to networking devices, such as WAFs and routers.

Let’s compare this traditional architecture to a modern, distributed cloud native system. The modern system is a dynamic and fluid environment where network boundaries are loosely defined at best, and virtually any resource can be made publicly accessible in just a few clicks.

In this environment, a security solution must provide monitoring and protection that is thorough, effective, granular, and scalable. Legacy solutions are not suited to these requirements. Instead, a new approach is required; one that can address not only these challenges, but some new ones as well.


## **New Challenges for Cloud Native Systems**

The scale and scalability of a typical distributed cloud deployment creates a broad and dynamic attack surface. Maintaining a strong security posture is a non-trivial problem.

The growing dominance of container-based workloads adds additional complications. For example, Docker is a commonly deployed engine; a single node with several deployed containers becomes its own miniature ecosystem, complete with a network, API, and compute resources. Container hosts bring added complexity to an already complex system, which means additional security challenges as well.

Containers are inherently dynamic and ephemeral. They typically have a short lifespan, and use dynamic port assignment to streamline communication with and through their host node. Their underlying engine also has an API that often comes with insecure defaults, plus they require shared access to host resources; a single compromised container can potentially lead to other containers, and perhaps even the host, being compromised. Therefore, in environments where containers are used, it is crucial to have access to a granular view of everything occurring on each host.


## **Cloud Security Solutions**

The major cloud platforms are trying to offer just this. Many vanilla computing resources automatically provision with basic security features like WAF and DDoS protection as a sidecar. The sidecar can also function as an agent for provider-managed services like logging, configuration, and observability. However, rather than offering specialized, custom solutions, these sidecars only provide general, high-level protection from basic threats. Arguably, many of these are primarily meant to help the providers serve their own obligations in the shared security model.

Many third-party cloud-based security solutions are available, but these aren’t ideal either. Most are basically cloud implementations of a traditional castle-and-moat approach; the security solution exists in a separate environment, and all incoming traffic must be routed into that environment, decrypted, analyzed, filtered, re-encrypted, and then forwarded on to the original destination. This is suboptimal for several reasons, most notably in the latency that is added, and the compromises of privacy that are required.

Clearly, a new approach is required—one that lends itself more naturally to new cloud native architectures.


## **Leveraging the Service Mesh**

As discussed in the previous article, service meshes that are based on a proxy such as [Envoy](https://www.envoyproxy.io/) can solve many of the challenges associated with containers and microservices, including communication, discoverability, management, visibility, and more.

Security can also be addressed by the mesh, because each microservice communicates only with its proxy; in turn, the proxy is responsible for communicating with the outside world.

The proxy is an obvious place to perform traffic filtering. All traffic is already flowing through it; we merely need to add the security logic.

In fact, if we could add comprehensive traffic-filtering capabilities to the proxy, then security would become an inherent part of the service mesh. There would be no need to route traffic elsewhere for processing, nor any need to decrypt it outside of the environment. This would be a complete zero-trust model, with no compromises on privacy, that stays within compliance boundaries automatically. Security would be baked into the environment itself.


## **Inherent Security**

This is exactly what Curiefense does. It is an extension of Envoy that adds robust web security to any architecture where Envoy is used (including service meshes, ingress gateways, and other applications). As traffic passes through Envoy, Curiefense analyzes it and allows legitimate traffic to pass through, while malicious activity is blocked.

Doing this in today’s threat environment requires a variety of security technologies. More information on these components of Curiefense is available here:



*   [The Curiefense WAF](https://www.reblaze.com/blog/the-curiefense-waf/)
*   [Tagging and External Threat Feeds](https://www.reblaze.com/blog/an-intuitive-system/)
*   [Hostile bot detection](https://www.reblaze.com/blog/hostile-bot-detection-part-1-replacing-recaptcha/)
*   [API security](https://www.reblaze.com/blog/api-security-part-1/)
*   [How Curiefense works](https://www.reblaze.com/blog/how-curiefense-works/)


## **Conclusion**

While service meshes have some well-known objectives (e.g., to abstract away the communication problems inherent in large-scale distributed systems), they can serve as capable platforms for tackling security challenges as well.

Traditional security solutions were designed for fixed-sized, static deployments. Although cloud-based solutions are more useful in modern architectures, they still retain some of the disadvantages of the traditional approach.

A service mesh architecture allows for web security to be added directly to the ‘fabric’ of the mesh, by adding traffic filtering to the mesh proxies. Curiefense does this with multiple security technologies, giving organizations a way to improve the security posture of their cloud workloads via a cloud native, open source platform.
