---
layout: ../../layouts/Post.astro
title: 'Kubernetes 101 - Containers'
metaTitle: 'Kubernetes 101 - Containers'
metaDesc: 'What exactly are containers and how do they work?'
ogImage: /images/02-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/4aeac8f3-c3f9-4432-9d40-d4c2c45be400
date: 2022-11-02T03:00:00.000Z
tags:
  - kubernetes
---

For this article we'll be looking a bit more in detail into containers. Containers are ready to run software packages, meaning they include everything:

- code
- runtime if required
- application
- system libraries

Once something is converted into a container the code cannot change, if you need to update any of the above mentioned elements you'll need to create a new image version.

The benefit of these images containing everything out of the box is that the can easily run on different OS environments and clouds.

## Container images

As for the container images it references a bundles application that you can run on a given pod.

So where do these images live?

By default Kubernetes will look in the Docker registry for your images based on it's name.
However it's possible to use other registries as well as private hosted ones.

We won't go into too much detail around this for now.

The main thing here is to know that at some point we'll have to convert our code into a image and push it somewhere.

## Container hooks

Hooks are not a new concept, but something worth mentioning.
Our containers come with some hooks exposed, there are two exposed ones:

- `PostStart`: Executed immediately after creation of the container.
- `PreStop`: Called before the container is terminated due to unhealthiness of controller decided to kill it off. It's important to note the container will always be killed, it won't wait for some calls to happen in this hook.

For our beginning exploration of Kubernetes we won't use these hooks just yet, so let's dive into them at a later stage again.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
