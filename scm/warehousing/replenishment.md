---
# required metadata

title: Replenishment
description: This article describes the replenishment strategies that are available for warehouses that use the functionality that is available in Warehouse management.
author: YuyuScheller
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: WHSReplenishmentTemplates
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 90043
ms.assetid: 49fa97eb-8e10-49a5-9261-1e393159f178
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Replenishment

[!include[banner](../includes/banner.md)]


This article describes the replenishment strategies that are available for warehouses that use the functionality that is available in Warehouse management.

This article describes the replenishment strategies that are available for warehouses that use the functionality that is available in Warehouse management. The information doesn't apply to the warehousing solution that is available in Inventory management. Three replenishment strategies are available:

-   **Wave demand replenishment** – This strategy creates replenishment work for outbound orders or loads if inventory isn't available when the wave creates work. For example, replenishment work can be created if the quantity that is required for a sales order isn't available when a wave is processed.
-   **Min/Max replenishment** – This strategy uses minimum and maximum stocking limits to determine when locations should be replenished. The item and location criteria define the inventory that is evaluated for replenishment. Min/Max replenishment templates are the primary mechanism for maintaining optimal levels in picking locations. To help guarantee that enough pick face inventory is available to meet wave demand, you can use demand replenishment as a supplement between Min/Max replenishment cycles.
-   **Load demand replenishment** – This strategy sums the demand for several loads and creates the replenishment work that is required in order to stock the relevant picking locations. This strategy helps guarantee that the loads that are created can be picked in the warehouse after they are released.

All three strategies create replenishment work, based on a replenishment template.

## Wave demand replenishment
Wave demand replenishment creates replenishment work, based on demand, if the quantity that is required for outbound orders or loads isn't available when a wave creates work. The replenishment template contains information about the item criteria, the unit of measure, the demand increment, and the location. 

Location directives are used to determine which location should be replenished. You link these location directives to the replenishment template by using the **Directive code** field. If the **Directive code** field isn't set, queries are used to determine which location directive should be used. Note that if a directive code isn't specified in the replenishment template, and the location directive has a directive code, the location directive will be ignored, even if the query on the location directive is correct. Pick location directives are used to determine where to get inventory for the replenishment. 

In addition to creating a template, you must specify some replenishment settings in the wave template. The wave template should contain a wave step for replenishment that is run only if allocation of an item isn't successful. This replenishment wave step uses a wave step code to determine which replenishment template should be used. In addition to having a wave step for replenishment, you must make sure that **replenish** is selected in the **Methods** section of the wave template. 

The **Replenishment template** page includes an **Allow wave demand to use unreserved quantities** check box. You should select this check box if you want to allow demand replenishment to deduct unreserved quantities from work that is generated from the selected replenishment template. To enable demand replenishment templates to use this logic, you must set the check box for every existing replenishment template. When demand replenishment is triggered in the warehouse, it will deduct the demand from existing replenishment work that has unreserved quantities, if the work originates from replenishment templates where the **Allow wave demand to use unreserved quantities** check box is selected.

## Min/Max replenishment
In Min/Max replenishment, stock is replenished so that it's between the minimum and maximum limits that have been set. Typically, this process occurs one time every day to help guarantee that all picking locations are filled to the maximum level before picking starts. 

The minimum and maximum amounts are set in a replenishment template. Many of the other settings in the template resemble the settings in templates that are used in Wave demand replenishment. The template should contain one line for each item and location. When you run replenishment by using the batch job, Microsoft Dynamics 365 for Operations evaluates whether replenishment is required, in the sequence that the lines are organized in. 

Note that the Min/Max replenishment strategy can't replenish an empty location unless the location is set as the fixed location for the item. If the location that must be replenished isn't a fixed location, Dynamics 365 for Operations can't determine which item to replenish. Therefore, at least some on-hand quantity is required before replenishment occurs.

## Load demand replenishment
Load demand replenishment sums the demand for several loads and creates the replenishment work that is required in order to stock the relevant picking locations. Load demand replenishment resembles Wave demand replenishment in many ways. The main difference is how and when Load demand replenishment and Wave demand replenishment are run. Like Min/Max replenishment, Load demand replenishment is run by using a batch job. To set up the batch job, on the **Load demand replenishment** page, select the replenishment template to use, and set a filter query to specify which loads are used to determine the demand. The location query defines the locations that any available quantity will be subtracted from to meet the aggregated demand of the loads.

## Replenishment prerequisites
| Prerequisite            | Description                                                                                                                                                                                                                                        |
|-------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Item                    | The item must be enabled for warehouse management processes.                                                                                                                                                                                       |
| Warehouse               | The warehouse must be enabled for warehouse management processes. To enable the warehouse for warehouse management processes, on the **Warehouses** page, select the warehouse, and then select the **Use warehouse management processes** option. |
| Replenishment templates | At least one replenishment template must be set up for Min/Max replenishment, Wave demand replenishment, or Load demand replenishment.                                                                                                             |
| Locations               | Locations must be created and connected to a location profile.                                                                                                                                                                                     |
| Location profiles       | Location profiles are required in order to create locations.                                                                                                                                                                                       |
| Location directives     | Location directives are required in order to guide work to the locations where replenishment is required, and to the locations that inventory is sourced from.                                                                                     |
| Work templates          | Work templates of the **Replenishment** type are required in order to create replenishment work so that inventory can be moved to the desired locations.                                                                                           |




