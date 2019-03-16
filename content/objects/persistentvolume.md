+++
draft = false
weight = 200
description = "Represents physical volume for data"
title = "PersistentVolume"

doclink = "persistentvolume-v1-core"

+++

{{<genmap>}}
{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;
    classDef grey fill:#EBEBEB,stroke:#141B41,stroke-width:2px;

    pv--may belongs to single-->sc
    sc[StorageClass]-.dynamically provisions.->pv
    physical((Physical Data))-.->pv
    
    class pv highlight
    class physical grey 
{{< /mermaid >}}

PersistentVolume represents a physical volume - it has all the necessary parameters to connect underlying physical storage as [volume]({{< ref "volume" >}}) (using [PVC]({{< ref "persistentvolumeclaim" >}})) to a [pod]({{< ref "pod" >}}). It defines **"HOW"** to access a physical storage.

PersistentVolumes can be created in two ways

* **Statically** by cluster administrator with API request containing physical volume characteristics
* **Dynamically** by [StorageClass]({{< ref "storageclass" >}}) and a provisioner defined there
