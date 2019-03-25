+++
draft = false
weight = 170
description = "Manages stateful apps"
title = "StatefulSet"

doclink = "statefulset-v1-apps"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;

    pod[Pod]--runs in an orderly fashion-->statefulset[StatefulSet]

    class statefulset highlight

{{< /mermaid >}}

StatefulSets are designed to run services which require predictable hostnames and IP addresses that don't change when [Pod]({{< ref "pod" >}}) is moved/deleted/recreated. All pods running in a StatefulSet **require** a storage which is defined by [PersistentVolumeClaim]({{< ref "persistentvolumeclaim" >}}) objects.

Most database clusters and other services which create some kind of group of instances to provide redundancy, high-availability and greater performance, work in StatefulSet.