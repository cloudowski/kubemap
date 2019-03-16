+++
draft = false
weight = 200
description = "Groups and defines parameters for persistent volumes"
title = "StorageClass"

doclink = "storageclass-v1-storage-k8s-io"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;

    pv--may belongs to single-->sc
    sc[StorageClass]-.dynamically provisions.->pv
    
    class sc highlight 
{{< /mermaid >}}

StorageClass has two functions:

1. For static [PersistentVolumes]({{< ref "persistentvolume" >}}) (those created by cluster administrator) it groups and thus enabling fine-grained assignment in [PersistentVolumeClaims]({{< ref "persistentvolumeclaim" >}}) definitions.
2. For dynamic mode it creates PersistentVolume automatically with defined provisioner (e.g. EBS volume on AWS). It also assign each created PersistentVolume a `storageClassName` parameter. 