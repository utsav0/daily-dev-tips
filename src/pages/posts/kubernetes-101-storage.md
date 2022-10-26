---
layout: ../../layouts/Post.astro
title: 'Kubernetes 101 - Storage'
metaTitle: 'Kubernetes 101 - Storage'
metaDesc: 'What are the storage options in Kubernetes and how do they work'
ogImage: /images/04-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/83418507-ff93-4b7b-17db-1325467a6b00
date: 2022-11-04T03:00:00.000Z
tags:
  - kubernetes
---

Another essential aspect of Kubernetes is storage. In some instances, you will want to use some kind of storage solution.

Because our pods can re-spool, die and recreate on the fly, we can't rely on storing elements on them.

In many cases, we want some data stored but stay there and make that data accessible across multiple pods.

Kubernetes has quite a wide variety of storage options. Let's take a closer look at them.

## Volumes

Volumes are the basic storage entities in Kubernetes. It can provide all types of storage depending on your cloud provider and needs. Access to these storage volumes can be achieved through persistent volumes.

For example, the Azure cloud will have its implementation, as does Google and AWS.

## CSI - Container Storage Interface

This interface is used to store containers. It's a plugin making it easier for us to manage storage containers.

## Non-Persistent Storage

This is the default storage option for Kubernetes, consisting of non-persistent temporary storage. As long as the container keeps living, it will be there, but as soon as it dies and shuts down, it gets wiped.

## Persistent volumes

For persistent volumes, we have two important concepts to understand.

### Persistent Volume (PV)

This is a storage element in a cluster, defined manually or by a storage class (A way to define the type of volumes). A PV storage has its lifecycle separate from your other pods and implements its layer to communicate to your desired storage.

### Persistent Volume Claim (PVC)

This is a user's storage request. An application can request a specific type of storage, for example, how to interact with the data. Or how big the storage should be and the level of performance.
These claims are independent of your underlying implementation (so vendor-independent).

## Conclusion

Storage within Kubernetes is very vast and dynamic.
We are independent of our end storage solution and can wrap around these implementations.

This gives us a lot of flexibility and freedom.
Besides this freedom, we also get various storage options depending on our needs.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
