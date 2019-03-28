+++
draft = false
weight = 30
description = "Configures network access to an app"
title = "Service"

doclink = "service-v1-core"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;
    classDef net fill:#EBEBEB,stroke:#414141,stroke-width:1px;
    
    pod[Pod]--is exposed by-->svc[Service]

    svc-.configures.->lb(LoadBalancer)
    svc-.configures.->np(NodePort)
    svc-.configures.->cip(ClusterIP)
    lb-.direct traffic to.->pod
    np-.direct traffic to.->pod
    cip-.direct traffic to.->pod

    class svc highlight
    class lb,np,cip net

{{< /mermaid >}}

Service is an abstraction layer that configures underlying network infrastructure to provide an access to ports exposed by a [Pod]({{< ref "pod" >}}).

There are four types of Service:

* **ClusterIP** - basic and default type which provides an fixed, virtual address (accesible **ONLY** from inside a cluster) and DNS name if dns addon is installed 
* **NodePort** - configures the same things as ClusterIP and additionally opens a dedicated port on **every** node in a cluster; this port directs traffic to any available and ready pod regardless which node it is running on
* **LoadBalancer** - configures the same things as NodePort and additionally it creates a load balancer service on a platform that a cluster is running on; useful mostly on cloud platforms
* **ExternalName** - only adds a record in internal , cluster DNS server 


