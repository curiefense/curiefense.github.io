---
layout: post
title: 'Web Security and the Cloud Native Ecosystem, Part 1: Benefits and Challenges'
canonical_url: 'https://www.reblaze.com/blog/cloud-security/web-security-and-the-cloud-native-ecosystem-part-1-benefits-and-challenges/'
description: The cloud native ecosystem is becoming increasingly popular. In this article, we discuss why this is so, and also examine the challenges created for cloud native web security.
published: true
excerpt: The cloud native ecosystem is becoming increasingly popular. In this article, we discuss why this is so, and also examine the challenges created for cloud native web security.
createdOn: Fri Mar 11 2022 23:25:00 GMT+0000 (Coordinated Universal Time)
author: Spiros Psarris
mainImage: "/images/Web_Security_on_Service_Meshes,_Part_2__Making_It_Inherent.png"
thumbnail: "/images/Web_Security_on_Service_Meshes,_Part_2__Making_It_Inherent.png"
permalink: /blog/:title/
---

Cloud native services have become increasingly popular in the software development space, offering out-of-the-box features to solve problems that would otherwise require significant resources in traditional software development. There are hundreds of cloud services available today to help developers reduce their workloads; for example, object storage services make it easy to save files and other data.

With the increasing dependence of software on cloud services, the term “cloud native” was coined. Cloud native refers to software built around cloud computing and thus benefiting from cloud features like scalability and various implementation services, natively.

The [Cloud Native Computing Foundation (CNCF)][1] is a home for many open-source and vendor-neutral tools and software that can be used out of the box on any public cloud platform. This means that with some minor changes in your settings, you can run these tools in any major cloud, whether AWS, Azure, Google Cloud Platform (GCP), Digital Ocean, or others.

CNCF essentially combines the concepts of cloud native and cloud-agnostic, by promoting tools that can be used across cloud vendors and that have close integration with cloud-specific offerings. Therefore, users aren’t dependent on any single vendor and can easily switch cloud providers without affecting a tool’s compatibility. 

Of course, along with the benefits of cloud come some risks. Chief among these is security. 

In this article, we’ll discuss how the cloud native movement (especially as represented by the CNCF) has changed the developer landscape, and how this impacts the need for web security. 

## The Advantages of CNCF-Driven Development over Traditional Software Development

There are many benefits to cloud computing. Many implementation and management tasks that were previously handled by developers are now becoming the responsibility of cloud vendors. 

For example, you can use database-as-a-service without having to manage the database servers or deal with the complexity involved in failovers, replication, and so on. Similarly, using cache-as-a-service means you don’t have to manage cache servers yourself. These services are generally easy to use; often, all you have to do is feed your applications the appropriate credentials, and let the services do the rest.

Similarly, when it comes to the infrastructure layer, offloading implementation to cloud vendors has made developers’ lives easier by taking over some of their responsibilities. This, in turn, has led to faster development and delivery.

Developers who adopt (whether partially or fully) the open source CNCF ecosystem gain even more benefits. Many CNCF tools are mature, powerful solutions that provide multiple features out of the box. Developers don’t have to put any effort into implementing these capabilities, and so they can focus on other things. 

For example, a tool such as [Envoy Proxy][2] saves developers a great deal of time and effort by eliminating the need to deal with failovers, thresholds, rate limiting, TLS termination, etc. Envoy implements all of these functionalities, therefore your application doesn’t have to. Meanwhile, a tool such as Prometheus allows you to easily scrape metrics from applications and plot them for better visibility.

There is an increasing trend in the usage of tools like Kubernetes, service meshes, Fluentd, FluxCD, and Prometheus at the infrastructure layer, abstracting away the tasks of application instance management from developers. Tools like containerd provide a reliable way to create and run containers in Kubernetes. They also enable developers to ship their whole application as an image to the infrastructure layer.

Containerization enables the cloud native movement in a big way. With just a few basic cloud config changes, containerization lets you run the same software without having to make changes in the code on any cloud or services like EKS, ECS, AKS, and GKE; that is, developers don’t even have to think about what cloud their application will run on. 

All of these trends combined have supported another: the growing popularity of microservices. Thanks to the infrastructure abstraction, powerful open source tools, and other inherent advantages of cloud native development, developers are free to focus on their business logic alone, and can deploy a variety of small, tightly focused services.

## Cloud Native Architectures and Security
While cloud native computing offers many benefits, it also creates some challenges. This is especially true for web security. We’ll discuss two aspects of this: the challenges of securing containers, and of protecting microservice architectures from attackers.

### Securing containers
In traditional models, web security relies mainly on firewalls and server hardening. However, with modern models of containerization, handling changes with firewalls, server hardening, network policies, ACLs, and so on is becoming more and more difficult. 

Server hardening can be achieved through changes in the container’s images and the cluster deployment itself. For example, when launching your Kubernetes cluster, you can follow the [CIS Benchmark for Kubernetes][3]. Networking, on the other hand, is a continuously moving component, with the introduction of new services, deployment of new pods, and older pods going down. 

Of course, it’s normal for pods or VMs to go down in the cloud or Kubernetes. This means it’s necessary to somehow implement security so that any changes in your security rules can persist in the new pod or VM.

If web application firewall changes can be implemented via commands, why can’t this be done in containers? Containers are entities that frequently die, so running security commands will not work. You have to ensure the changes you want to make are built into the images of the containers. Or, you have to find a way to deploy these changes using Kubernetes-native deployment methods, such as init containers or operators.

To secure containers, the modern method for deploying rules involves executing commands at their startup. But this becomes complicated for developers, as the final container needs to be shipped from the security team. It would seem necessary to inject these rules into the container during runtime.

### Securing microservice architectures
Many modern architectures depend on microservices that talk to each other and form a coherent system together. However, a large number of interacting microservices creates a broad and complicated attack surface that can be difficult to secure.

Typically, many of the microservices are Internet-facing. This creates several problems:

* Instead of having a closed, defensible perimeter, much of the system’s “interior” infrastructure is exposed to potential attackers.
* Further, most of this exposure consists of API endpoints. This can make security more difficult, because most security solutions rely on legacy technologies (e.g., reCAPTCHA) that can’t be used to filter hostile API calls.
* The potentially large number of APIs can make it very challenging to create security policies and rulesets that will allow all the various permutations of legitimate usage, while still blocking all forms of malicious traffic.
* Modern CI/CD practices often result in APIs evolving very quickly, again making it difficult to create and maintain robust security policies.
* Administration in general can become very complicated when dealing with microservices. Since each one is a separate entity, this can make it tedious to maintain correct service-to-service whitelisting, for example. 

As if all this weren’t enough, microservice architectures don’t always respond to attacks in the same way as monolithic applications. For example, DDoS attacks can create havoc, especially when their incoming requests trigger further intraservice communication, which amplifies the effects of the attack. 

## Solving the Challenges
We see that cloud native development offers a large number of benefits. It’s unsurprising then that so many organizations are embracing parts of the CNCF ecosystem.

However, we also see that cloud native raises some potentially difficult security issues. In Part 2, we’ll discuss how to solve them.

[1]: https://www.cncf.io/
[2]: https://www.envoyproxy.io
[3]: https://www.cisecurity.org/benchmark/kubernetes/