+++
draft = false
weight = 200
description = "Run a task until successful completion"
title = "Job"

doclink = "job-v1-batch"

+++

{{<mermaid>}}

graph BT;
    classDef highlight fill:#AFFC41,stroke:#141B41,stroke-width:2px;
    
    pod[Pod]--execute a task-->job[Job]

    class job highlight

{{< /mermaid >}}

Job is a simple objects that ensures that specified task completes successfully. It is very similar to a [CronJob]({{< ref "cronjob" >}}), but it starts immediately while CronJob works based on a schedule.
 