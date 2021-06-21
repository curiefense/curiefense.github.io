---
layout: post
title: 'The Performance of Curiefense'
canonical_url: 'https://www.reblaze.com/blog/curiefenses-performance/'
description: How much processing latency does Curiefense introduce? Here are the results from some recent testing, and how you can run the same tests within your own environment.
published: true
excerpt: How much processing latency does Curiefense introduce? Here are the results from some recent testing, and how you can run the same tests within your own environment.
createdOn: Thu Apr 22 2021 19:01:05 GMT+0000 (Coordinated Universal Time)
author: Spiros Psarris
mainImage: "/images/The_Performance_of_Curiefense.png"
thumbnail: "/images/The_Performance_of_Curiefense.png"
permalink: /blog/:title/
---
When evaluating a web security solution, there are multiple aspects to consider. Among them are:

* Effectiveness (there should be a minimal rate of false negative and false positive alarms)
* Ease of administration (there should be an intuitive, easy-to-maintain system)
* And performance (the traffic filtering should introduce as little latency as possible).

This post will be about Curiefense’s performance: we’ll show the results from recent testing, describe how these statistics were generated, and discuss how you can run the same tests within your own environment if desired.

## Possible Sources of Latency

When a web security solution is used to filter incoming traffic, it can introduce three types of latency:

* **Routing**: If the security infrastructure is located in a separate environment, traffic does not flow directly to the origin server. Instead, it must be routed to the solution first for processing, and then forwarded on to the origin. For most solutions, this requires extra travel time.
* **Securing the transmission**: When an external solution is used, it must decrypt incoming traffic before it can perform its analysis. Then it must re-encrypt it before forwarding it to the origin. This cycle of decryption/re-encryption also takes some time.
* **Analyzing the traffic**: A security solution requires some compute time to process the incoming requests and block those that are hostile. 

By running inside the environment, Curiefense avoids the first two types of latency. (This already gives it an advantage over most commercial security solutions, which run outside the origin’s environment and introduce all three types.) 

Of course, Curiefense still requires a non-zero length of time to filter traffic. We periodically measure this for a variety of loads; here’s how we do this.

## Testing Curiefense’s performance

To measure Curiefense’s processing latency, we:

* Use [Fortio][1] as a load-testing tool to generate requests for Curiefense to process.
* Use [Jaeger][2] for request tracing. It attaches a special http header to requests, allowing us to measure the time when requests enter and leave various waypoints.
* Measure the transit time for requests with and without Curiefense being present. The delta is the amount of latency introduced by Curiefense’s processing; ideally, this number would be as close to zero as possible.

To run these tests in your own environment, you can use [this deployment script][3] in the GitHub repo, which will deploy Curiefense into GKE, along with the instrumentation necessary for the test. You will also need the scripts in the repo’s [latency folder][4].

## Some recent results
When we measure Curiefense’s performance, we test different combinations of:

* Number of open connections
* QPS (number of queries per second)

…and then graphing them according to Percentile, where:

* P50 represents the fastest 50 percent of requests, i.e. 50 percent of requests are processed within this time or less.
* P90 represents the fastest 90 percent of requests , i.e. 90 percent of requests are processed within this time or less.
* P99 represents the fastest 99 percent of requests , i.e. 99 percent of requests are processed within this time or less.

Here are the results from a recent test, where the orange lines are the processing times for requests *without* Curiefense (i.e., the infrastructure’s processing time), and the blue lines are the processing times *with* Curiefense.

Note the relevant metric is *not* each blue line’s absolute value, as shown on the left axis. Instead, **Curiefense’s processing time for a given QPS is the difference between the values shown on the orange line and blue line**.

For 10 open connections, processing times at low loads are a few milliseconds, approaching 25 ms at high loads. 

<div align="center">
  <img width="80%" src="/images/Curiefense-performance-10.png" /><br>
  <em>Processing times for 10 open connections</em>
</div>

For 70 connections, times are similar, up to about 30 ms at high loads.

<div align="center">
  <img width="80%" src="/images/Curiefense-performance-70.png" /><br>
  <em>Processing times for 70 open connections</em>
</div>

At 125 open connections, processing times for some queries are still low, while at high loads, some approach 50-65 ms.

<div align="center">
  <img width="80%" src="/images/Curiefense-performance-125.png" /><br>
  <em>Processing times for 125 open connections</em>
</div>

At 250 open connections, we see processing times range from ~20 ms up to a worst case of about 120 ms at high loads. 

<div align="center">
  <img width="80%" src="/images/Curiefense-performance-250.png" /><br>
  <em>Processing times for 250 open connections</em>
</div>

Note however that at the 50th percentile, the latencies are still small (less than 20 ms). In other words, even at high loads and with a large number of open connections, half or more of the incoming requests are processed very quickly, while even the worst cases still have good performance.

## Conclusion

Curiefense is a highly performant security platform. Its architecture eliminates two major sources of added latency that are inherent to most web security solutions. As for processing latency, it is modest for most requests in most use cases. 

Hopefully this brief discussion has been helpful. We run these tests periodically as part of our larger effort to keep improving Curiefense, and make it the best cloud native web security platform possible.

[1]:	https://github.com/fortio/fortio
[2]:	https://www.jaegertracing.io/
[3]:	https://github.com/curiefense/curiefense/blob/main/deploy/deploy-gke.sh
[4]:	https://github.com/curiefense/curiefense/tree/main/e2e/latency
