+++
draft = false
weight = 190
description = "Runs a single Pod on every node in a cluster"
title = "DaemonSet"

doclink = "daemonset-v1-apps"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;
    pod[Pod]--is scaled by-->ds[DaemonSet]

    class ds highlight

{{< /mermaid >}}

DaemonSet is responsible of running a **single** instance of a defined [pod]({{< ref "pod" >}}) on **every** node in Kubernetes cluster.