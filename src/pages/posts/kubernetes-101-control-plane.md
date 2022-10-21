---
layout: ../../layouts/Post.astro
title: 'Kubernetes 101 - Control Plane'
metaTitle: 'Kubernetes 101 - Control Plane'
metaDesc: 'A closer look at the Kubernetes control plane and what it can do'
ogImage: /images/30-10-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/b85f3d39-8025-4405-53e3-5fd6ad1a5d00
date: 2022-10-30T03:00:00.000Z
tags:
  - kubernetes
---

As mentioned in the previous article, on one side of Kubernetes, we get something called the control plane.

This is the control system that can make decisions about the cluster. For example, ensuring enough pods are online at all times and routing traffic correctly.

## What is the control plane

The control plane is really like the brains of the operation. It includes several components that control your cluster, manage data, state data, and configuration.

It's also solely responsible for ensuring the cluster works the way you want it to, which you defined declaratively (more on that later).

Let's take a closer look at the components inside the control plane.

### kube-apiserver

The API server is one of the components inside the control plane, and it exposes the Kubernetes API.
This API server is the front end of the Kubernetes control plane.

It's responsible for all external and internal requests.
The API server is also designed to scale horizontally, meaning you can spool up multiple instances and communicate between them.

### kube-scheduler

This particular component is used for scheduling pods onto specific nodes according to your needs and resources.
It can determine the best place to put a pod based on multiple requirements.

### kube-controller-manager

The controller is a component that handles all the controller processes, of which we have multiple combined in this one.

Some of these types are:

- Node controller: Ensuring the nodes are up and acting on failing nodes.
- Job controller: Watches for once-off jobs, creates a pod to run the job, and fails them once they're done.
- Namespace controller: Handle all the namespace-specific actions to act on.

And so on, there is a bigger list. Let's go into detail in another article.

The controller manager, it's the overseer of all the individual controllers.

### etcd

This consists of a key-value database used by Kubernetes to store information about your cluster state and config.

### cloud-controller-manager

This particular element contains cloud-specific logic. It lets you link the uniform Kubernetes and each cloud provider's specific needs.

It's important to note this component only exists when running your service on a cloud provider. Locally there is no need for one.

As with the kube-controller-manager, the cloud controller is split into multiple individual controllers depending on the cloud provider's offer.

## Conclusion

The Control Plane is the brains of the operation and can interact between all the resources and systems our cluster needs.

It provides multiple individual components that all serve their purposes.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
