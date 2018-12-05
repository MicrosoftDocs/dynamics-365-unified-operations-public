---
# required metadata

title: Cost configuration for DOM
description: This topic describes cost configuration for distributed order management (DOM) functionality in Microsoft Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 12/05/2018
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-12-15
ms.dyn365.ops.version: 

---
# Cost configuration for DOM

Organizations cosider multiple cost components when determining the optimal location from which to fulfill an order. Some of these cost components are shipping cost, handling cost, and packaging cost. A combination of these costs is computed to determine the fulfillment location. 

The first iteration of DOM in Retail only factored for distance when optimizing the assignment of orders to locations. While distance can be co-related with cost, it is not the same. For example, an over-night shipping method will cost higher than a 3-day shipping or a 7-day shipping for the same distance. 

The cost configuration feature allows retailers to define and configure additional cost components that will be calculated and factored in when deciding the optimal location for the fulfillment of order lines.  

When cost components are configured, the DOM solver will use only these cost definitions to decide the optimal location for order fulfillment. It will not weigh in the distance component as a cost at all. If no cost components are configured, then the DOM solver will fall back to the distance component as a cost to determine the fulfillment location for orders.

## Set up cost components

There are two major cost component types that can be defined in the system -- shipping, and other.

Both support multiple calculation basis as explained in the table below.

| Cost type | Calculation basis |
|-----------|-------------------|
| Shipping  | Simple            |
|           | Tiered            |
| Other     | Sales order       |
|           | Sales line        |
|           | Location          |

### Shipping cost type
The section below explains how each combination of the cost type and calculation basis for shipping cost can be set up and how they are used by the DOM solver.

#### Cost type shipping and calculation basis simple

This combination of cost type and calculation basis is used to define shipping cost for a mode of delivery either based on a flat cost or per distance.

The fields that need to be set up for this combination are:

-   **Cost factor**: This is the unique identifier id for the cost factor.

-   **Description**: This is the name and description of the cost factor.

-   **Start date** and **End date**: These fields can be used to restrict the cost factor for a given date range. If the fields are left blank, the cost factors are valid for an indefinite period.

-   **Active**: This field is used to mark whether the cost factor is active or not. Only active cost factors that are associated to the fulfillment profile are considered by DOM.

-   **Company**: This is the Legal entity for which the cost factor is configured. All lines of the calculation criteria need to be for one legal entity.

-   **Modes of delivery**: This field specifies the modes of delivery for which the cost is configured.

-   **Calculation type**: This field determines how the cost is calculated for a specific mode of delivery. There are two supported calculation types:
        -  Fixed: This denotes that a flat cost as defined in the cost field is the cost for the mode of delivery.
        -  Per-distance unit: This denotes that the cost for the mode of delivery is computed as the cost defined in the cost field times the distance between the delivery address and the locations.

-   **Cost**: This field is used to define the cost value that is used in conjunction with the **Calculation type** to compute the cost for a mode of delivery.

#### Cost type shipping and calculation basis tiered

This combination is used to define shipping cost for a mode of delivery either based on a flat cost or per distance based on a tiered range of distances.

The fields that needs to be set up for this combination of configuration are:

-   **Cost factor**: This is the unique identifier id for the cost factor.

-   **Description**: This is the name and description of the cost factor.

-   **Default cost**: If the distance between the delivery address and the location does not fall into any of the tiered distances for a mode of delivery, then the value in the **Default cost** field is used as the cost for that mode of delivery for that tiered distance.

-   **Start date** and **End date**: These fields can be used to restrict the cost factor for a given date range. If left blank, the cost factors are valid for an indefinite period.

-   **Active**: This field is used to mark whether the cost factor is active or not. Only active cost factors that are associated to the fulfillment profile are considered by DOM.

-   **Company**: This is the legal entity for which the cost factor is configured. All lines of the calculation criteria need to be for one legal entity.

-   **Modes of delivery**: This field specifies the modes of delivery for which the cost is configured.

-   **Distance type**: This field is used to define whether the tiered distance definition is in aerial distance or road distance.

-   **Distance units**: This field is used to specify the unit in which the tiered distance is defined.

-   **Distance from**: This field defines the beginning range of the tiered distance.

-   **Distance to**: This field defines the end range for the tiered distance.

-   **Calculation type**: This field determines how the cost is calculated for a specific mode of delivery and tiered distance. There are two supported calculation types:
        - Fixed: This denotes that a flat cost as defined in the cost field is the cost for the mode of delivery and the tiered distance.
        - Per distance unit: This denotes that the cost for the mode of delivery and tiered distance is computed as the cost defined in the cost field times the distance between the delivery address and the locations.

-   **Cost**: This field is used to define the cost value that is used in conjunction with the **Calculation type** to compute the cost for a mode of delivery.

 **Notes:**
-   When defining tiered distances, the system will validate that there are no missing or overlapping distances.

-   The **Distance type** used for a mode of delivery must be the same across all the tiered distances.

### Other cost type
The section below explains how each combination of cost type and other cost type for non-shipping cost can be set up and how they are used by the DOM solver.

####  Cost type, other cost type, sales order

This combination of cost type and other cost type is used to define non-shipping costs at a sales order level.

The fields that must be set up for this combination are:

-   **Cost factor**: This is the unique identifier id for the cost factor.

-   **Description**: This is the name and description of the cost factor.

-   **Start date** and **End date**: These fields can be used to restrict the cost factor for a given date range. If left blank, the cost factors are valid for an indefinite period.

-   **Active**: This field is used to mark whether the cost factor is active or not. Only active cost factors that are associated to the fulfillment profile are considered by DOM.

-   **Cost**: This field is used to define the cost value for a non-shipping cost at a sales order level.

####  Cost type, other cost type, sales line

This combination of cost type and other cost type is used to define non-shipping costs at a sales order line level.

The fields that must be set up for this combination are:

-   **Cost factor**: This is the unique identifier id for the cost factor.

-   **Description**: This is the name and description of the cost factor.

-   **Start date** and **End date**: These fields can be used to restrict the cost factor for a given date range. If left blank, the cost factors are valid for an indefinite period.

-   **Active**: This field is used to mark whether the cost factor is active or not. Only active cost factors that are associated to the fulfillment profile are considered by DOM.

-   **Cost**: This field is used to define the cost value for a non-shipping cost at a sales order line level.

####  Cost type, other cost type, location

This combination of cost type and other cost type is used to define non-shipping costs for a group of locations or individual location.

The fields that must be set up for this combination are:

-   **Cost factor**: This is the unique identifier id for the cost factor.

-   **Description**: This is the name and description of the cost factor.

-   **Start date** and **End date**: These fields can be used to restrict the cost factor for a given date range. If left blank, the cost factors are valid for an indefinite period.

-   **Active**: This field is used to mark whether the cost factor is active or not. Only active cost factors that are associated to the fulfillment profile are considered by DOM.

-   **Fulfillment group**: The group of locations for which the non-shipping cost is defined.

-   **Fulfillment location** The location for which the non-shipping cost is defined. Configuration of fulfillment group and fulfillment location on the same line for location-based calculation criteria is not supported.

-   **Cost**: This field is used to define the cost value for a non-shipping cost at a fulfillment group or fulfillment location level. The cost factor needs to be added to the relevant fulfillment profile for DOM to consider these costs in its execution.

