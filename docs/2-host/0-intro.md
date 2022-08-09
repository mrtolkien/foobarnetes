# Host introduction

## Glossary

Before starting, I recommend reading the [Kubernetes Components](https://kubernetes.io/docs/concepts/overview/components/) article on the official Kubernetes website.

## Hosts

Hosts are the machines that will be running **nodes** in your Kubernetes cluster.

You can make a kubernetes cluster out of a **single node**, where it will be both a control plane node and a worker node. This is done through [removing its tainting](https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/#concepts).

But even a single physical machine you can create two virtual machines to have a proper control plane node and a worker node, which lets you stay within "standard" Kubernetes setups and allows for easier migration later.
