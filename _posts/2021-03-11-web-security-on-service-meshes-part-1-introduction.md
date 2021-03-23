---
title: 'Web Security on Service Meshes, Part 1: Introduction'
layout: post
description: Many organizations today have embraced microservices; they have abandoned
  the legacy, monolithic infrastructure of applications in the past, and moved into
  a world of APIs, cloud native infrastructure, and containerization. However, while
  microservices provide many benefits, they also introduce unique challenges.
published: true
excerpt: Many organizations today have embraced microservices; they have abandoned
  the legacy, monolithic infrastructure of applications in the past, and moved into
  a world of APIs, cloud native infrastructure, and containerization. However, while
  microservices provide many benefits, they also introduce unique challenges
createdOn: Tue Mar 11 2021 13:42:55 GMT+0000 (Coordinated Universal Time)
author: Spiros Psarris
mainImage: ""
thumbnail: "./images/604b2dba5c9a7036a9c629c6_service-mesh-16x9-p-2000.jpg"
---

Many organizations today have embraced microservices; they have abandoned the legacy, monolithic infrastructure of applications in the past, and moved into a world of APIs, cloud native infrastructure, and containerization. However, while microservices provide many benefits, they also introduce unique challenges, such as:

* How are new services and infrastructure discovered?
* How is interservice communication handled?
* What about the extra issues of using container-based workloads?

To solve the challenges of microservices, a recent innovation has been gaining popularity: the service mesh. This is an addition to distributed infrastructures: an independent layer that adds various features related to the challenges above. With a service mesh in place, a microservice architecture gains improved discoverability, observability, and service-to-service communication.

However, a service mesh isn’t foolproof, and security remains an ever-present concern. Can a service mesh be just as secure as other architectures? Or, going even further: can we take advantage of a service mesh’s features to make security even better than is possible elsewhere?

This two-part article series will answer these questions. But first, we need to lay some groundwork, and understand the issues that a service mesh is meant to solve.

## Why Use a Service Mesh?
Service meshes solve a number of communication problems which arise at the typical scale of most modern deployments. Imagine a basic application architecture with three nodes—A, B, and C. Node A will act as a frontend, which needs data from node B (the backend) and then node C (a database) to complete a request. But what happens if node B is unavailable? Does node A stop serving requests entirely? How long does it retry the connection to B before giving up? Can it find another instance of B to use, and if so, how? And once an instance of B is found, what if C seems to be unavailable, and all these questions have to be answered all over again? How do all the nodes update each other on their health and workloads while also serving client requests?

Without an inherent way to handle these types of communication hurdles, developers are forced to write this logic into their application code. This creates a number of problems.

First, this approach might be manageable for two or three nodes, but what about 1,000? Or 10,000? A small logistics problem about service communication suddenly becomes a very large-scale problem that should not be handled by application and business logic.

Second, as their name implies, microservices are supposed to be small. Bundling communication logic into them makes them larger and (much) more complicated than they need to be.

Third, there are many practical problems associated with direct interservice communication. For example, microservices can be written in different languages using different frameworks, or versions of frameworks, and with different caching mechanisms, and they might not even use the same communication protocols. There are many opportunities for incompatibilities.

Next, this architecture can create management nightmares. When every microservice has its own implementation of interservice communication, it can be near-impossible for admins to set global policies for retries, timeouts & circuit breaking, failovers, and so on.

Next, there is observability—a very serious challenge, related to all of the above. When something goes wrong, but the communication logic is built into the services themselves, then it is very difficult to tell what caused the problem, and how to prevent it from happening again.

Lastly, security is also a serious concern—perhaps the worst one of all. If every microservice can accept incoming connections from the outside world, then it also needs the ability to detect and block threats within the incoming traffic stream. This places an enormous burden on developers, who can no longer focus solely on business logic; instead, they have to stay current on a complicated and ever-evolving threat environment, where attackers are continually improving their tools and capabilities, so they can include effective countermeasures. They also must implement full and robust authentication and authorization capabilities for each microservice that they create. And they have to keep all of this security logic up-to-date over time.

Clearly, it’s unfair to expect developers to do all of this perfectly, all of the time. Most microservices will probably have a significant vulnerability at least some of the time—and on today’s Internet, that level of risk is unacceptable.

So far, there’s lots of bad news here for microservices. Fortunately, there’s a single approach that can address all of these challenges.

## Enter the Service Mesh
A service mesh is an added layer of communication infrastructure, which solves the problems described above, while providing some additional benefits as well.

Without a service mesh, a group of microservices can be thought of as a single layer. They all communicate directly with each other.

With a service mesh, services do not communicate directly with each other. Instead, each service has a proxy, deployed as a sidecar (i.e., it runs in a separate process). In this architecture, services only communicate with, and through, their proxies. All incoming requests (whether from other proxies or the outside world) are sent to the proxy, which forwards them to the microservice. Similarly, all outgoing communication is sent to the proxy, which then routes it to the appropriate destination.

A service mesh creates a separate layer of meta-communication. Nodes and services transmit status data and other information about themselves via their mesh proxy, which transmits that data to other proxies in the stack.

## Solving the challenges

A full-featured service mesh can solve all the problems listed earlier.

**Developers no longer need to write code for network operations** such as the discovery of new infrastructure, health monitoring of existing infrastructure, failover, and so on. This is all done automatically by the service mesh, as the proxies communicate with each other.

**Developers no longer need to address the scale of the network** within which their microservices operate. Each microservice communicates only with its proxy.

**Each microservice is small and lean**; it contains only its business logic, with no need for anything else.

**Languages and frameworks** can be chosen according to the developers’ preferences. A modern mesh proxy such as [Envoy](https://www.envoyproxy.io/) supports a wide variety of them.

**Interservice communication is hardened automatically** by the proxies, wherever it needs to be.

**Management is greatly simplified**. Admins don’t need to try to control network operations via capabilities bundled into a variety of different microservices; instead, they merely administer the mesh, which is designed to be configured and managed easily.

**Admins have access to performance metrics** and other data, getting granular views of the health and performance of specific segments from the proxies.

**Observability and transparency are key features** of modern mesh proxies. In fact, the Envoy project was [born to accomplish this main goal](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy): “The network should be transparent to applications. When network and application problems do occur it should be easy to determine the source of the problem.”

**Security is no longer a problem** for microservice developers, because each microservice no longer needs to concern itself with filtering incoming traffic, authenticating users, and so on. Each microservice communicates only with its proxy, which is a trusted entity.

Obviously, this last point requires that all the “heavy lifting” for security is done within the proxy. In order for microservices to assume that all incoming traffic is benign, their proxies must ensure that it is.

How is this accomplished? That’s a large topic, and it deserves its own article.

In Part Two, we’ll dig deeper into security as it relates to service meshes; we’ll discuss how a mesh architecture lends itself to traffic filtering, and how recent developments have made robust security much easier to achieve when using this architecture. Stay tuned!
