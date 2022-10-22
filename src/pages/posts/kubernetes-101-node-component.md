---
layout: ../../layouts/Post.astro
title: 'Kubernetes 101 - Node component'
metaTitle: 'Kubernetes 101 - Node component'
metaDesc: "What's in the node component and what can it do for us?"
ogImage: /images/31-10-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/77d26101-6af4-44f9-6c62-354d80ec4a00
date: 2022-10-31T03:00:00.000Z
tags:
  - kubernetes
---

We'll check out the node component in more detail for this article.

The node component is a component that runs on every node, and it's responsible for maintaining running pods and providing the Kubernetes runtime environment.

It closely connects with the Kubernetes API and receives and sends data from its node.

Each node runs two main components a kubelet and a container runtime. Let's take a look at what each one does.

### kubelet

The kubelet is responsible for establishing and acting on the communication between the Control Plane and the node.

### Container runtime

The container runtime is in charge of pulling the relevant image from the image registry, unpacking them, and running them on the node.
It can run multiple container runtimes, including Docker, CRI, CRI-O, and Containerd.

### kube-proxy

Besides the two main components, we also get the kube-proxy which runs on each node. It's responsible for maintaining network rules on each node. It makes sure the communication between nodes and pods is as expected.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
