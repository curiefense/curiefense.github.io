---
layout: post
title: 'Changes to logging in version 1.4'
canonical_url: 'https://www.reblaze.com/blog/curiefense-changes-to-logging-in-version-1-4/'
description: Curiefense currently offers a variety of outputs for its traffic logs. In version 1.4, this will change, and later, some of its current behavior will be deprecated. In this post, we’ll discuss how and why this is happening.
published: true
excerpt: Curiefense currently offers a variety of outputs for its traffic logs. In version 1.4, this will change, and later, some of its current behavior will be deprecated. In this post, we’ll discuss how and why this is happening.
createdOn: Wed May 05 2021 20:34:00 GMT+0000 (Coordinated Universal Time)
author: Flavio Percoco
mainImage: "/images/blog-how-curiefense-works.png"
thumbnail: "/images/blog-how-curiefense-works.png"
permalink: /blog/:title/
---
Curiefense currently offers a variety of outputs for its traffic logs. In version 1.4, this will change, and later, some of its current behavior will be deprecated. In this post, we’ll discuss how and why this is happening.

## Background
Curiefense logs all details of all incoming http requests. Full traffic visibility is an important feature of Curiefense, and so the platform exposes comprehensive details, leaving it to the users to filter out the information they don’t currently need.

This logging is done by a service called **curielogger**. It fetches the data from the plugin and the proxy (which currently is **Envoy**; later, **nginx** will also be supported), and sends it all to the final destination. 

Currently, curielogger offers a number of different outputs, including logstash, fluentd, and elasticsearch. 

## The case against logging
It might seem that Curiefense shouldn’t perform any logging. After all, most users will already have a logging solution already running in their environment.

Also, there are many popular logging solutions today. It’s unreasonable to expect curielogger to integrate with every possible configuration that users might have.

Lastly, logging raises a lot of questions, such as:

* How will performance be affected?
* Where will the data be stored?
* How will the data be accessed?
* How will the data be parsed?
* How will the data be analyzed?

Curiefense is a security platform. These sorts of data management issues would seem to be outside of its scope.

## The case for logging
While it’s true that Curiefense is a security platform, this is actually an argument in favor of logging, because a comprehensive store of traffic data is very important. A proper logging setup is a fundamental part of any security product.

Among other things, it is useful for:

* Understanding what is happening within your application
* Understanding the decisions that Curiefense is making about individual requests
* Understanding traffic trends 
* Discovering and diagnosing False Positive and False Negative alarms, which allows you to fine-tune your security policies and eliminate these errors
* Compliance and auditing

As a proxy-based solution, Curiefense does its processing outside of the main user application. If it weren’t logging all of its data, it would be impossible to fully understand what is happening within/to the stream of incoming traffic. Real-time data is frequently very useful, but often, users must look back into time and examine historical data. And so, logs are vital.

Having said that, it’s still important to consider how exactly curielogger should do this, and indeed, what the boundaries of that job should be. Currently, curielogger is doing more than it probably should. In version 1.4, this will change.

## Logging in version 1.4: Refactored to be more flexible
Starting in version 1.4, curielogger will be refactored. It will work according to these principles:

* Curielogger is only concerned about logging events, not about storing them.
* Curielogger should not need to worry about failure tolerance, data retention, data consistency, etc. It will merely get and log the proxy data.
* Different users will prefer different logging solutions. We will not try to integrate with all of them. In fact, we will not integrate directly with *any* of them.
* Instead, we will take advantage of this fact: each logging technology has its own recommended way to fetch logs from stdout. 
* Therefore, if curielogger sends its logs to stdout, the data will be available to whatever logging solution is preferred by the user.

By trimming down curielogger’s possible outputs, and sending log data to stdout according to a well-defined schema, we’ll make it more cloud native, and we’ll also enable users to choose whatever logging technologies they want.

We’ll also include the ability to send logs directly to a storage bucket (since this is important for some enterprise applications).

## Roadmap
These changes will begin in version 1.4. By default, we’ll start logging to stdout, and disable the other loggers. 

However, the other loggers will still be available. This will give users time to migrate over to the suggested architecture. We will provide guidance and recommendations for the migration process, along with config files etc. for a few popular use cases.

Then, starting in version 1.5, direct support for the other loggers will be deprecated and removed from the codebase. 

Soon, we will publish more specific details about the new schema, the migration process, and so on. First, we wanted to explain what will be happening, and why. Hopefully this post has been helpful for this.
