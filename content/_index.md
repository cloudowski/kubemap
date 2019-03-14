+++
title = "Kubernetes Objects Map"
description = ""
weight = 20
draft = false
bref = ""
toc = false
aliases = [
    "/map"
]
url = "/"
+++

<div id="action-buttons">
    <a class="button outline big" href="https://github.com/cloudowski/kubemap">View on Github</a>
  </div>


  <h2 itemprop="headline"> What is it?</h2>
  <div id="post">
    Kubemap presents Kubernetes objects (or resources if you prefer) with relationships
    and connections between them.
    This may help people who learn better with diagrams and maps to understand how they interact with each other.
  </div>

  <h2 itemprop="headline"> How to use it?</h2>
  <div id="post">
    You may want to use zoom in your browser, as currently the map does not support zooming itself. Some objects have additional data as tooltips (just hover over them to see more info) or links to a page with more details.
  </div>

{{<mermaid>}}
graph BT;
    
    linkStyle default interpolate basis
    classDef default stroke-width:2px,font-size:22px;


    container["Container(s)"]--run inside-->pod[Pod]
    click container callback "One or more containers"

    pod--is scaled by-->rs[ReplicaSet]
    click pod "{{< ref "/object/pod" >}}" "Click for details"

    click rs callback "A simple controller that just runs multiple replicas from a pod definition"

    pod--is scaled by-->rc[ReplicationController]
    click rc callback "A simple controller that just runs multiple replicas from a pod definition. LEGACY and it's been replaced by ReplicaSet."

    pod--runs in an orderly fashion-->statefulset[StatefulSet]
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
