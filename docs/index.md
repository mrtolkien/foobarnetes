# Introduction

Do you want to **learn** how to setup your own Kubernetes cluster and drive its state through a git repository? You've come to the right place!

We'll go step by step, from hardware considerations to setting up validation and linting on each Pull Request (PR) to your repository.

## Motivation

Kubernetes are a great tool, but learning how to use them can be daunting. Furthermore, there are now multiple services and apps that have become ubiquitous and that you are expected to know and use.

As I was lost myself when trying to build a git-driven Kubernetes cluster at home, I thought that writing down every step could help future users.

## Structure

<!-- TODO: Link that to the right pages and navigation -->
- Workstation preparation
- Host preparation
    - Hardware considerations
    - OS considerations
- Installing Kubernetes
- Setting up Helm
- Setting up Gitops
- Setting up your first apps
- Adding nodes
- Adding apps

## Thanks

This repository is pretty much a written-out version of the [k8s-at-home flux cluster template repository](https://github.com/k8s-at-home/flux-cluster-template/).

The template automates most of the process, but at the cost of comprehension.
