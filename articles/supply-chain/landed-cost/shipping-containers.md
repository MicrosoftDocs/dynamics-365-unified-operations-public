---
# required metadata

title: Shipping containers
description: Shipping container types define the available types of shipping containers that are used during shipping and voyages.
author: mkirknel
manager: tfehr
ms.date: 12/09/2020
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
ms.author: mkirknel
ms.search.validFrom: 2020-12-09
ms.dyn365.ops.version: Release 10.0.17
---

# Shipping containers

## Shipping container types

Shipping container types define the available types of shipping containers that are used during shipping and voyages.

To work with the shipping container types, go to **Landed cost \> Containers setup \> Shipping container types** and make the settings described in the following table.

| **Setting** | **Description** |
| --- | --- |
| **Shipping container type** | The unique identification name of the type of shipping container used. |
| **Description** | The description of the shipping container type. |
| **Volume** | The volume allowed within the shipping container type. |
| **Weight** | The maximum weight allowed within the shipping container type. |
| **Returnable** | Is the container returnable to the vendor after being used in a voyage? If this is set to &#39;Yes&#39;, additional costs may apply for the return of shipping containers of this type to the port of origin. |

## Shipping containers

Use shipping container records to identify the specific containers that a company uses during voyages. When creating a voyage, you can select a specific container for that voyage using a drop-down list that shows the shipping container records that you have defined here. This feature is especially useful if your company owns its own shipping containers. You don&#39;t need to enter shipping container numbers for shipping containers that will be used only once; instead, the shipping container number can be added at the time of voyage creation. The drop-down list selection is not required to create a shipping container during voyage creation.

Shipping container records are only used by Landed cost and aren&#39;t available to the standard transportation management module.

To work with shipping containers, go to **Landed cost \> Containers setup \> Shipping containers**. Here, you can view, add, and remove records for each of your shipping containers. The following table describes the settings available for each container.

| **Setting** | **Description** |
| --- | --- |
| **Shipping container** | Enter the unique identification name/number of the shipping container. |
| **Shipping container type** | Select the type of shipping container that it is. See also [Shipping container types](#_Shipping_container_types). |

> [!NOTE]
>
> - The shipping container setup is optional. You will normally use it only if your company owns its own shipping containers or re-uses the same ones often.
> - No check digits are calculated for container numbers.

## Unit types

Use unit types an additional grouping and identification method against a container. The unit type is typically used to identify the type of container the goods are packaged in, such as pallets or drums. You can select a unit type when setting up a container on the **All shipping containers** page.

Unit types are only used in Landed cost and aren&#39;t available to the standard transportation management module.

To work with unit types, go to **Landed cost \> Containers setup \> Unit types**. Here, you can view, add, and remove records for each of your unit types. The following table describes the settings available for each type.

| **Setting** | **Description** |
| --- | --- |
| **Unit type** | Enter a unique identification name/number of the unit type. |
| **Description** | Enter a description of the unit type. |

## Refrigeration types

Refrigeration types are used as an additional grouping and identification method against a container, normally for refrigerated containers. You can select a refrigeration type when setting up a container on the **All shipping containers** page.

To work with refrigeration types, go to **Landed cost \> Containers setup \> Refrigeration types**. Here, you can view, add, and remove records for each of your refrigeration types. The following table describes the settings available for each type.

| **Field Name** | **Field Description** |
| --- | --- |
| **Refrigeration type** | The unique identification name/number of the refrigeration type. |
| **Description** | The description of the refrigeration type. |