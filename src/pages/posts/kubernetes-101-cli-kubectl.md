---
layout: ../../layouts/Post.astro
title: 'Kubernetes 101 - CLI kubectl'
metaTitle: 'Kubernetes 101 - CLI kubectl'
metaDesc: 'How to install and use the kubectl CLI'
ogImage: /images/06-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/92b47588-6c8b-44f8-f5f0-d9d6de627200
date: 2022-11-06T03:00:00.000Z
tags:
  - kubernetes
---

Yesterday we set up our [Kubernetes dashboard](https://daily-dev-tips.com/posts/kubernetes-101-kubernetes-dashboard/) and used something called `kubectl`. This is a command line interface for communicating with the Kubernetes control plane.

In the article, we didn't go into detail on how to install and use it, so that this article will help you with that.

## Installing kubectl

We can run either of the following commands to install the tool.

```bash
# MacOS (Homebrew)
brew install kubectl

# MacOs (Curl - Intel)
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/amd64/kubectl"=

# MacOs (Curl - Silicon)
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/arm64/kubectl"

# Windows
curl.exe -LO "https://dl.k8s.io/release/v1.25.0/bin/windows/amd64/kubectl.exe"
```

To verify your installation is correct, run the following command.

```bash
kubectl cluster-info
```

It outputs if the cluster is running and you're connected to it.

## The command syntax

Before diving into the commands, let's look at the basic command syntax for `kubectl`.

A typical command is structured like this:

```bash
kubectl [command] [type] [name] [flags]
```

Where the following mean:

- `command`: Describes the operation we are executing. Examples are `create`, `get`, and `delete`.
- `type`: Describes the type of resource we are trying to interact with, examples being `pods`, `namespaces`, and `deployments`.
- `name`: Describes a particular name of a resource. If you omit this, your command will execute on all target resource types.
- `flags`: Describes unique options for the command. These vary per command.

## Useful commands

`kubectl` can do many amazing things, but let's look at some of the most valuable commands you want to know.

The first ones are around resources, as often we want to see which resources exist.

```bash
# List all services in the namespace
kubectl get services
# List all pods in all namespaces
kubectl get pods --all-namespaces
# List all pods in the current namespace with more details
kubectl get pods -o wide
# List all pods in the namespace
kubectl get pods
# Get a pod's YAML
kubectl get pod my-pod -o yaml
```

Then in some cases, you might want to delete resources.

```bash
# Delete a pod using the type and name specified in pod.json
kubectl delete -f ./pod.json
# Delete a pod with no grace period
kubectl delete pod unwanted --now
# Delete pods and services with the same names, "baz" and "foo"
kubectl delete pod, service baz foo
# Delete all pods and services in namespace my-ns
kubectl -n my-ns delete pod,svc --all
```

It's often also super handy to get some logs for a running pod. This can help you debug if it's stuck in some loop, for instance.

```bash
# dump pod logs (stdout)
kubectl logs my-pod
# dump pod logs, with label name=myLabel (stdout)
kubectl logs -l name=myLabel
# stream pod logs (stdout)
kubectl logs -f my-pod
```

Another helpful element is being able to set up new configurations and resources. Kubernetes uses the apply command for this, and we can apply specific yaml files like this.

```bash
# create resource(s)
kubectl apply -f ./my-manifest.yaml
# create from multiple files
kubectl apply -f ./my1.yaml -f ./my2.yaml
```

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
