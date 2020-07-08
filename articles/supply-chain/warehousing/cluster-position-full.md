---
# required metadata

title: Cluster position full
description: This feature offers an alternative to more rigid enforcement of work break rules when using cluster picking as it enables larger margin of error in volumetric constraints of containers or totes. 
author: Mirzaab
manager: tfehr
ms.date: 07/08/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: Release 10.0.8
---

# Cluster position full

[!include [banner](../includes/banner.md)]

This feature offers an alternative to more rigid enforcement of work break rules when using cluster picking as it enables larger margin of error in volumetric constraints of containers or totes. It is a common scenario that not all items within the work order fit into a selected container. This leaves the warehouse worker who is cluster picking with little option for resolution, either changing the container size to a larger one or solving it differently with the supervisor.

This functionality introduces the ability to execute "full" option on one of the work units within a cluster. This was not an option with cluster picking in older version, but it was only available with normal order picking. However, this feature differs from standard full button flow as it cancels the remaining work. It does not suggest user to add another bin to same cluster and it does not create new work automatically.

## Set up

The cluster picking mobile device menu item must have the **Allow splitting of work** parameter enabled. Add the SO Pick work class to the Cluster pick create mobile device menu item.

## Create picking work

Before cluster picking, some outbound work must be created. Previously created Cluster profile specifies 2 cluster positions, hence create at least two different Work IDs.

Navigate to **Sales and Marketing \> Sales orders \> All sales order**. Select **New** to create a new sales order. In the _General_ section specify warehouse 61.

1. Sales order 1 (US-010): Add a new line to the sales order, item T0100, quantity 5 pcs. Add a second line for item L0101, quantity 20 ea. Ensure the confirmed ship dates for both lines are today.
2. Sales order 2 (US-011): Add a new line to the sales order, item L0101, quantity 20 ea. Add a second line for item T0100, quantity 2 ea. Ensure the confirmed ship dates for both lines are today.

Reserve the inventory and Release it to warehouse. Two different Work IDs should have been created, each with two pick lines.

## Mobile device flow execution

1. Enter mobile device menu item Cluster pick create in Outbound.

1. Enter the first work ID to assign it to the cluster

1. Enter the second work ID to assign it to the cluster.

1. The system will automatically then direct the user to the first consolidate pick (2 PL of L0101).

1. Enter the LP to pick from and select **OK** to confirm the first pick

1. The system will show the user the second grouped pick, for 7 of item T0100.

1. Click position full, select position 1 as being full, and enter quantity 2 to pick (out of 5).

1. Select **OK**, enter the LP to pick from, and select **OK** to complete the work.

The user will be directed to put the cluster down to STAGE01.

As a result of the full, the original picking work for sales order 1, will remain in an open status, with one line for item T0100, quantity 3 associated with it. This is what was pulled off and still needs to be picked.

A new work ID has been created, associated with SO 1, that contains the pick for 1 PL of L0101, and the 2 of T0100 that were picked.