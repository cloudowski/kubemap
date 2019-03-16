+++
draft = false
weight = 190
description = "Holds a confidential data"
title = "Secret"

doclink = "secret-v1-core"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;

    secret[Secret]--env variables-->pod
    secret-->vol
    vol[Volume]--files-->pod[Pod]
    
    class secret highlight 
{{< /mermaid >}}

Secrets are **base64** encoded (**NOT** encrypted) values that are designed to provide confidential data for [containers]({{< ref "container" >}}) as files mounted inside them using [volumes]({{< ref "volume" >}}) or environment variables passed directly to them.

It is very similar to [ConfigMap]({{< ref "configmap" >}}) object.

<!-- ### Secret types -->

<!-- There are a couple of types specified with <code>.spec.type</code> field:

* **Opaque** - Regular secret that can store any kind of data
* **TLS** - Stores a pair of TLS certificate and key -->
