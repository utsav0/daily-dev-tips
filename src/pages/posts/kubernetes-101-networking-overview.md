---
layout: ../../layouts/Post.astro
title: 'Kubernetes 101 - Networking overview'
metaTitle: 'Kubernetes 101 - Networking overview'
metaDesc: 'A closer look at networking within Kubernetes'
ogImage: /images/03-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/8a4d74cb-a654-4377-7d93-f1ae1bc27800
date: 2022-11-03T03:00:00.000Z
tags:
  - kubernetes
---

A big part of Kubernetes is the networking capabilities, we get the option to internally route traffic to neighbouring pods, split workloads on multiple nodes and even open up networking to the outside world.

Let's take a closer look at some of the elements conform networking.

## How does the network get setup

The first thing to note is that Kubernetes networking happens on a DNS level, every pod in a cluster receives it's own cluster wide unique IP address.
This means we don't have to manualy set up mapping between the pods and Kubernetes can resolve connecitons easily for us.

There are a lot of benefits of doing it this way, mainly because the pods get randomly refreshed, and luckily for us Kubernetes can keep perfect track of this.

## Services

A big part of networking in Kubernetes is services, which are a abstract way to expose an application running on a set of pods. Kubernetes under the hood will assign unique IP addresses to each of them, but make them available with one single DNS name. It can also use this behaviour to load balance between the different pods.

What this comes down to is that we as the end user of the application can call `my-service` as the endpoint on whichever protocol we want.
And Kubernetes will know to call the correct pod, which could potentially have a different internal port number.

## Ingress

So far we looked at internal traffic within the cluster to other pods, this is pretty useful but it still means our application can't be accessed from the outside world.

To fix this we can use Ingress, which is an API object that manages external access to a service inside your cluster. (Typically via HTTP(S)).

When defining ingress resources we can define a set of rules about what the outside world will see (an endpoint) and what service this routes to inside Kubernetes internals.

## Nuances

When you are diving into networking in Kubernetes it's a big pool of many, many options you can use.

I would personally advice you to stick to the bare minium as described in this article and expand from here as to which use-case you will have to look into.

As always the [Kubernetes documentation](https://kubernetes.io/docs/concepts/services-networking/) on this provides a massive amount of background information. (Which I tried to abstract to beginners).

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
