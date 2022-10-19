---
layout: ../../layouts/Post.astro
title: 'Kubernetes 101 - Introduction'
metaTitle: 'Kubernetes 101 - Introduction'
metaDesc: 'What exactly is Kubernetes and what can it do for us?'
ogImage: /images/28-10-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/114d2158-0a00-4473-bd06-68f54c4c2800
date: 2022-10-28T03:00:00.000Z
tags:
  - kubernetes
---

Although I'm not a DevOps guy, I wanted to learn more about this engineering.
It's an area I always semi-understood but never took the time to explore beyond that.
Kubernetes was available to me as an engineer, and it worked without knowing why half the time.

So I decided it was time to explore it more in detail.
And what better way to do so than to write some articles about it?

In an upcoming couple of articles, we'll be deep diving into Kubernetes, what it is, what each component is, and even how we can set it up.

## Introduction

This article, in particular, is a broader high-level overview of what it is.

As I'm sure, many of you, like me, have only a vague idea of it.

> Note: I'm still no professional, so if you make any mistakes you spot, please feel free to contact me or change it directly on this page (via GitHub).

The description given by Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services. It facilitates both declarative configuration and automation.

So, it's a perfect way to manage containerized deployment as a uniform standard.

You might also hear the name K8S, which is the same as Kubernetes. (It comes from the eight letters between the K and the S).

Google originally developed the system, and they open-sourced it back in 2014 [you can read a good background story here](https://kubernetes.io/blog/2015/04/borg-predecessor-to-kubernetes/).

## Why do we need this?

First, we must keep in mind that we are talking about containerized deployments.

You might be familiar with traditional deployment. This is when we get a physical server and deploy the code on that server we own.
The problem with this was scalability and maintainability.
As you can imagine, it was tough to maintain it when more resources were needed, or a machine failed over time.

The follow-up to this was virtual deployments. It allows one to run multiple virtual machines on one physical server's CPU. This meant we could more easily scale them and move them to another physical server.

As for containerized deployments, it's very close to virtual, but with one big difference. They share the OS between the applications. The big benefit is that they become decoupled from the infrastructure and can run across multiple clouds and OS distributions.

## So, where does Kubernetes come into play?

You want to ensure your application is always up and running in production environments. This means one container might go down at a given stage. You want to ensure there's always a backup container up and running, so the application has no downtime.

But can you imagine having to set this up yourself and manage each system yourself? This will become a nightmare.

Thus, Kubernetes can help you orchestrate this more easily. It provides a framework to run systems and takes care of scaling and failovers. It also comes with deployment patterns and so on.

So highlights of what Kubernetes gives us:

- Service discovery and load balancing: Kubernetes can expose containers using DNS name, so if traffic is high, Kubernetes can load balance your traffic to several containers to ensure the app is stable.
- Rollouts and rollbacks: You can state how you want your system to be deployed, which means you should first set up the new deployment and only then retire the old one, or you can pick another strategy. Besides this, you can opt to describe a rollback scenario.
- Bin packing: We can provide Kubernetes with a cluster of nodes and tell it how much CPU and memory each container needs. Kubernetes can fit containers on these nodes and help us use our resources in the best possible fashion.
- Self-healing: Kubernetes can take care of restarting containers that fail or even deprecate them and spool up new ones.
- Config management: It also provides a way to manage and store secrets and config to safely inject your stack without ever exposing it.

And that's it, atleast on a super high level.
If you liked this article, subscribe to the newsletter, as we will dive into more Kubernetes details soon.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
