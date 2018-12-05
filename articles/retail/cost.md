---
# required metadata

title: Cost configuration
description: This topic describes the Cost configuration for Distributed order management (DOM) functionality in Microsoft Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 11/15/2018
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
ms.search.validFrom: 2018-11-15
ms.dyn365.ops.version: 

---
**Cost configuration**

**Overview**

Organizations weigh in multiple cost components while determining the optimal location to fulfill an order. Some of these cost components are shipping cost, handling cost, packaging cost etc. A combination of these costs is computed to determine the optimal fulfillment location for an order. 

The V1 feature of DOM only factored for distance when optimizing the assignment of orders to locations. While distance can be co-related with cost, it is not the same, as an over-night shipping method will cost higher than a 3 days shipping or a 7 days shipping for the same distance. 

The Cost configuration feature would enable retailers to define & configure additional cost components that will be calculated and factored in when deciding the optimal location for fulfillment of order lines.  

When cost components are configured, the DOM solver will only use these cost definitions to decide the optimal location for order fulfillment. It will not weigh in the distance component as a cost at all. If no cost components are configured, then the DOM solver will fall back to the distance component as a cost to determine the fulfillment location for orders

**Setup**

There are two major cost component type that can be defined in the system:

1.  Shipping

2.  Other

Both supports multiple calculation basis as explained in the table below:

| Cost type | Calculation basis |
|-----------|-------------------|
| Shipping  | Simple            |
|           | Tiered            |
| Other     | Sales order       |
|           | Sales line        |
|           | Location          |

The below section explains how each of the combination of the Cost type & Calculation basis for Shipping cost can be set-up and how they are used by the DOM solver:

1.  **Cost Type – Shipping, Calculation basis – Simple**

    This combination of Cost type and Calculation basis is used to define shipping cost for a mode of delivery either based on a flat cost or per distance.

    The below are the explanation of the fields that needs to be set-up for this combination of configuration:

-   Cost factor: This is the unique identifier id for the Cost factor

-   Description: This is the name / description of the cost factor

-   Start date / End date: These fields can be used to restrict the cost factor for a given date range. If left blank it would mean that the cost factors are valid for an indefinite period

-   Active: This field is used to mark whether the cost factor is active or not. Only active cost factors that are associated to the fulfillment profile is considered by DOM

-   Company: This is the Legal entity for which the cost factor is configured for. With the current release, all lines of the Calculation criteria need to be for one Legal entity.

-   Modes of delivery: This is the modes of delivery for which the cost is configured for

-   Calculation type: This field determines how the cost is calculated for a specific mode of delivery. There are two supported calculation types:

    a.  Fixed: This denotes that a flat cost as defined in the Cost field is the cost for the mode of delivery

    b.  Per distance unit: This denotes that the cost for the mode of delivery is computed as the cost defined in the Cost field times the distance between the delivery address & the locations

-   Cost: This field is used to define the Cost value that is used in conjunction with the Calculation type to compute the cost for a mode of delivery

2.  **Cost Type – Shipping, Calculation basis – Tiered **

    This combination of Cost type and Calculation basis is used to define shipping cost for a mode of delivery either based on a flat cost or per distance based on a tiered range of distances

    The below are the explanation of the fields that needs to be set-up for this combination of configuration:

-   Cost factor: This is the unique identifier id for the Cost factor

-   Description: This is the name / description of the cost factor

-   Default cost: If the distance between the delivery address and the location does not fall into any of the tiered distances for a mode of delivery, then the value in the Default cost field is used as the cost for that mode of delivery for that tiered distance

-   Start date / End date: These fields can be used to restrict the cost factor for a given date range. If left blank it would mean that the cost factors are valid for an indefinite period

-   Active: This field is used to mark whether the cost factor is active or not. Only active cost factors that are associated to the fulfillment profile is considered by DOM

-   Company: This is the Legal entity for which the cost factor is configured for. With the current release, all lines of the Calculation criteria need to be for one Legal entity.

-   Modes of delivery: This is the modes of delivery for which the cost is configured for

-   Distance type: This field is used to define whether the tiered distance definition is in Aerial distance or Road distance

-   Distance units: This field is used to specify the unit in which the tiered distance is defined

-   Distance from: This field defines the beginning range of the tiered distance

-   Distance to: This field defines the end range for the tiered distance

-   Calculation type: This field determines how the cost is calculated for a specific mode of delivery & tiered distance. There are two supported calculation types:

    c.  Fixed: This denotes that a flat cost as defined in the Cost field is the cost for the mode of delivery & the tiered distance

    d.  Per distance unit: This denotes that the cost for the mode of delivery and tiered distance is computed as the cost defined in the Cost field times the distance between the delivery address & the locations

-   Cost: This field is used to define the Cost value that is used in conjunction with the Calculation type to compute the cost for a mode of delivery

 **Notes:**

-   When defining tiered distances, system will validate that there are no missing or overlapping distances

-   Distance type used for a Mode of delivery has to be the same across all the tiered distances

The below section explains how each of the combination of the Cost type & Other cost type for non-shipping cost can be set-up and how they are used by the DOM solver:

1.  **Cost Type – Other, Other cost type – Sales order**

    This combination of Cost type and Other cost type is used to define non-shipping costs at a sales order level

    The below are the explanation of the fields that needs to be set-up for this combination of configuration:

-   Cost factor: This is the unique identifier id for the Cost factor

-   Description: This is the name / description of the cost factor

-   Start date / End date: These fields can be used to restrict the cost factor for a given date range. If left blank it would mean that the cost factors are valid for an indefinite period

-   Active: This field is used to mark whether the cost factor is active or not. Only active cost factors that are associated to the fulfillment profile is considered by DOM

-   Cost: This field is used to define the Cost value for a non-shipping cost at a sales order level

2.  **Cost Type – Other, Other cost type – Sales order**

    This combination of Cost type and Other cost type is used to define non-shipping costs at a sales order line level

    The below are the explanation of the fields that needs to be set-up for this combination of configuration:

-   Cost factor: This is the unique identifier id for the Cost factor

-   Description: This is the name / description of the cost factor

-   Start date / End date: These fields can be used to restrict the cost factor for a given date range. If left blank it would mean that the cost factors are valid for an indefinite period

-   Active: This field is used to mark whether the cost factor is active or not. Only active cost factors that are associated to the fulfillment profile is considered by DOM

-   Cost: This field is used to define the Cost value for a non-shipping cost at a sales order line level

3.  **Cost Type – Other, Other cost type – Location**

    This combination of Cost type and Other cost type is used to define non-shipping costs for a group of locations or individual location

    The below are the explanation of the fields that needs to be set-up for this combination of configuration:

-   Cost factor: This is the unique identifier id for the Cost factor

-   Description: This is the name / description of the cost factor

-   Start date / End date: These fields can be used to restrict the cost factor for a given date range. If left blank it would mean that the cost factors are valid for an indefinite period

-   Active: This field is used to mark whether the cost factor is active or not. Only active cost factors that are associated to the fulfillment profile is considered by DOM

-   Fulfillment group: The group of locations for which the non-shipping cost is defined for.

-   Fulfillment location: The location for which the non-shipping cost is defined for. Configuration of fulfillment group and fulfillment location on the same line for location-based calculation criteria is not supported

-   Cost: This field is used to define the Cost value for a non-shipping cost at a fulfillment group or fulfillment location level.



