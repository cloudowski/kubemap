+++
draft = false
weight = 190
description = "Represents a named volume in a Pod"
title = "Volume"

doclink = "volume-v1-core"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;
    vol[Volume]-->pod[Pod]
    class vol highlight

{{< /mermaid >}}

Volumes are used to provide different kind of data to containers defined in a [pod]({{< ref "pod" >}}).

### Volume types

There are a couple of types of volumes:

* **configuration** - Secret and ConfigMap are such objects; they contain configuration data stored in Kubernetes store and are provided to containers as directories with files, single files or environment variables passed to containers; usually they are read-only
* **data** - standard volumes mounted inside containers to provide a place for reading a writing data
* **interface** - abstraction layers to hide complexity and implementation details from a user (e.g. csi, persistentVolumeClaim, flexVolume)