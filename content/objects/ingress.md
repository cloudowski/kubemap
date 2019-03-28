+++
draft = false
weight = 200
description = "Interface for a reverse proxy"
title = "Ingress"

doclink = "ingress-v1beta1-extensions"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;
    
    svc[Service]--provides info-->ing[Ingress]
    ep[Endpoints]-.provide ip:port pair.->ing

    class ing highlight

{{< /mermaid >}}

Ingress is an **interface** that is implemented by many providers. They implement this simple interface to provide automatically configurable reverse proxy for http applications running in containers in [Pods]({{< ref "pod" >}}). Information about endpoints is retrieved through a [Service]({{< ref "service" >}}) (records are taken directly from matching [Endpoints]({{< ref "service" >}}) object).
 