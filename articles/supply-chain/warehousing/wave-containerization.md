---
# required metadata

title: Containerization
description: This article describes how to automate the containerization of loads. Automated containerization creates containers and the picking work for shipments when a wave is processed.
author: Mirzaab
ms.date: 03/08/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSWaveTemplateTable, InventLocationIdLookup, WHSContainerType, WHSContainerGroup, WHSContainerizationTable, WHSContainerizationBreak, WHSCreateContainerBreak, WHSContainerStructure, WHSContainerTable, WHSContainerizatonHistory, WHSContainerPackingPolicyChange, WHSManifestShipmentContainers, WHSAllowedContainerTypeGroup, WHSPostMethod, WHSContainerCreateDialog, WHSContainerCloseDiag, WHSContainer
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac

# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2021-03-08
ms.dyn365.ops.version: 10.0.18
---

# Containerization

[!include [banner](../includes/banner.md)]

This article describes how to automate the containerization of loads. Automated containerization creates containers and the picking work for shipments when a wave is processed.

To set up containerization, you must create the following:

- **Container type** ─ Define the physical characteristics of the containers. Use container types to pack inventory items into a specific type and size of packaging, such as bins or pallets.
- **Container groups** ─ Create groups of container types that are similar. For example, a container group can include container types that have similar size dimensions. A container group specifies the sequence in which containers are packed, and the fill percentage of each container.
- **Container build template** ─ Create templates that define rules for containerization. For example, rules for mixing inventory and other packing strategies.
- **Wave templates** – Set up one or more wave templates to create the picking work for containerization.

## Create wave templates for containerization

You must set up one or more shipping wave templates for containerization. Wave templates include criteria that determine the following:

- How to process waves. This can be either manual or automatic.
- How to create picking work. This is determined by the wave methods. The wave template must include the **containerization** method.
- How to match items or allocation lines with a wave.

For more information, see [Wave templates](wave-templates.md).

## Create container types

Use container types to create descriptions of containers, including maximum values for physical size dimensions and weight capacity. When a containerized wave is processed, the containers are created based on the container type information.

To set up a container type, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Containers** \> **Container type**.
1. Select **New** to create a new container type.
1. Enter a unique identifier (ID) and description for the container type.
1. In the **Tare weight** field, enter the actual or estimated weight of the container.
1. In the **Maximum weight** field, enter the maximum weight that the container can hold.
1. In the **Containerization maximum volume**, **Containerization maximum length**, **Containerization maximum width**, and **Containerization maximum height** fields, specify the physical dimensions of the container.

    > [!NOTE]
    > The values for length and width are interchangeable. This means that you can rotate items laterally, or on the x-axis, if needed. For example, if the length is 2 feet, and the width is 1 foot, you can change the length to 1 foot and the width to 2 feet. Note that this does not apply to the height dimension. You cannot change the height value to rotate an item vertically.

1. Select custom attribute values for the container in the fields for attributes. Attributes are custom values that are used to filter or sort items based on a value that is otherwise not available. For example, if you want to pack items for a particular customer, you can create an attribute for the customer name. You create attributes on the **Container attributes** page.

## Create container groups

You can set up logical groups of container types. For each group, you can specify the sequence in which to pack the containers and the percentage of the containers to fill. The size dimensions of the item determine whether it will fit in a container. The container that is closest to the size dimensions of the item is used. If you have multiple container types in a group, we recommend that you arrange the sequence by size, so that the largest container is first, number 1 in the sequence, and the smallest container is last.

To set up a container group, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Containers** \> **Container groups**.
1. Select **New** to create a container group.
1. Enter a unique ID and description for the container group.
1. On the **Details** FastTab, select **New** to add a container type to the group.
1. In the **Container type** field, select a container type.
1. Select **Move up** or **Move down** to specify the sequence in which the container types are packed.

## Create container build templates

You can set up rules for the containerization process, such as inventory mixing rules and other packing strategies. For example, you can set up a rule so that workers cannot pack allocation lines that represent sales orders from different customers in the same container.

To set up a container build template, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Containers** \> **Container build template**.
1. Create a new container build template.
1. In the **Containerization name** and **Sequence number** fields, enter the name of the containerization template and the order that is matched to allocation lines.

    > [!NOTE]
    > The system will apply the first template that the allocation line meets the query criteria for. Therefore, put the template with the most specific criteria at the top of the list. The broader the criteria, the more likely that an allocation line will meet the criteria. This could lead to lines being assigned to the wrong container. If needed, you can select **Move up** or **Move down** to change the sequence of templates.

1. In the **Container group ID** field, select the container group from which to create containers.
1. In the **Base query types** field, select the query type that will determine what to pack and what to base the filter query on. The following options are available:

      - **Sales allocation line** ─ Pack allocation lines that are created for sales orders.
      - **Transfer allocation line** ─ Pack allocation lines that are created for transfer orders.
      - **Container** ─ Pack a container that was already created by the containerization process. For example, this is used for nesting containers.
      - **Outbound order allocation line** ─ Pack allocation lines that are created for [outbound shipment orders](wms-only-mode-exchange-data.md#inbound-outbound-shipment-order-messages).

        > [!NOTE]
        > To use nesting containers, you must make the containerization method repeatable. For more information, see [Wave templates](wave-templates.md).

1. On the **General** FastTab, in the **Wave step code** field, enter the unique identifier of the wave process method that links the container build template to steps in a wave template.
1. Select the **Allow split picks** check box to allow workers to pack items from a work order in separate containers. This requires that the entire quantity fits in the container. The largest unit of measure in the allocation line is always used.
1. In the **Pack by unit** field, select the unit of measure that will represent the container. For example, you can indicate that a case is a container. If you pack by the unit of measure, you cannot also specify a container group because the unit of measure is the container.
1. In the **Container packing strategy** field, select the packing strategy to use. The following options are available:

    > [!NOTE]
    > The strategy applies only to sales allocation lines and transfer allocation lines.

      - **Pack into all open containers** – The system evaluates whether the allocation line will fit in any container that was created during the containerization cycle.
      - **Pack into current container only** – The system only evaluates whether the allocation line will fit in the most recently created container.

    For more information and examples that show how to work with container packing strategies, see [Container packing strategies](container-packing-strategy-overview.md).

1. To set up rules for packing allocation lines in containers, select **Mixing Logic Breaks**. For example, you can create a rule that will allow workers to pack allocation lines for two different items in the same container. To define a mixing rule, follow these steps:

    1. In the **Mixing Logic Breaks** page, select **New**.
    1. In the **Table** field, select the table that contains the field to use as a criterion for the mixing logic break.
    1. In the **Field Select** field, select the field to use as a criterion for the mixing logic break.
    1. Repeat these steps until you have added all of the criteria for the mixing logic break.

    > [!NOTE]
    > If you use mixing logic, we recommend that you sort by the same fields in the filter criteria query. This will reduce the number of containers that are created.
