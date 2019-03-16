+++
draft = false
weight = 20
description = "A building block for other workloads"
title = "Pod"

doclink = "pod-v1-core"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;
    container["Container(s)"]-->pod[Pod]
    click pod "{{< ref "/objects/pod" >}}" "Click for details"
    class pod highlight

{{< /mermaid >}}

Pod runs one or more containers. Those containers share the same network namespace and this have the same IP address. These containers also run **always** on the same host.
