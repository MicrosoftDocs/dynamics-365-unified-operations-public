---
# required metadata

title: Replenishment strategies
description: The replenishment strategy on the wave demand replenishment template lines allows for users to choose how to do replenishment. 
author: mirzaab
manager: tfehr
ms.date: 10/29/2020
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
ms.search.validFrom: 2020-10-29
ms.dyn365.ops.version: Release 10.0.16
---

# Replenishment strategies

[!include [banner](../includes/banner.md)]

The templates defined on the **Replenishment templates** page include wave demand replenishment template lines that let you control how replenishment is done. Each line now provides a **Replenishment strategy** setting.

The *Wave demand quantity* strategy is the default strategy, and is the replenishment strategy that was used before the introduction of the **Replenishment strategy** field. It uses the replenishment location directives to find locations that could be replenished and replenishes them until the demand is covered.

The *Maximum location capacity* strategy introduces some new functionality. This strategy uses the location directives to find locations that could be replenished, and it will replenish them until the demand is covered. It differs from the *Wave demand quantity* strategy in that all the replenished locations are replenished to the maximum of their capacity, as defined by the location stocking limits. The *Maximum location capacity* strategy tries to create work to bring the requested quantity plus some extra quantity to fill the locations being replenished. Sometimes that won't be possible, such as when the bulk locations don't have enough inventory to cover the extra quantity. In these cases, the system will detect the failure and try to recover.

One example where the *Maximum location capacity* strategy would be preferred over the *Wave demand quantity* strategy is during peak season. Here, some items could be selling at high volume, so you might want to proactively replenish the relevant picking locations as much as possible to reduce the number of work IDs created for replenishment.

> [!IMPORTANT]
> For the *Maximum location capacity* strategy to work, you must redefine the stocking limits for the relevant location. Otherwise, the strategy will work just like the *Wave demand quantity* strategy.

## Enable the Replenish to max based on stocking limits feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Replenish to max based on stocking limits*

## Set up replenishment strategies

Access the templates by going to **Warehouse management \> Setup \> Replenishment \> Replenishment templates**. Select or create a wave demand replenishment template with a **Replenishment type** of *Wave demand*. Then set up its replenishment template lines in the **Replenishment template details** section. For each line, select the **Replenishment strategy** you want to use.

![Replenishment template](media/ReplenTempWaveDmdMaxLocCap.png "Replenishment template")

If you don't see the **Replenishment strategy** column in the grid in the **Replenishment template details** section, make sure that the feature has been enabled and that the selected replenish template has a **Replenishment type** of *Wave demand*.

> [!NOTE]
> The default strategy is *Wave demand quantity*. This means you only need to update the replenishment template lines where you want to use the *Maximum location capacity* strategy.

## Example scenarios

### Example 1

In this example, we assume that there is only one replenishment template with only one replenishment template line.

We create a sales order for 130 pcs of item A0001. Before we release to warehouse, the setup of the warehouse is as follows:

- There is only one bulk location with 500 pcs available on-hand inventory.
- There are three pick locations, which have stocking limits of 100 pcs. (Remember that stocking limits are required for the *Maximum location capacity* strategy.) 
- The replenishment put locations are the same as the sales pick locations.
- The replenishment unit is in boxes (1 Box = 20 pcs).

At the time of the order, the on-hand inventories at the sales pick locations are:

- Pick-001: 20 pcs (1 Box)
- Pick-002: 0 pcs
- Pick-003: 0 pcs

Initially, the replenishment strategy is set to *Wave demand quantity*.

After releasing the sales order to the warehouse and wave processing runs for the wave, we get the following replenishment work:

- Replenishment work 1: Pick 4 boxes from bulk and put them at location pick-001
- Replenishment work 2: Pick 2 boxes from bulk and put them at location pick-002

We get two replenishment work IDs because we need to replenish two different locations, and multi-puts are not supported.

If the replenishment strategy were set to *Maximum location capacity*, we would get the following replenishment work:

- Replenishment work 1: Pick 4 boxes from bulk and put them at location pick-001
- Replenishment work 2: Pick 5 boxes from bulk and put them at location pick-002

[![Example 1](media/ReplenTemp_example_1.png "Example 1")](media/ReplenTemp_example_1_large.png)

### Example 2

To see what would happen when there isn't enough inventory in the bulk location to cover the extra quantity, consider the same scenario as above, but with the difference that the bulk location holds 160 pcs (8 Boxes).

The *Wave demand quantity* strategy would create the same work as before. However, the *Maximum location capacity* strategy would try to create the work IDs as before, so it could fail. At that point the system would try to recover.

Based on whether the **Allow split** option is set on the location directives for replenishment picking, the following two outcomes are possible. If **Allow split** is set to *Yes*, then the following replenishment work would be created:

- Replenishment work 1: Pick 4 boxes from bulk and put them at location pick-001
- Replenishment work 2: Pick 4 boxes from bulk and put them at location pick-002

If **Allow split** is set to *No*, then the following replenishment work would be created:

- Replenishment work 1: Pick 4 boxes from bulk and put them at location pick-001
- Replenishment work 2: Pick 2 boxes from bulk and put them at location pick-002

The reason for the different results has to do with the information that is available when we create the work. When **Allow split** is set on the location directives for replenishment picks, we know that we managed to find 160 pcs, so we can create work for that. On the other hand, when we don't have **Allow split** enabled, then we don't know of the existence of the 160 pcs. Since the extra quantity that we decided to replenish was 3 boxes, we drop them, and we try again the original quantity.

[![Example 2](media/ReplenTemp_example_2.png "Example 2")](media/ReplenTemp_example_2_large.png)

So, to get the maximum possible quantity to the replenished locations, **Allow split** should be enabled on the location directives for replenishment picks.
