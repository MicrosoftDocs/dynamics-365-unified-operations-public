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

On **Replenishment templates** the replenishment strategy on the wave demand replenishment template lines allows for users to choose how to do replenishment. The *wave demand quantity* strategy is the default strategy, and it works in exactly the same way as the wave demand replenishment before the introduction of the replenishment strategy field. It uses the replenishment location directives to find locations that could be replenished and replenishes them until the demand is covered.

The *maximum location capacity* strategy introduces some new functionality. This strategy will use the location directives to find locations that could be replenished, and it will replenish them until the demand is covered. The difference with the *wave demand quantity* strategy, is that all the replenished locations are replenished to the maximum of their capacity as it is defined by the location stocking limits.

When we are using the *maximum location capacity* strategy, we are trying to create work to bring the requested quantity plus some extra quantity to fill the locations we are replenishing. Sometimes, that won’t be possible. For example, when the bulk locations don’t have enough inventory to cover the extra quantity. In these cases, we detect the failure, and we try to recover.

An example, where this replenishment strategy would be preferred over the *wave demand quantity* strategy, is during peak season, where some items are selling a lot we want to proactively replenish the picking locations as much as possible to reduce the number of work created for replenishment.

> [!IMPORTANT]
> For the *maximum location capacity* strategy to work, the stocking limits of the location need to be defined. If not, the strategy will work as the wave demand quantity strategy.

## Enable the Replenish to max based on stocking limits feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Replenish to max based on stocking limits*

## Set up replenishment strategies

The replenishment strategy is a property of the replenishment template detail lines. If you do not see the **replenishment strategy** field on the line in the **replenishment Template Details** section, ensure that the feature has been enabled and that the selected **replenish template** has the **replenishment type** of *Wave demand*.

Access the templates by navigating to **Warehouse management \> Setup \> Replenishment \> Replenishment templates**.

Select or create the wave demand replenishment template you want to set up. The replenishment strategy can be edited on the replenishment template lines appearing in the **replenishment template details** section.

> [!NOTE]
> The default strategy is the *wave demand quantity*. This means you only need to update the replenishment template lines that you want to use the *maximum location capacity* strategy.

![Replenishment template](media/ReplenTempWaveDmdMaxLocCap.png "Replenishment template")

## Examples

In this example, we assume that there is only one replenishment template with only one replenishment template line.

We create a sales order for item A0001 of 130 pcs. Before we release to warehouse, the setup of the warehouse is the following.

There is only one bulk location with available on-hand 500 pcs. There are three pick locations, that have stocking limits 100 pcs. (Remember that stocking limits is required for the strategy.) The replenishment put locations are the same as the sales pick locations, and the replenishment unit is in boxes (1 Box = 20 pcs).

At the time of the order the on-hand on the sales pick locations is as follows:

- Pick-001: 20 pcs (1 Box)
- Pick-002: 0 pcs
- Pick-003: 0pcs

Initially the replenishment strategy is set to wave demand quantity.

After releasing the sales order to the warehouse and the wave processing runs for the wave, we get the following replenishment work:

- Replenishment work 1: Pick 4 Boxes from Bulk and put it on Pick-001
- Replenishment work 2: Pick 2 Boxes from Bulk and put it on Pick-002

We get two replenishment works because we need to replenish two different locations, and multi-puts are not supported.

If the replenishment strategy were set to maximum location capacity the replenishment work would be the following:

- Replenishment work 1: Pick 4 Boxes from Bulk and put it on Pick-001
- Replenishment work 2: Pick 5 Boxes from Bulk and put it on Pick-002

To demonstrate what would happens when there is not enough inventory in the bulk location to cover the extra quantity, we consider the same scenario as above, with the difference that the bulk location holds 160 pcs (8 Boxes)

The wave demand quantity strategy would create the same work as before. On the other hand, the maximum location capacity strategy would try to create the works as before and it could fail. At that point we would try to recover.

Based on whether the allow split option is set on the location directives for replenishment picking, the following two outcomes are possible. If the allow split is set to true, then the replenishment work that will be created is the following:

- Replenishment work 1: Pick 4 Boxes from Bulk and put it on Pick-001
- Replenishment work 2: Pick 4 Boxes from Bulk and put it on Pick-002

If the allow split is not set to true, then the replenishment work that will be created is the following:

- Replenishment work 1: Pick 4 Boxes from Bulk and put it on Pick-001
- Replenishment work 2: Pick 2 Boxes from Bulk and put it on Pick-002

The reason for the different results has to do with the information that is available when we create the work. When the allow split is set on the location directives for replenishment picks, we know that we managed to find 160 pcs, so we can create work for that. On the other hand, when we don’t have the allow split enabled, then we don’t know of the existence of the 160 pcs. Since the extra quantity that we decided to replenish was 3 Boxes, we drop them, and we try again the original quantity.

So, to get the maximum quantity possible to the replenished locations the allow split should be enabled on the location directives for replenishment picks.
