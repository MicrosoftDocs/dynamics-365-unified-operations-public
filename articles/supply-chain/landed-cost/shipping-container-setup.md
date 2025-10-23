---
title: Shipping containers
description: Learn how to set up shipping containers for the Landed cost module, including an outline on setting up container types and a table defining various fields.
author: prasungoel 
ms.author: prasungoel 
ms.reviewer: kamaybac
ms.search.form: ITMContainerTypeTable, ITMContainerTable, ITMContainerUnitTypeTable, ITMRefrigerationTypeTable, ITMContainersListPage, ITMContainers
ms.topic: how-to
ms.date: 09/19/2025
ms.custom: 
  - bap-template
---

# Shipping container setup

[!include [banner](../../includes/banner.md)]

This article describes how to set up shipping containers for the **Landed cost** module.

## <a id="shipping-container-types"></a>Set up shipping container types

Shipping container types define the types of shipping containers that you can use during shipping and voyages.

To work with the shipping container types, go to **Landed cost** \> **Containers setup** \> **Shipping container types**. You can view, add, and remove records for your container types. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Shipping container type | Enter a unique identification name or number for the shipping container type. |
| Description | Enter a description of the shipping container type. |
| Volume | Enter the maximum volume for shipping containers of this type. |
| Weight | Enter the maximum weight for shipping containers of this type. |
| Returnable | Specify whether shipping containers of this type can be returned to the vendor after they're used during a voyage. If you set this option to *Yes*, additional costs might apply for the return of shipping containers of this type to the port of origin. |

## Set up shipping containers

Use shipping container records to identify each container that you use during voyages. When you create a voyage, you can select a specific container for it from the list of all the shipping container records that you define. This feature is especially useful if your company owns its own shipping containers.

You don't need to enter shipping container numbers for shipping containers that you use only one time. Instead, you can add the shipping container number when you create a voyage.

Shipping container records are used only in Landed cost. They aren't available in the standard **Transportation management** module (TMS).

To work with shipping containers, go to **Landed cost** \> **Containers setup** \> **Shipping containers**. There, you can view, add, and remove records for your shipping containers. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Shipping container | Enter a unique identification name or number for the shipping container. |
| Shipping container type | Select the type of shipping container. Learn more in the [Set up shipping container types](#shipping-container-types) section earlier in this article. |

> [!NOTE]
>
> - The shipping container setup is optional. Typically, you'll use it only if your company owns its own shipping containers or often reuses the same shipping containers.
> - No check digits are calculated for shipping container numbers.

## <a name="unit-types"></a>Set up unit types

Unit types provide extra groupings and identification methods for shipping containers. Use the unit type to identify the type of container that goods are packaged in, such as pallets or drums. Select a unit type when you set up a container on the **All shipping containers** page.

Unit types are used only in Landed cost. They aren't available in TMS.

To work with unit types, go to **Landed cost** \> **Containers setup** \> **Unit types**. You can view, add, and remove records for your unit types. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Unit type | Enter a unique identification name or number for the unit type. |
| Description | Enter a description of the unit type. |

## <a name="refrigeration-types"></a>Set up refrigeration types

Refrigeration types provide extra groupings and identification methods for shipping containers, usually refrigerated containers. Select a refrigeration type when you set up a container on the **All shipping containers** page.

To work with refrigeration types, go to **Landed cost** \> **Containers setup** \> **Refrigeration types**. You can view, add, and remove records for your refrigeration types. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Refrigeration type | Enter a unique identification name or number for the refrigeration type. |
| Description | Enter a description of the refrigeration type. |
