---
layout: post
title: 'Changes to Helm charts'
canonical_url: 'https://www.reblaze.com/blog/curiefense-changes-to-helm-charts/'
description: Until recently, Curiefense’s Helm charts were part of the Curiefense repository. Now they have been moved into a separate repo. Here’s why this was done, and the benefits that we expect from this.
published: true
excerpt: Until recently, Curiefense’s Helm charts were part of the Curiefense repository. Now they have been moved into a separate repo. Here’s why this was done, and the benefits that we expect from this.
createdOn: Thu Jun 03 2021 03:02:05 GMT+0000 (Coordinated Universal Time)
author: Flavio Percoco
mainImage: "/images/Helm-16x9.jpg"
thumbnail: "/images/Helm-16x9.jpg"
permalink: /blog/:title/
---
Until recently, Curiefense’s Helm charts were part of the [Curiefense repository][1]. Now they have been moved into a [separate repo][2]. Here’s why this was done, and the benefits that we expect from this.

## Background

Curiefense includes a number of Helm charts for its deployment in various configurations. Previously, these charts were hosted in the main project repo.

This was convenient in some respects, but not ideal in others. For example, someone who was interested in using our charts would have needed to clone the repo, and then run the charts locally somewhere, because we weren’t providing any packages or releases.

## Creating a dedicated repository

We have now created a separate, dedicated repo for the charts. This will provide the following benefits.

First, the charts are more organized. This will become more significant going forward, as more charts are added.

Also, they are easier to use. People who want to deploy Curiefense with Helm in their Kubernetes environments can now just simply run a couple of helm commands, like this:

`⛵ minikube in curiefense-fresh on gh-pages [?] took 3s`<br>
`➜ helm repo add curiefense https://helm.curiefense.io/`<br>
`"curiefense" has been added to your repositories`<br>
`⛵ minikube in curiefense-fresh on gh-pages [?]`<br>
`➜ helm repo update`<br>
`Hang tight while we grab the latest from your chart repositories...`<br>
`[snip]`<br>
`...Successfully got an update from the "curiefense" chart repository`<br>
`[snip]`<br>
`Update Complete. ⎈Happy Helming!⎈`<br>
`⛵ minikube in curiefense-fresh on gh-pages [?]`<br>
`➜ helm search repo curiefense`<br>
`NAME                    CHART VERSION   APP VERSION     DESCRIPTION`<br>
`curiefense/curiefense   1.0.0           1.0.0           Complete curiefense deployment`<br>

Next, we can now cut releases for Helm charts, and version them properly. Basically, the charts have become a separate product that we can develop and support.

## Looking forward

Perhaps most importantly, we expect that having a dedicated charts repo will increase the number of use cases for which charts are available.

There are countless possible use cases, with different requirements and different combinations of settings, and we can’t anticipate all of them. For example, for logging purposes, our charts currently allow users to deploy fluentd, logstash, and filebeat. But someone might be interested in having their logs going into cold cloud storage instead, or they might have some other use case that we haven’t directly considered.

So, some engineers will be customizing charts for their own needs. By creating a separate repository, we’re providing a way for them to share their work back with the community.

And of course, a dedicated repo will provide a central place for people to discuss issues related to our Helm charts. We’re hopeful that this will increase the amount of community participation in their development. 

[1]:	https://github.com/curiefense/curiefense
[2]:	https://github.com/curiefense/curiefense-helm
