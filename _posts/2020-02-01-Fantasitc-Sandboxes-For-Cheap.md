---
layout: post
title: "Fantastic Sandboxes for Cheap"
date: 2020-02-01
---

Still in Preview as of this writing, Azure Spot VMs are great for folks for like me who need to create sandboxes for groups of people with 
workloads that can be interrupted. More importantly, these Spot instances difer from DevTestLab VMs in that they can accept images you've
custom-built. This feature comes in handy if you're testing software under specific conditions, like me. 

According to the Microsoft [documentation](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/spot-vms): Spot VMs allows you to take advantage of our unused capacity at a significant cost savings. At any point in time when Azure needs the capacity back, the Azure infrastructure will evict Spot VMs. Therefore, Spot VMs are great for workloads that can handle interruptions like batch processing jobs, dev/test environments, large compute workloads, and more.

There are some caveats when using these Spot VMS to consider before deploying them:
- Spot VMs do not support B-series
- Promo VM sizing like Dv2, NV, NC, H are unavailalbe
- There iss no SLA
- Spot VMs cannot support ephemeral OS disks
- Spot VMs cannot be deployed to Azure China, or Department of Defense (DoD) in the Government region

Of course, these restricitons make sense as B-series Burstable VMs are cost-effective ways to get more compute power for less money
per hour. Spot VMs made a D2s V3 server 60% cheaper my Pay-As-You-Go subscription hosted in the East2 region and 81% cheaper for a DS2 v2 VM
in the same region. That's wonderful news.
