+++
draft = false
weight = 200
description = "A request for persistent storage"
title = "PersistentVolumeClaim"

doclink = "persistentvolumeclaim-v1-core"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;

    pv[PersistentVolume]--binds-->pvc
    pvc[PersistentVolumeClaim]--provides persistent storage-->vol[Volume]
    
    class pvc highlight 
{{< /mermaid >}}


PersistentVolumeClaim defines **"WHAT"** kind of persistent storage is needed by a Pod. It describes it with only a few parameters such as size, access mode (single/multi, ro/rw) and optionally group ([StorageClass]({{< ref "storageclass" >}})) that it belongs to.