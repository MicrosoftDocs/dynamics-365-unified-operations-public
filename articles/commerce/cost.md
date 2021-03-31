---
# required metadata

title: Cost configuration for distributed order management (DOM)
description: This topic describes cost configuration for the distributed order management (DOM) functionality in Dynamics 365 Commerce.
author: josaw1
ms.date: 12/05/2018
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-12-15
ms.dyn365.ops.version: 

---
# Cost configuration for distributed order management (DOM)

[!include [banner](../includes/banner.md)]

Organizations consider multiple cost components to determine the optimal location to fulfill an order from. Some of these cost components are shipping cost, handling cost, and packaging cost. A combination of these costs is calculated to determine the fulfillment location.

When the first iteration of distributed order management (DOM) in Dynamics 365 Commerce optimized the assignment of orders to fulfillment locations, it factored in distance only. Although distance can be correlated with cost, it isn't the same as cost. For example, an overnight shipping method costs more than three-day shipping or seven-day shipping over the same distance.

The cost configuration feature lets retailers define and configure additional cost components that will be calculated and factored in to determine the optimal location to fulfill order lines from.

When cost components are configured, the DOM solver uses only those cost definitions to determine the optimal location for order fulfillment. It doesn't consider the distance component as a cost. However, if no cost components are configured, the DOM solver does use the distance component as a cost to determine the optimal location for order fulfillment.

## Set up cost components

Two major cost component types can be defined in the system: **Shipping** and **Other**.

Both cost component types support multiple calculation bases, as shown in the following table.

<table>
<thead>
<tr>
<th>Cost component type</th>
<th>Calculation basis</th>
</tr>
</thead>
<tbody>
<tr>
<td>Shipping</td>
<td>
<ul>
<li>Simple</li>
<li>Tiered</li>
</ul>
</td>
</tr>
<tr>
<td>Other</td>
<td>
<ul>
<li>Sales order</li>
<li>Sales line</li>
<li>Location</li>
</ul>
</td>
</tr>
</tbody>
</table>

### Shipping cost component type

This section explains how to set up each combination of the **Shipping** cost component type and a calculation basis for shipping costs. It also explains how the DOM solver uses each combination.

#### Cost component type = Shipping and Calculation basis = Simple

If a combination of the **Shipping** cost component type and the **Simple** calculation basis is used, the shipping cost for a mode of delivery is based on either a flat cost or distance.

You must set up the following fields for this combination:

- **Cost factor** – Enter a unique identifier for the cost factor.
- **Description** – Enter the name and description of the cost factor.
- **Start date** and **End date** – You can use these fields to limit the cost factor for a specific date range. If you leave these fields blank, the cost factor is valid for an indefinite period.
- **Active** – Indicate whether the cost factor is active. The DOM considers only active cost factors that are associated with the fulfillment profile.
- **Company** – Specify the legal entity that the cost factor is configured for. All lines of the calculation criteria must be for the same legal entity.
- **Modes of delivery** – Specify the modes of delivery that the cost is configured for.
- **Calculation type** – Specify how the cost should be calculated for a specific mode of delivery. Two calculation types are supported:

    - **Fixed** – A flat cost is used for the mode of delivery. If you select this calculation type, the **Cost** field defines the flat cost.
    - **Per-distance unit** – The cost for the mode of delivery is calculated as the cost value that is specified in the **Cost** field times the distance between the delivery address and the locations.

- **Cost** – Specify the cost value that is used in conjunction with the **Calculation type** field to compute the cost for a mode of delivery.

#### Cost component type = Shipping and Calculation basis = Tiered

If a combination of the **Shipping** cost component type and the **Tiered** calculation basis is used, the shipping cost for a mode of delivery is based on either a flat cost or distance. However, in this combination, the distance is based on a tiered range of distances.

You must set up the following fields for this combination:

- **Cost factor** – Enter a unique identifier for the cost factor.
- **Description** – Enter the name and description of the cost factor.
- **Default cost** – Specify the cost that should be used for a mode of delivery if the distance between the delivery address and the location doesn't fall into any of the tiered distances for the mode of delivery.
- **Start date** and **End date** – You can use these fields to limit the cost factor for a specific date range. If you leave these fields blank, the cost factor is valid for an indefinite period.
- **Active** – Indicate whether the cost factor is active. The DOM considers only active cost factors that are associated with the fulfillment profile.
- **Company** – Specify the legal entity that the cost factor is configured for. All lines of the calculation criteria must be for the same legal entity.
- **Modes of delivery** – Specify the modes of delivery that the cost is configured for.
- **Distance type** – Specify whether the tiered distance definition is an aerial distance or a road distance.
- **Distance units** – Specify the unit that the tiered distance is measured in.
- **Distance from** – Specify the start range for the tiered distance.
- **Distance to** – Specify the end range for the tiered distance.
- **Calculation type** – Specify how the cost should be calculated for a specific mode of delivery and tiered distance. Two calculation types are supported:

    - **Fixed** – A flat cost is used for the mode of delivery. If you select this calculation type, the **Cost** field defines the flat cost.
    - **Per distance unit** – The cost for the mode of delivery and tiered distance is calculated as the cost value that is specified in the **Cost** field times the distance between the delivery address and the locations.

- **Cost** – Specify the cost value that is used in conjunction with the **Calculation type** field to compute the cost for a mode of delivery.

> [!NOTE]
> - When you define tiered distances, the system validates that there are no missing or overlapping distances.
> - The distance type that is used for a mode of delivery must be the same across all the tiered distances.

### Other cost component type

This section explains how to set up each combination of the **Other** cost component type and an other cost type for non-shipping costs. It also explains how the DOM solver uses each combination.

#### Cost component type = Other and Other cost type = Sales order

A combination of the **Other** cost component type and the **Sales order** other cost type is used to define non-shipping costs at the sales order level.

You must set up the following fields for this combination:

- **Cost factor** – Enter a unique identifier for the cost factor.
- **Description** – Enter the name and description of the cost factor.
- **Start date** and **End date** – You can use these fields to limit the cost factor for a specific date range. If you leave these fields blank, the cost factor is valid for an indefinite period.
- **Active** – Indicate whether the cost factor is active. The DOM considers only active cost factors that are associated with the fulfillment profile.
- **Cost** – Specify the cost value for a non-shipping cost at the sales order level.

#### Cost component type = Other and Other cost type = Sales line

A combination of the **Other** cost component type and the **Sales line** other cost type is used to define non-shipping costs at the sales order line level.

You must set up the following fields for this combination:

- **Cost factor** – Enter a unique identifier for the cost factor.
- **Description** – Enter the name and description of the cost factor.
- **Start date** and **End date** – You can use these fields to limit the cost factor for a specific date range. If you leave these fields blank, the cost factor is valid for an indefinite period.
- **Active** – Indicate whether the cost factor is active. The DOM considers only active cost factors that are associated with the fulfillment profile.
- **Cost** – Specify the cost value for a non-shipping cost at the sales order line level.

#### Cost component type = Other and Other cost type = Location

A combination of the **Other** cost component type and the **Location** other cost type is used to define non-shipping costs for a group of locations or an individual location.

You must set up the following fields for this combination:

- **Cost factor** – Enter a unique identifier for the cost factor.
- **Description** – Enter the name and description of the cost factor.
- **Start date** and **End date** – You can use these fields to limit the cost factor for a specific date range. If you leave these fields blank, the cost factor is valid for an indefinite period.
- **Active** – Indicate whether the cost factor is active. The DOM considers only active cost factors that are associated with the fulfillment profile.
- **Fulfillment group** – Specify the group of locations that the non-shipping cost is defined for.
- **Fulfillment location** – Specify the location that the non-shipping cost is defined for.

    > [!NOTE]
    > You can't specify a fulfillment group and a fulfillment location on the same line for location-based calculation criteria.

- **Cost** – Specify the cost value for a non-shipping cost at the fulfillment group level or fulfillment location level.

> [!IMPORTANT]
> For DOM to consider these costs when it's run, you must add the cost factor to the relevant fulfillment profile.


[!INCLUDE[footer-include](../includes/footer-banner.md)]