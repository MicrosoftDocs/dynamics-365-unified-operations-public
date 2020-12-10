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

## <a name="Shipping-container-types"></a>Set up shipping container types

Shipping container types define the types of shipping containers available for use during shipping and voyages.

To work with the shipping container types, go to **Landed cost \> Containers setup \> Shipping container types**. Here, you can view, add, and remove records for each of your container types. The following table describes the settings available for each container type.


| **Setting** | **Description** |
| --- | --- |
| **Shipping container type** | Enter a unique identification name/number for the shipping container type. |
| **Description** | Enter the unique identification name/number of the container type. |
| **Volume** | Enter the maximum volume allowed within the shipping container type. |
| **Weight** | Enter the maximum weight allowed within the shipping container type. |
| **Returnable** | Choose whether or not the container can be returned to the vendor after being used in a voyage. If this is set to *Yes*, additional costs may apply for the return of shipping containers of this type to the port of origin. |

## Set up shipping containers

Use shipping container records to identify each specific container that you use during voyages. When creating a voyage, you can select a specific container for that voyage using a drop-down list that shows the shipping container records that you have defined here. This feature is especially useful if your company owns its own shipping containers. You don't need to enter shipping container numbers for shipping containers that will be used only once; instead, you can add the shipping container number when you create a voyage.

Shipping container records are only used by Landed cost and aren't available to the standard transportation management module (TMS).

To work with shipping containers, go to **Landed cost \> Containers setup \> Shipping containers**. Here, you can view, add, and remove records for each of your shipping containers. The following table describes the settings available for each container.

| **Setting** | **Description** |
| --- | --- |
| **Shipping container** | Enter a unique identification name/number for the shipping container. |
| **Shipping container type** | Select the type of shipping container that it is. See also [Set up shipping container types](#Shipping-container-types). |

> [!NOTE]
>
> - The shipping container setup is optional. You will normally use it only if your company owns its own shipping containers or re-uses the same ones often.
> - No check digits are calculated for container numbers.

## Set up unit types

Unit types establish additional groupings and identification methods for containers. The unit type is typically used to identify the type of container the goods are packaged in, such as pallets or drums. You can select a unit type when setting up a container on the **All shipping containers** page.

Unit types are only used in Landed cost and aren't available to TMS.

To work with unit types, go to **Landed cost \> Containers setup \> Unit types**. Here, you can view, add, and remove records for each of your unit types. The following table describes the settings available for each type.

| **Setting** | **Description** |
| --- | --- |
| **Unit type** | Enter a unique identification name/number for the unit type. |
| **Description** | Enter a description of the unit type. |

## Set up refrigeration types

Refrigeration types establish additional groupings and identification methods for containers (normally for refrigerated containers). You can select a refrigeration type when setting up a container on the **All shipping containers** page.

To work with refrigeration types, go to **Landed cost \> Containers setup \> Refrigeration types**. Here, you can view, add, and remove records for each of your refrigeration types. The following table describes the settings available for each type.

| **Setting** | **Description** |
| --- | --- |
| **Refrigeration type** |  Enter a unique identification name/number for the refrigeration type. |
| **Description** | The description of the refrigeration type.|