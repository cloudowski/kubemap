+++
draft = false
weight = 190
description = "Runs multiple instances of Pod"
title = "ReplicaSet"

doclink = "replicaset-v1-apps"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;
    pod[Pod]--is scaled by-->rs[ReplicaSet]

    class rs highlight

{{< /mermaid >}}

ReplicaSet is a very simple object that has only **ONE** task - to run a defined number of replicas defines as [pod]({{< ref "pod" >}}) templates. It keeps them alive by launching new ones in case of failure (node crash, pod unresponsive etc.). 