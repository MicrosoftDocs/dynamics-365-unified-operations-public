---
# required metadata

title: Shipping containers
description: This topic describes how to set up shipping containers for the Landed cost module.
author: Weijiesa
ms.date: 12/09/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ITMContainerTypeTable, ITMContainerTable, ITMContainerUnitTypeTable, ITMRefrigerationTypeTable, ITMContainersListPage, ITMContainers
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: weijiesa
ms.search.validFrom: 2020-12-09
ms.dyn365.ops.version: 10.0.17
---

# Shipping container setup

[!include [banner](../../includes/banner.md)]

This topic describes how to set up shipping containers for the **Landed cost** module.

## <a id="shipping-container-types"></a>Set up shipping container types

Shipping container types define the types of shipping containers that are available for use during shipping and voyages.

To work with the shipping container types, go to **Landed cost \> Containers setup \> Shipping container types**. There, you can view, add, and remove records for your container types. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Shipping container type | Enter a unique identification name/number for the shipping container type. |
| Description | Enter a description of the shipping container type. |
| Volume | Enter the maximum volume that is allowed in shipping containers of this type. |
| Weight | Enter the maximum weight that is allowed in shipping containers of this type. |
| Returnable | Specify whether shipping containers of this type can be returned to the vendor after they are used during a voyage. If this option is set to *Yes*, additional costs might apply for the return of shipping containers of this type to the port of origin. |

## Set up shipping containers

You use shipping container records to identify each container that you use during voyages. When you create a voyage, you can select a specific container for it in the list of all the shipping container records that you've defined here. This feature is especially useful if your company owns its own shipping containers.

You don't have to enter shipping container numbers for shipping containers that will be used only one time. Instead, you can add the shipping container number when you create a voyage.

Shipping container records are used only in Landed cost. They aren't available in the standard **Transportation management** module (TMS).

To work with shipping containers, go to **Landed cost \> Containers setup \> Shipping containers**. There, you can view, add, and remove records your shipping containers. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Shipping container | Enter a unique identification name/number for the shipping container. |
| Shipping container type | Select the type of shipping container. For more information, see the [Set up shipping container types](#shipping-container-types) section earlier in this topic. |

> [!NOTE]
> - The shipping container setup is optional. Typically, you will use it only if your company owns its own shipping containers or often reuses the same shipping containers.
> - No check digits are calculated for shipping container numbers.

## <a name="unit-types"></a>Set up unit types

Unit types establish additional groupings and identification methods for shipping containers. The unit type is typically used to identify the type of container that goods are packaged in, such as pallets or drums. You can select a unit type when you set up a container on the **All shipping containers** page.

Unit types are used only in Landed cost. They aren't available in TMS.

To work with unit types, go to **Landed cost \> Containers setup \> Unit types**. There, you can view, add, and remove records for your unit types. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Unit type | Enter a unique identification name/number for the unit type. |
| Description | Enter a description of the unit type. |

## <a name="refrigeration-types"></a>Set up refrigeration types

Refrigeration types establish additional groupings and identification methods for shipping containers (usually refrigerated containers). You can select a refrigeration type when you set up a container on the **All shipping containers** page.

To work with refrigeration types, go to **Landed cost \> Containers setup \> Refrigeration types**. There, you can view, add, and remove records for your refrigeration types. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Refrigeration type | Enter a unique identification name/number for the refrigeration type. |
| Description | Enter a description of the refrigeration type. |
