+++
draft = false
weight = 200
description = "Keeps ip:port pairs of pods for defined service"
title = "Endpoints"

doclink = "endpoints-v1-core"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;
    
    ep[Endpoints]--keeps ip:port pairs-->svc[Service]

    class ep highlight

{{< /mermaid >}}

Endpoints object keeps all **ip:port** pairs of [Pods]({{< ref "pod" >}}) serving requests defined by a selector in a [Service]({{< ref "service" >}}).
