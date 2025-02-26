---
title: Home
---

# `KWOK` (`K`ubernetes `W`ith`O`ut `K`ubelet)

<img align="right" width="180px" src="/favicon.svg">

[KWOK] is pronounced as `/kwɔk/`.

[KWOK] is a toolkit that enables setting up a cluster of thousands of Nodes in seconds.
Under the scene, all Nodes are simulated to behave like real ones, so the overall approach employs
a pretty low resource footprint that you can easily play around on your laptop.

## What is KWOK?

KWOK stands for Kubernetes WithOut Kubelet. So far, it provides two tools:

- `kwok` is the cornerstone of this project, responsible for simulating the lifecycle of fake nodes, pods, and other Kubernetes API resources.
- `kwokctl` is a CLI tool designed to streamline the creation and management of clusters, with nodes simulated by `kwok`.

### What's the difference with `kubemark`

[kubemark] is a kubelet that does not actually run a container. Its behavior is exactly the same as kubelet,
which means that simulating a large number of nodes and pods requires a lot of memory.

`kwok`, however, simply simulates the behavior of the node. As a result, it can simulate a large number of nodes and pods using very little memory.

### What's the difference with `kind`

[kind] runs Kubernetes in Docker, creating a real cluster.

`kwokctl` can be used as an alternative to [kind] in some scenarios where you don’t need to actually run any pod.

## Why KWOK?

- Lightweight: You can [simulate thousands of nodes] on your laptop without significant consumption of CPU or memory resources.
Currently, KWOK can reliably maintain 1k nodes and 100k pods easily.
- Fast: You can create and delete clusters and nodes almost instantly, without waiting for boot or provisioning.
Currently, KWOK can create 20 nodes or pods per second.
- Compatibility: KWOK works with any tools or clients that are compliant with Kubernetes APIs, such as kubectl, helm, kui, etc.
- Portability: KWOK has no specific hardware or software requirements. You can [run it using pre-built images], once Docker/Podman/Nerdctl is installed. Alternatively, binaries are also available for all platforms and can be easily installed.
- Flexibility: You can configure different node types, labels, taints, capacities, conditions, etc., and you can configure different pod behaviors, status, etc. to test different scenarios and edge cases.

## Getting Started

The animation below shows a test process to work with the latest version of `kwok`/`kwokctl`.

<img width="700px" src="/img/demo/manage-clusters.svg">

Welcome to [get started][user guide] with the installation, basic usage, custom configuration,
and [contribution to KWOK][contributor guide].

## `kwokctl` Runtime Support Matrix

Runtime indicates which medium `kwokctl` will use to start the cluster

|    OS/Arch    | binary | docker | podman | nerdctl | kind  | kind-podman |
|:-------------:|:------:|:------:|:------:|:-------:|:-----:|:-----------:|
|  linux/amd64  |   🟢   |   🟢   |   🟢   |   🟢    |  🟢   |     🟢      |
|  linux/arm64  |   🔵   |   🔵   |   🟣   |   🟣    |  🟣   |     🟣      |
| darwin/amd64  | 🟢/🟠  |   🟢   |   🔵   |  🔵/🟡  |  🟢   |     🔵      |
| darwin/arm64  | 🔵/🟠  |   🔵   |   🔵   |  🔵/🟡  |  🔵   |     🔵      |
| windows/amd64 | 🟣/🟠  |   🟣   |   🟤   |  🟤/🟡  |  🟤   |     🟤      |
| windows/arm64 | 🟣/🟠  |   🟣   |   🔴   |   🔴    |  🔴   |     🔴      |

- 🟢 Supported and test covered by CI
- 🔵 Supported and test by manually
- 🟣 Supported but not test yet (need help to verify)
- 🟤 Unsupported but should work in theory (need help to verify)
- 🔴 Unsupported and will not work
- 🟠 Need to build [platform-specific Kubernetes binaries]
- 🟡 Need to do some workaround to make it work

## Community

See our own [contributor guide] and the Kubernetes [community page].

### Getting Involved

If you're interested in participating in future discussions or development related to KWOK, there are several ways to get involved:

- Slack: [#kwok] for general usage discussion, [#kwok-dev] for development discussion. (visit [slack.k8s.io] for a workspace invitation)
- Open Issues/PRs/Discussions in [sigs.k8s.io/kwok]

### Code of conduct

Participation in the Kubernetes community is governed by the [Kubernetes Code of Conduct][code of conduct].

[KWOK]: https://sigs.k8s.io/kwok
[kind]: https://github.com/kubernetes-sigs/kind
[kubemark]: https://github.com/kubernetes/kubernetes/tree/master/test/kubemark
[community page]: https://kubernetes.io/community/
[user guide]: {{< relref "/docs/user" >}}
[contributor guide]: {{< relref "/docs/contributing" >}}
[code of conduct]: https://github.com/kubernetes-sigs/kwok/blob/main/code-of-conduct.md
[sigs.k8s.io/kwok]: https://sigs.k8s.io/kwok/
[#kwok]: https://kubernetes.slack.com/messages/kwok/
[#kwok-dev]: https://kubernetes.slack.com/messages/kwok-dev/
[slack.k8s.io]: https://slack.k8s.io/
[run it using pre-built images]: {{< relref "/docs/user/all-in-one-image" >}}
[simulate thousands of nodes]: {{< relref "/docs/user/kwok-manage-nodes-and-pods" >}}
[platform-specific Kubernetes binaries]: {{< relref "/docs/user/kwokctl-platform-specific-binaries" >}}
