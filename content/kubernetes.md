+++
title = "Kubernetes Object Map"
description = ""
weight = 20
draft = false
type = "graph"
bref = ""
toc = false
aliases = [
    "/map"
]
url = "/"
image = 
+++

{{<mermaid>}}
graph BT;
    
    linkStyle default interpolate basis
    classDef default stroke:#333,stroke-width:2px,font-size:22px,padding:8px;


    container["Container(s)"]--run inside-->pod[Pod]
    click container callback "One or more containers"

    pod--is scaled by-->rs[ReplicaSet]
    click pod callback "This is a pod. It is a building block for all other workloads inside Kubernetes."
    click rs callback "A simple controller that just runs multiple replicas from a pod defintion"

    pod--is scaled by-->rc[ReplicationController]
    click rc callback "A simple controller that just runs multiple replicas from a pod defintion. LEGACY and it's been replaced by ReplicaSet."

    pod--runs in an order-->statefulset[StatefulSet]
    click statefulset callback "Runs a set of pods with IP and DNS names set in ordinal fashion. Used by cluster-type workloads."

    pod--runs on every node by-->ds[DaemonSet]
    click ds callback "Runs a single pod on every node in a cluster."

    rs--enables updates-->deployment[Deployment]
    click deployment callback "Manage applications lifecycle through mulitple ReplicaSets.
    "
    pod-->job[Job]

    pod-->cronjob[CronJob]
    pod--is scaled automatically by-->hpa[HorizontalPodAutoscaler]


    pod--is exposed by-->svc[Service]
    ep[Endpoints]--registers active IP:PORT pairs-->svc
    svc--provides info for proxy config-->ing[Ingress]
    
    pv[PersistentVolume]-.satisfies.->pvc
    pvc[PersistentVolumeClaim]--provides persistent storage-->volumes

    sc[StorageClass]-.dynamically provisions.->pv
    pv--may belongs to single-->sc
    configmap--exposes as env variables-->pod
    configmap--exposes as files-->volumes
    secret--exposes as env variables-->pod
    secret--exposes as files-->volumes
    volumes--mounts data inside as files or dirs-->pod[Pod]

{{< /mermaid >}}
