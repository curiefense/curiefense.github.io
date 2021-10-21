---
layout: post
title: 'Curiefense and NGINX Use Cases'
canonical_url: 'https://www.reblaze.com/blog/curiefense-and-nginx-use-cases/'
description: NGINX can be used in a variety of use cases, and for many of them, web security is important. Curiefense is fully integrated with NGINX, and is useful in many of these situations.
published: true
excerpt: NGINX can be used in a variety of use cases, and for many of them, web security is important. Curiefense is fully integrated with NGINX, and is useful in many of these situations.
createdOn: Thursday Oct 14 2021 10:38:00 GMT+0000 (Coordinated Universal Time)
author: Spiros Psarris
mainImage: "/images/curiefense-nginx.png"
thumbnail: "/images/curiefense-nginx.png"
permalink: /blog/:title/
---
[NGINX][1] is the world’s most popular web server, and it has other capabilities as well. Over 400 million sites use NGINX (pronounced engine-x) in one capacity or another.

In version 1.4, [Curiefense][2] added [web security for NGINX][3], and became the first all-encompassing cloud native web security solution that’s fully integrated into it. Curiefense allows NGINX users to easily add built-in web security and traffic filtering to their environments, including WAF, L7 DDoS mitigation, bot management, session flow control, rate limiting, API protection, and more.

In this article, we’ll explore some of the most popular use cases for NGINX, in order to see many of the situations where Curiefense can easily add a comprehensive suite of security technologies.

## Background

NGINX started back in 1999, as a web server designed to solve the C10K problem and be capable of handling 10,000 or more concurrent connections. Since then, NGINX has become much more than just a web server.

Today, it can handle hundreds of thousands of concurrent connections and also act as a reverse proxy, a load balancer, a caching and routing layer, and much more. The most popular version of NGINX is open source, although there is also a paid version with additional features for enterprise customers.

## Use Cases for NGINX

### Web Server

NGINX is one of the fastest web servers available, beating out Apache and others when it comes to benchmarking tools that measure performance. When NGINX was first released, websites were basic HTML pages with mostly static content. Today, sites are rich in dynamic content and have mostly switched to being web applications. NGINX has successfully evolved with the industry and is now capable of handling a variety of web technologies including web sockets, gRPC, HTTP/2, and the streaming of various video formats.

### Load Balancer

NGINX can act as a capable load balancer to distribute traffic across all the nodes in a cluster. It provides built-in load balancing features, with a variety of methods and algorithms at the user’s disposal.

For example, in the sample snippet shown below, the upstream directive is used to define a server group called `auth_backend`, which acts as the load balancer to distribute load between three domains: `auth1.domain.com`, `auth2.domain.com`, and `auth3.domain.com`. Also, there’s a backup server to take over traffic if one of the three servers goes down.

In the server directive, there’s a proxy pass to the server group `auth_backup`, defined earlier, when the location of the request is `/auth`:

```nginx
http {
 upstream auth_backend {
  server auth1.domain.com;
  server auth2.domain.com;
  server auth3.domain.com;
  server auth-backup.domain.com;
 }
 server {
  location /auth {
   proxy_pass https://auth_backend;
  }
 }
}
```

The [documentation][4] on the NGINX website provides detailed information on all available features, including defining a weight for each server in a group and specifying a particular algorithm for each upstream server group.

### Reverse Proxy

This is a common use case of NGINX, as the built-in ability to simply pass a request to another server, server group, or any other application over a variety of protocols, makes it a convenient choice for a reverse proxy server.

Apart from the HTTP protocol, NGINX also supports FastCGI, uwsgi, SCGI, and memcached protocols to forward the requests it gets over HTTP. Also, NGINX provides the ability to change or add headers to requests before forwarding them.

For example, suppose you run an ecommerce business where you have a dedicated microservice for authorization and authentication, a dedicated service for user profiles, and another dedicated service for carts. You can configure an NGINX server as a reverse proxy to easily divert traffic to these dedicated services from one public endpoint, as seen in the code snippet below:

```nginx
http {
 upstream auth_backend {
  server auth1.domain.com;
  server auth2.domain.com;
 }
 upstream user_profiles_backend {
  server profile1.domain.com;
  server profile2.domain.com;
 }
 upstream carts_backend {
  server cart1.domain.com;
  server cart2.domain.com;
 }
 server {
  location /auth {
   proxy_pass https://auth_backend;
  }
  location /profile {
   proxy_pass https://user_profiles_backend;
  }
  location /cart {
   proxy_pass https://carts_backend;
  }
 }
}
```

Above, there are three server groups defined using the upstream directive, which internally all have two servers defined. And in the server directive, in each of the locations `/auth`, `/profile`, and `/cart`, there is a proxy pass happening to corresponding server groups.

This NGINX configuration is using both the load balancing and the reverse proxy features to first pass the request to a specific server group and then distribute the load between multiple servers. With a more advanced configuration and features, NGINX can orchestrate your web traffic much more efficiently.

### API Gateway

Another common use case of NGINX is as an API gateway. Microservices are commonplace in modern applications, which means you cannot ask your API consumers to keep track of the hosts and endpoints of each service. As an API provider, it’s your responsibility to provide a consistent host and endpoint collection for your consumers. This is where API gateways come into the picture.

NGINX provides all the necessary tools to not just define various endpoints but to also route the requests to those backend services while also load balancing for all the various servers for those services. Using NGINX as an API gateway can be simple. Consider the NGINX configuration for routing the traffic for various API endpoints, shown below:

```nginx
http {
 upstream login {
  server 10.0.0.1:80;
  server 10.0.0.2:80;
  server 10.0.0.3:80;
 }
 upstream profile {
  server 10.0.0.4:80;
  server 10.0.0.5:80;
  server 10.0.0.6:80;
 }
 upstream addresses {
  server 10.0.0.7:80;
  server 10.0.0.8:80;
  server 10.0.0.9:80;
 }
 server {
  listen 443 ssl;
  server_name api.example.com;
 
  # TLS config here
  location /api/auth/ {
   location /api/auth/login {
    proxy_pass http://login;
   }
  }
  location /api/user/ {
   location /api/user/profile {
    proxy_pass http://profile;
   }
   location /api/user/addresses {
    proxy_pass http://addresses;
   }
  }
 }
}
```

There are three upstream directives used to define three server groups, and each server group has three servers among which the load will be balanced by NGINX. In the server directive, there are three API endpoints defined using the location directive. Whenever a request is received to any of those three endpoints, NGINX will simply route that traffic to one of three upstream servers.

### Kubernetes Ingress Controller

If you’ve worked with Kubernetes, you know that you need to explicitly manage all web traffic into the Kubernetes cluster, including HTTP, HTTPS, gRPC, TCP, etc. Kubernetes has a product called Ingress for this. NGINX works with Ingress via the [NGINX Ingress Controller][5] to bring all the features of NGINX into the world of Kubernetes.

You can easily install NGINX as another pod along with the load balancer inside a Kubernetes cluster. Along with routing traffic to specific pods in the cluster, NGINX can also act as an API gateway, TLS/SSL terminator, load balancer, etc. within the cluster.

NGINX Ingress Controller also supports the various features that Kubernetes Ingress provides, such as TLS/SSL termination and content-based routing, including host-based and path-based routing. This is a good product if you are already using NGINX in your stack or want to quickly spin up a Kubernetes cluster with multiple pods.

### Resource Compression

Resource compression and decompression is a great feature offered by NGINX for web acceleration. Resource compression in itself is not a new feature; most backend services already compress responses before sending them out. But doing this in the application layer introduces an unwanted delay in delivering responses because compressing data on the fly is a costly operation. To solve this, you can offload resource compression to NGINX.

Enabling this feature is as simple as using the `gzip` directive with the on parameter. NGINX will then start compressing all responses with the MIME type `text/plain`, although this might not help if you’re mostly working with other data formats such as JSON, XML, or static resources. For these, you can use the `gzip_types` directive to provide a list of MIME types for which compression has to be enabled.

And if you’re worried that enabling compression would compress even small responses and waste CPU cycles, you have the option of specifying the minimum size (20 bytes by default) of the responses for which compression has to be enabled.

NGINX also intelligently avoids re-compressing data, for example, by a proxy server. But if the proxy server is not compressing responses, you can still enable compression on select responses coming from the proxy server using the `gzip_proxied` directive.

For clients that don’t support or accept compressed or gzipped responses, NGINX can respond with the uncompressed version of the response, which will happen automatically when `gzip` is enabled.

For static resource responses, NGINX will not perform compression on the fly, which can be considered a drawback. But if `gzip` is enabled, NGINX will look for the .gz version of the file at the same path as the original. If that compressed version of the file is not found at the same path, NGINX will simply serve the uncompressed version of the file. So for static resources, you will have to compress the file beforehand and place the file at the same location as the original.

## Summary

NGINX is a great tool to have in your tech stack for anything to do with HTTP/HTTPS services or APIs. Initially designed as a performant web server, it has become a Swiss Army Knife toolset for managing web traffic with a variety of features.

Above, we discussed six different common uses for NGINX, and there are even more popular use cases beyond these. For a wide variety of them, web security is an issue.

As a web security solution that’s fully integrated with NGINX, Curiefense provides easy-to-add traffic filtering that is:

* Free for all users.
* Open source and extensible.
* GitOps and developer-friendly, drivable by both web console UI and REST API.
* Transparent, including full traffic visibility and real-time metrics, with open and extensible dashboards and traffic logs.

[Reblaze][6] initially launched Curiefense to provide [web security for Envoy Proxy][7], with support for containerized deployments such as Kubernetes and offering [web security for service meshes such as Istio][8]. Now it supports NGINX as well.

If you use NGINX, or are considering doing so, be sure to investigate Curiefense and see what it can offer for your use case.

[1]: https://nginx.org/en/
[2]: https://www.curiefense.io/
[3]: https://www.reblaze.com/blog/curiefense-now-supports-nginx/
[4]: https://docs.nginx.com/nginx/admin-guide/load-balancer/http-load-balancer/
[5]: https://kubernetes.github.io/ingress-nginx/
[6]: https://www.reblaze.com/
[7]: https://www.reblaze.com/blog/adding-web-security-to-envoy/
[8]: https://www.reblaze.com/blog/web-security-on-service-meshes-part-2-making-it-inherent/
