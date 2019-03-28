+++
draft = false
weight = 10
description = "An isolated process running on a node inside a cluster"
title = "Container"

doclink = "container-v1-core"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;
    container["Container(s)"]-->pod[Pod]
    class container highlight

{{< /mermaid >}}

Container does all the work defined in a [pod]({{< ref "pod" >}}) definition.

### Types

There are a couple of container <i>types</i>:

* <strong>main container</strong> - runs a main application/service
* <strong>init container</strong> - runs _before_ main container and performs some initalization tasks 
* <strong>sidecar container</strong> - runs alongside application/service container; it cooperates in serving requests or sometimes acts as a proxy (e.g. used by [istio](https://istio.io) project)

