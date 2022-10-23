---
layout: ../../layouts/Post.astro
title: 'Kubernetes 101 - Pods'
metaTitle: 'Kubernetes 101 - Pods'
metaDesc: 'A closer look at pods, the smallest component in Kubernetes'
ogImage: /images/01-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/428cd775-210f-4bc6-9948-f4a316e56700
date: 2022-11-01T03:00:00.000Z
tags:
  - kubernetes
---

I wanted to explore Pods in more detail as they are quite an essential aspect of the Kubernetes ecosystem.

You can take the name Pod as the literal sense of "pod of whales" or "pea pod," meaning it's one single element in a group of elements.

In the technical sense, a pod is a group of containers with shared storage and network resources. The pods' content is always co-located, co-scheduled, and run in a shared context.

So what exactly is this container we can run on it? It comes down to your application container.
For the sake of simplicity, imagine each pod can run a docker container. Depending on your setup, it can run multiple containers inside one architecture.

## What does a pod do?

Pods are cheap systems. Kubernetes can quickly spool them up, destroy them or replace them.
It takes little to no effort to replace pods, meaning they are stateless and pure.

As mentioned, most of the time, it runs one container, but in some cases, it can run a closed system that needs multiple containers. (Imagine app + background worker).

## Why pods over containers?

You might be wondering why don't we deploy the container directly.
Why is the pod layer needed?

The most straightforward answer to this question is that pods can access shared resources on the local network, meaning they can communicate between them. If we again group the containers they run in, they have yet another way of communicating with the outside pods.

Another reason is their health system in place, making them easily detectable on failure, telling the controller to kill it and spool up a new one.

## Replicable

Because of this setup, it also means pods are the replicable elements.
This basically comes down to Kubernetes being able to automatically create replicas of the system running on the pod.

With this system in place, we can scale horizontally when our load gets higher or have 99% uptime due to replicas on different data sets.

Keep in mind this is solely possible due to the single responsibility of one pod. If this were not the case, it would become impossible to scale them across the board.

## Creating pods

I want to note that you'll never have to create pods manually. This is all managed by the controller.

By doing this, Kubernetes can use resources to their fullest by only spooling up the pods we actively need and managing their workload across different nodes.

A side note is that you can manually create them, but unless things go south, I strongly advise against this.

## Conclusion

Pods are the smallest entity in Kubernetes. Your containers are deployed on nodes.

Pods are managed by the controller and are treated as single-task things. Meaning they are cheap, easy, and stateless.
By doing this, Kubernetes can spool them up quickly and destroy them as it sees fit.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
