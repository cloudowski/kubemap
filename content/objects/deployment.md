+++
draft = false
weight = 170
description = "Manages application lifecycle"
title = "Deployment"

doclink = "deployment-v1-apps"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;
    rs[ReplicaSet]--enables app declarative updates-->deployment[Deployment]
    deployment-.manages.->rs

    class deployment highlight

{{< /mermaid >}}

<div class="message focus" data-component="message">
    <span class="close small"></span>
    For standard applications <b>Deployment</b> object is best and recommended way to launch them. It is advised NOT to use <b>ReplicaSet</b> objects and definitely not <b>Pod</b> directly.
</div>

Deployment object manages application updates by creating revisions with  [ReplicaSet]({{< ref "replicaset" >}}) objects.

Currently it support two update strategies:

* **RollingUpdate** (default) - gradaully increase number of replicas with new version and decreases old instances until all all of them are running the latest, desired version
* **Recreate** - all *old* instances (pods) are killed before new ones are created
