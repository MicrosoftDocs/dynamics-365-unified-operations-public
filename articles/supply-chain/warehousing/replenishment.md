---
# required metadata

title: Replenishment overview
description: This article describes the replenishment strategies that are available for warehouses that use the functionality that is available in Warehouse management.
author: Mirzaab
ms.date: 02/19/2020
ms.topic: overview
ms.prod: 

ms.technology: 

# optional metadata

ms.search.form: WHSReplenishmentTemplates, WHSReplenishmentTemplates, WHSInventFixedLocation, WHSRequestType
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 49fa97eb-8e10-49a5-9261-1e393159f178
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Replenishment overview

[!include [banner](../includes/banner.md)]

This article describes the replenishment strategies that are available for warehouses that use the functionality that is available in Warehouse management. The information in this article doesn't apply to the warehousing solution that is available in Inventory management.

The following replenishment strategies are available:

- **Wave demand replenishment** – This strategy creates replenishment work for outbound orders or loads if inventory isn't available when the wave creates work. For example, replenishment work can be created if the quantity that is required for a sales order isn't available when a wave is processed.
- **Min/Max replenishment** – This strategy uses minimum and maximum stocking limits to determine when locations should be replenished. The item and location criteria define the inventory that is evaluated for replenishment. Min/Max replenishment templates are the primary mechanism for maintaining optimal levels in picking locations. To help guarantee that enough pick face inventory is available to meet wave demand, you can use demand replenishment as a supplement between Min/Max replenishment cycles.
- **Load demand replenishment** – This strategy sums the demand for several loads and creates the replenishment work that is required in order to stock the relevant picking locations. This strategy helps guarantee that the loads that are created can be picked in the warehouse after they are released.
- **Immediate replenishment** – This strategy replenishes inventory before a wave is run if allocation fails for a location directive line that has a replenishment template. 

All four strategies create replenishment work, based on a replenishment template.

## Wave demand replenishment
Wave demand replenishment creates replenishment work, based on demand, if the quantity that is required for production orders, kanbans, outbound orders, or loads isn't available when a wave creates work. The replenishment template contains information about the item criteria, the unit of measure, the demand increment, and the location. 

Location directives are used to determine which location should be replenished. You link these location directives to the replenishment template by using the **Directive code** field. If the **Directive code** field isn't set, queries are used to determine which location directive should be used. Note that if a directive code isn't specified in the replenishment template, and the location directive has a directive code, the location directive will be ignored, even if the query on the location directive is correct. Pick location directives are used to determine where to get inventory for the replenishment. 

In addition to creating a template, you must specify some replenishment settings in the wave template. The wave template should contain a wave step for replenishment that is run only if an item isn't successfully allocated. This replenishment wave step uses a wave step code to determine which replenishment template should be used. In addition to having a wave step for replenishment, you must make sure that **Replenish** is selected in the **Methods** section of the wave template. 

The **Replenishment template** page includes an **Allow wave demand to use unreserved quantities** check box. Select this check box if demand replenishment should be able to deduct unreserved quantities from work that is generated from the selected replenishment template. To enable demand replenishment templates to use this logic, select this check box for every existing replenishment template. When demand replenishment is triggered in the warehouse, it will deduct the demand from existing replenishment work that has unreserved quantities, if the work originates from replenishment templates where the **Allow wave demand to use unreserved quantities** check box is selected.

**Replenishment unit** is the minimum unit to replenish. This must be a whole number that is a multiple of the unit. The system will round up to the highest unit possible when creating work.

Demand replenishment is supported for sales orders, transfer orders, production orders, and kanbans. 

## Min/Max replenishment
In Min/Max replenishment, stock is replenished so that it's between the minimum and maximum limits that have been set. Typically, this process occurs one time every day, to help guarantee that all picking locations are filled to the maximum level before picking starts. 

The minimum and maximum amounts are set in a replenishment template. Many of the other settings in the template resemble the settings in templates that are used in Wave demand replenishment. The template should contain one line for each item and location. When you run replenishment by using the batch job, the system evaluates whether replenishment is required by using the sequence that the lines are organized in. 

Note that the Min/Max replenishment strategy can't replenish an empty location unless the location is set as the fixed location for the item. If the location that must be replenished isn't a fixed location, the system can't determine which item should be replenished. Therefore, at least some on-hand quantity is required before replenishment occurs.

## Load demand replenishment
Load demand replenishment sums the demand for several loads and creates the replenishment work that is required in order to stock the relevant picking locations. Load demand replenishment resembles Wave demand replenishment in many ways. The main difference is how and when Load demand replenishment and Wave demand replenishment are run. Like Min/Max replenishment, Load demand replenishment is run by using a batch job. To set up the batch job, on the **Load demand replenishment** page, select the replenishment template to use, and set a filter query to specify which loads are used to determine the demand. The location query defines the locations that any available quantity will be subtracted from to meet the aggregated demand of the loads.

## Immediate replenishment
Instead of having to sum demand at the end of an allocation process and do replenishment on the basis of the summed up quantity, you can apply the Immediate replenishment strategy. When you use this strategy, the inventory can be replenished immediately after a location directive line fails. Therefore, you can set up the replenishment so that it's restricted by specific units, and so that it uses quantities that are set for specific locations.

## Replenishment prerequisites

|      Prerequisite       |                                                                                                                                Description                                                                                                                                 |
|-------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          Item           |                                                                                                        The item must be enabled for warehouse management processes (WMS).                                                                                                        |
|        Warehouse        | The warehouse must be enabled for warehouse management processes (WMS). To enable a warehouse for WMS, on the <strong>Warehouses</strong> page, select the warehouse, and then select the <strong>Use warehouse management processes</strong> option. |
| Replenishment templates |                                                                   At least one replenishment template must be set up for Min/Max replenishment, Wave demand replenishment, or Load demand replenishment.                                                                   |
|        Locations        |                                                                                                       Locations must be created and connected to a location profile.                                                                                                       |
|    Location profiles    |                                                                                                        Location profiles are required in order to create locations.                                                                                                        |
|   Location directives   |                                                       Location directives are required in order to guide work to the locations where replenishment is required and to the locations that inventory is sourced from.                                                        |
|     Work templates      |                                                   Work templates of the <strong>Replenishment</strong> type are required in order to create replenishment work so that inventory can be moved to the desired locations.                                                    |



[!INCLUDE[footer-include](../../includes/footer-banner.md)]