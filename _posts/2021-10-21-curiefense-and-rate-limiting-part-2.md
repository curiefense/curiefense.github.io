---
layout: post
title: 'Curiefense and Rate Limiting, Part 2'
canonical_url: 'https://www.reblaze.com/blog/curiefense-and-rate-limiting-part-2/'
description: We continue our exploration of Curiefense's rate limiting features, which go beyond the capabilities offered by many commercial solutions.
published: true
excerpt: We continue our exploration of Curiefense's rate limiting features, which go beyond the capabilities offered by many commercial solutions.
createdOn: Wed Oct 21 2021 06:45:00 GMT+0000 (Coordinated Universal Time)
author: Spiros Psarris
mainImage: "/images/curiefense-rate-limiting-part-1.png"
thumbnail: "/images/curiefense-rate-limiting-part-1.png"
permalink: /blog/:title/
---

Many web attacks (such as enumeration attacks, credential stuffing, payment card validation, and so on) are not easily recognizable; they consist of a series of requests that do not contain obvious threats. Essentially, the attack consists of the combination of requests and the way in which they are used. 

Rate limiting can be an effective way to detect and block these attacks. In the previous article ([Curiefense and Rate Limiting, Part 1][1]), we looked at rate limiting; we discussed what it is, how it works, and the kinds of threats it can protect against. 

In this article, we’ll dig deeper. Many web security solutions include basic rate limiting; Curiefense goes farther and includes a much more powerful set of capabilities. In this article, we’ll discuss them.

## Basic Rate Limiting

Fundamentally, rate limiting is a simple concept. A security solution can monitor the rate at which each user submits incoming requests. When a user submits too many requests within a defined period of time, those requests can be blocked.

In Curiefense, basic rate limiting is easy to set up. This UI screenshot shows a rate limit that will allow five requests per minute from any IP address. If more than five requests are received, they are blocked until the time period expires and the limit resets.

<div align="center">
  <img width="80%" src="/images/Curiefense-rate-limiting-5-in-60.png"/><br>
</div>

Another important parameter is scope. Global rate limits can be useful, but often, it’s better to define specific limits for different purposes. Otherwise, a limit that is appropriate for some URIs might create problems when applied elsewhere.

Curiefense provides this ability, as shown below. For each rate limit, admins can define the locations where that limit is enforced. This can range from a global scope:

<div align="center">
  <img width="80%" src="/images/Curiefense-rate-limits-global-locations.png"/><br>
</div>

...down to a single endpoint.

<div align="center">
  <img width="80%" src="/images/Curiefense-rate-limits-single-URL.png"/><br>
</div>

A combination of limits can then be defined for different paths or endpoints. For example, a web application’s login form might have a tight rate limit enforced, while access to the rest of the application could be less restricted. 

Not all web security solutions offer rate limiting, and of those that do, many offer only the basic features described above. However, there are many situations where more advanced capabilities are necessary, and Curiefense offers a number of these.

## Going Beyond IPs

Sometimes, counting requests solely according to their IP addresses is not the best approach. For example, when multiple users have the same IP (say, on a shared Wifi connection), their requests will be counted and limited collectively. 

Curiefense allows rate limits to be defined according to combined criteria. For example, instead of counting all requests for each IP, you can maintain separate counts for each unique combination of IP and user ID. 

<div align="center">
  <img width="80%" src="/images/Curiefense-rate-limits-IP-and-userid.png"/><br>
</div>

This would address the shared IP issue described above. However, there’s a caveat with this.

As rate limits get more precise, they can lose their ability to detect broader threats. So, in situations where precise limits are helpful, Curiefense admins should also consider retaining broader limits wherever they are appropriate. 

The example shown above (counting requests according to combined IP and user ID) will not detect credential stuffing attacks, where an attacker is iterating through a list of user IDs and stuffing credential sets into login forms. Therefore, as mentioned earlier, it’s often best to maintain separate and more restrictive limits for sensitive targets such as these.

## Additional Configuration Options 

Curiefense offers a high degree of granularity for rate limits. Along with IP-based limiting, admins can define limits based on any header, cookie, argument, or attribute. 

This can be very powerful. For example, you could limit the rate at which a user can send queries with a field named “download”, even if the user tried to evade the limit by rotating IPs during their session.

Tag-based limiting is also available. Different limits can be enforced according to the tags assigned to each request. Thus, Curiefense’s [automated threat intelligence feeds and self-managed Global Filter lists][2] can all be integrated into rate limiting.

## Dynamic Rate Limiting

So far, we’ve discussed limits based on straightforward counting of requests, such as “count the number of requests coming from an IP.”

However, there are some situations where it’s desirable to monitor conditions, and count the number of times that they change. For example, it’s conceivable that a user might switch ASNs during a session. (Perhaps they were accessing a web application from a coffee shop’s WiFi, then switched to a cell network.) You might want to allow this switch once, but if it occurs again, treat it more suspiciously.

Curiefense provides this capability via the “Event” parameter. Here’s how you would create a limit for this ASN example:

<div align="center">
  <img width="80%" src="/images/Curiefense-rate-limits-ASN-per-user.png"/><br>
</div>

The Event parameter is very powerful. For a more in-depth explanation, see the [Rate Limiting documentation][3].

## Flexible Enforcement Actions

When a rate limit is violated, an action will be triggered. Often, the desired action is to block the over-the-limit request with a `503 Service Unavailable` error. However, Curiefense offers other actions too. 

Admins can choose to: 
- Block the request with a 503 error
- Block the request with a custom error code
- Block the request and redirect the requestor to a specific URL
- Issue a [bot challenge][4], and block the request if the challenge fails
- Tag the request without blocking it (this is especially useful for testing)
- Pass the request, but add a custom header for evaluation by the backend
- Block the request, ban the traffic source, and block all its subsequent requests for a specific length of time.

## Conclusion

As you can see, Curiefense provides a powerful set of rate limiting features. 

Whether you’re using Curiefense as a [web security solution for NGINX][5], or to provide [web security for Envoy Proxy][6], it’s worth spending some time exploring its rate limiting capabilities. They can provide protection against a wide variety of threats that are difficult to detect otherwise. 

[1]: https://www.reblaze.com/blog/curiefense-and-rate-limiting-part-1/
[2]: https://docs.curiefense.io/settings/policies-rules/global-filters
[3]: https://docs.curiefense.io/settings/policies-rules/rate-limits
[4]: https://docs.curiefense.io/reference/the-challenge-process
[5]: https://www.reblaze.com/blog/curiefense-now-supports-nginx/
[6]: https://www.reblaze.com/blog/announcing-general-availability-of-curiefense/