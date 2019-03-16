+++
draft = false
weight = 190
description = "Stores configuration data"
title = "ConfigMap"

doclink = "configmap-v1-core"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;

    cm[ConfigMap]--env variables-->pod
    cm-->vol
    vol[Volume]--files-->pod[Pod]
    
    class cm highlight 
{{< /mermaid >}}

ConfigMap is a *sibling* of [Secret]({{< ref "secret" >}}). It is a general purpose object for storing configuration, **non-confidential** data for [containers]({{< ref "container" >}}) and providing them as files mounted inside them using [volumes]({{< ref "volume" >}}) or environment variables passed directly to them. 
