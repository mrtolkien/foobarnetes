# Host operating system

## Fedora Server

[Fedora Server](https://getfedora.org/en/server/) is a perfect fit for Kubernetes clusters. While it uses newer packages than Debian distros and is known to be cutting-edge, it is also a highly tested and reliable distribution. It includes all necessary containerization tools by default, and this makes setting up new nodes a breeze.

## Running the OS

### Bare metal or VM

This guide assumes you will be installing Fedora Server either:

- Directly on a physical server with a bare metal install
- In a virtual machine (VM) managed by an hypervisor like [Proxmox VE](https://www.proxmox.com/en/proxmox-ve)

Those installs are by far the easiest way to handle Kubernetes nodes. If you're RAM-limited with low-end machines a bare metal will let you squeeze the most performance out of it. If you have some RAM to spare the performance overhead of VMs is very small with modern type 2 hypervisors and lets you split up your workloads more easily.

### Containers

While it is possible to run Kubernetes in a container with LXC or Docker, it is very painful and adds a ton of complexity to the setup. Without direct access to the kernel, Kubernetes cannot control networking as directly as it needs.

It *is* doable and I might make a write-up on running Fedora Server in an LXC in the future, but it is not a high priority right now as it would require its own full chapter.
