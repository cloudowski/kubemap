+++
draft = false
weight = 190
description = "Runs multiple instances of Pod"
title = "ReplicationController"

doclink = "replicationcontroller-v1-core"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;
    pod[Pod]--is scaled by-->rc[ReplicationController]

    class rc highlight

{{< /mermaid >}}

<div class="message warning" data-component="message">
    <span class="close small"></span>
    <h5>Warning</h5>
    ReplicationController is considered as deprecated and it is recommended to use its successor - <a href="{{< ref "replicaset" >}}">ReplicaSet</a>
</div>

ReplicationController job is to run a defined number of replicas defines as [pod]({{< ref "pod" >}}) templates. It keeps them alive by launching new ones in case of failure (node crash, pod unresponsive etc.). 