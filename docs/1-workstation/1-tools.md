# Tools

[Original list](https://github.com/k8s-at-home/flux-cluster-template/#-workstation-tools)

## Kubectl, Kustomize, and Helm

[`kubectl`](https://kubernetes.io/docs/reference/kubectl/kubectl/) (kube control) is the CLI used to interact with Kubernetes clusters.

[Kustomize](https://github.com/kubernetes-sigs/kustomize) is a tool to easily deploy resources for Kubernetes. Its CLI helps create kustomization files and build them for use with `kubectl`.

[Helm](https://helm.sh/) is a "package manager" for Kubernetes and heavily used to describe deployments configurations.

```shell
brew install kubectl-cli kustomize helm
```

## Age + SOPS

[Age](https://github.com/FiloSottile/age) is a simple and modern encryption tool. We will use it to generate a key and encrypt the secrets in our repository.

[Mozilla SOPS](https://github.com/mozilla/sops) is a flexible tool for managing secrets and will be working hand-in-hand with age.

```shell
brew install age
brew install sops
```

## Git and Flux CLI

[`git`](https://git-scm.com/) is the most widespread source-control management software and it will be how we manage our cluster's state.

[Flux](https://fluxcd.io/docs/) is the tool that will directly interact with our cluster. It will read from our `git` repository to make sure our cluster always reflects its state. Its CLI will allow us to quickly check its status.

```shell
brew install git fluxcd/tap/flux
```

## Pre-commit

[`pre-commit`](https://github.com/pre-commit/pre-commit) handles pre-commit hooks and makes sure we're not doing any mistakes without our repository like committing secrets or poorly formatted `.yaml` files.

```shell
brew install pre-commit
```

## Optional tools

### K9S

[K9S](https://github.com/derailed/k9s) is a great CLI management interface.

```shell
brew install k9s
```
