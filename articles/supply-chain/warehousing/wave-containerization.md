---
title: Containerization
description: Learn how to automate the containerization of loads, which create containers and the picking work for shipments when a wave is processed.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSWaveTemplateTable, InventLocationIdLookup, WHSContainerType, WHSContainerGroup, WHSContainerizationTable, WHSContainerizationBreak, WHSCreateContainerBreak, WHSContainerStructure, WHSContainerTable, WHSContainerizatonHistory, WHSContainerPackingPolicyChange, WHSManifestShipmentContainers, WHSAllowedContainerTypeGroup, WHSPostMethod, WHSContainerCreateDialog, WHSContainerCloseDiag, WHSContainer
ms.topic: how-to
ms.date: 10/08/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Containerization

[!INCLUDE [banner](../includes/banner.md)]

Automated containerization creates containers and picking work for shipments when a wave is processed. Instead of having workers decide how to pack each shipment, the system divides the allocated quantities into containers that it selects for you. It applies the container capacities, packing strategies, and mixing rules that you define, and then creates picking work against those containers.

> [!NOTE]
> By default, the wave containerization process automatically closes a container as the final step of work execution. Therefore, the container arrives at the packing station already closed, and you can't weigh, manifest, or label it there as an individual container. You can change this behavior so that the container is converted into a packing station container and left open when you put work to a packing station. Learn more in [Convert work containers at a packing station](packing-work.md#convert-containers-at-packing-station).

To set up containerization, you must create the following components:

- **Wave templates** – Set up one or more wave templates to create the picking work for containerization.
- **Container types** – Define the physical characteristics of the containers. Use container types to pack inventory items into a specific type and size of packaging, such as bins or pallets.
- **Container groups** – Create groups of container types that are similar. For example, a container group can include container types that have similar size dimensions. A container group specifies the sequence in which containers are packed, and the utilization percentage of each container.
- **Container build templates** – Create templates that define which allocation lines to pack and how to pack them. A template combines a filter query, a container group, a packing strategy, and optional mixing rules.

## Create wave templates for containerization

Set up one or more shipping wave templates for containerization. Wave templates include criteria that determine the following:

- How to process waves. You can choose either manual or automatic processing.
- How to create picking work. This process is determined by the wave methods. The wave template must include the *Containerization* method.
- How to match items or allocation lines with a wave.

Learn more in [Wave templates](wave-templates.md).

## Create container types

A container type describes a reusable physical package, such as a carton, bin, or pallet. When a containerized wave is processed, the system creates containers that are based on the container types that you define here.

Each container type stores two separate sets of measurements:

- The values in the **Maximums** section define the capacity that containerization works with. The packing strategies use these values, together with **Maximum net weight**, to decide whether an allocation line fits.
- The values in the **Container dimensions** section describe the outside of the container. The system uses them to calculate how much space a packed container occupies, such as when the container is nested inside another container or loaded onto a shipment.

To set up a container type, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Containers** > **Container types**.
1. On the Action Pane, select **New** to create a new container type.
1. Enter a unique identifier (ID) and description for the new container type.
1. On the **General** FastTab, in the **Weight** section, set the following fields:

    - **Tare weight** – Enter the actual or estimated weight of the empty container.
    - **Maximum net weight** – Enter the maximum weight of the contents that the container can hold. This value doesn't include the tare weight.

1. In the **Maximums** section, set the following fields to define the capacity that containerization uses:

    - **Volume** – Enter the maximum volume that can be packed into the container.
    - **Length**, **Width**, and **Height** – Enter the maximum dimensions of the space that's available inside the container.

    > [!NOTE]
    > For the *Pack into all open containers* and *Pack into current container only* strategies, the values for length and width are interchangeable. This interchangeability means that items can be rotated laterally, or on the x-axis, if needed. For example, if the length is 2 feet, and the width is 1 foot, you can change the length to 1 foot and the width to 2 feet. The interchangeability doesn't apply to the height dimension. You can't change the height value to rotate an item vertically. The *Optimized 3D packing* strategy behaves differently. It can rotate each unit into any of its six possible orientations, including orientations that stand the unit on end. Learn more in [Optimized 3D packing](#optimized-3d-packing).

1. In the **Container dimensions** section, set the following fields to describe the container itself:

    - **Container length**, **Container width**, **Container height**, and **Container volume** – Enter the outside measurements of the container.
    - **Flexible volume dimensions** – Set this option to *Yes* if the volume depends on the container volume plus the inventory that's put into the container. Set it to *No* if the volume is considered fixed and doesn't depend on the inventory that's put into the container. This setting doesn't affect existing containerization processes.
    - **Unit** – Select the unit of measure that the container dimensions are expressed in.

1. In the **Attributes** section, select custom attribute values for the container. Attributes are custom values that help to filter or sort items based on a value that isn't otherwise available. For example, if you want to pack items for a particular customer, create an attribute for the customer name. Create attributes on the **Container attributes** page.
1. On the Action Pane, select **Save**.

## Create container groups

A container build template can create containers only from the container types that belong to the container group that it points to. Set up a container group for each set of container types that the system can choose among.

For each group, specify the sequence in which to pack the containers and the percentage of each container to fill. For the *Pack into all open containers* and *Pack into current container only* strategies, the size dimensions of the item determine whether it fits in a container, and the container that is closest to the size dimensions of the item is used. If you have multiple container types in a group, arrange the sequence by size, so that the largest container is first, number 1 in the sequence, and the smallest container is last.

To set up a container group, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Containers** > **Container groups**.
1. On the Action Pane, select **New** to create a container group.
1. Enter a unique ID and description for the new container group.
1. On the **Details** FastTab toolbar, select **New** to add a new container type to the group.
1. For the new line, set the following fields:

    - **Container type** – Select a container type to include in the group.
    - **Container utilization percentage** – Enter the percentage of the container that the system is allowed to use. The default value is *100*, and the value must be greater than 0 and no more than 100.

1. Add a row for each other container type that you want to include in the group.
1. On the **Details** FastTab toolbar, select **Move up** or **Move down** to specify the sequence in which the container types are packed.
1. On the Action Pane, select **Save**.

## Create container build templates

A container build template controls which allocation lines are containerized and how they're packed. Each template combines the following elements:

- A *filter query* that selects the allocation lines or containers that the template applies to. The **Base query types** field sets the table that the query runs against, and the **Edit query** button lets you refine the query with your own ranges and sorting.
- A *container group* that provides the container types that the system can create.
- A *packing strategy* that determines how the system fills those containers.
- Optional *container mixing constraints* that prevent unrelated allocation lines from sharing a container. For example, you can set up a constraint so that workers can't pack allocation lines that represent sales orders from different customers in the same container.

Templates are evaluated in sequence. For each allocation line, the system applies the first template whose query the line matches.

To set up a container build template, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Containers** > **Container build templates**.
1. On the Action Pane, select **New** to create a new container build template.
1. In the **Container template ID** field, enter a name for the template. You can set this value only when you create the template.
1. The **Sequence number** defaults to the next available integer. Because the system applies the first template that the allocation line matches, put the template that has the most specific criteria at the top of the list. The broader the criteria, the more likely that an allocation line meets the criteria. This condition could lead to lines being assigned to the wrong container. On the Action Pane, select **Move up** or **Move down** to change the position of a selected template in the sequence. On the Action Pane, select **Reset sequence** to clean up and align the **Sequence number** values to match the displayed order if necessary.
1. In the **Container group ID** field, select the container group from which to create containers.
1. In the **Base query types** field, select the query type that determines what to pack and what to base the filter query on. The following options are available:

    - *Sales allocation line* – Pack allocation lines that are created for sales orders.
    - *Transfer allocation line* – Pack allocation lines that are created for transfer orders.
    - *Container* – Pack a container that the containerization process already created. For example, use this option for nested containers.
    - *Outbound order allocation line* – Pack allocation lines that are created for [outbound shipment orders](wms-only-mode-exchange-data.md#inbound-outbound-shipment-order-messages).

    > [!NOTE]
    > To use nesting containers, you must make the containerization method repeatable. Learn more in [Wave templates](wave-templates.md).

    > [!IMPORTANT]
    > When you change **Base query types**, the system asks you to confirm, and then it resets the filter query to the default query for the new type. Any ranges or sorting that you previously defined are lost.

1. On the Action Pane, select **Edit query** to refine the filter query that selects the allocation lines or containers for the template. In the standard query editor, you can add ranges to narrow the selection and add sorting to control the order in which lines are packed. The current ranges and sorting are shown in the **Query (range)** and **Query (sorting)** FactBoxes.
1. In the **Wave step code** field, select the wave process method that links the container build template to steps in a wave template. This field is required.
1. Select the **Allow split picks** check box to allow workers to pack items from a work order in separate containers. This condition requires that the entire quantity fits in the container. The largest unit of measure in the allocation line is always used.
1. Select the **Pack by directive unit** check box if you want location directives to control which unit is used for packing. Clear this check box to always use the inventory unit.

    > [!NOTE]
    > You can't combine **Pack by directive unit** with a container group or a packing strategy. While this check box is selected, the **Container group ID**, **Allow split picks**, and **Container packing strategy** fields are unavailable, and the system prevents you from setting both **Pack by directive unit** and **Container group ID**.

1. In the **Container packing strategy** field, select the packing strategy to use. The following options are available:

    - *Pack into all open containers* – The system evaluates whether the allocation line fits in any container that it creates during the containerization cycle.
    - *Pack into current container only* – The system only evaluates whether the allocation line fits in the most recently created container.
    - *Optimized 3D packing* – The system tracks the three-dimensional position of each unit in a container. It evaluates placements across the container types in the selected container group while respecting dimensions and maximum net weight. This option is only available if you have enabled the optimized 3D packing feature. Learn more in [Optimized 3D packing](#optimized-3d-packing).

    The first two strategies apply only to sales allocation lines and transfer allocation lines. Learn more, and review examples that use these strategies, in [Container packing strategies](container-packing-strategy-overview.md).

1. If you set **Container packing strategy** to *Optimized 3D packing*, select the **Save packing layout** check box if you want the containerization process to save a visualization of the container packing layout as JSON code in the container table. This option is only available if you have enabled the optimized 3D packing feature. Learn more in [Optimized 3D packing](#optimized-3d-packing).
1. To set up rules that prevent unrelated allocation lines from sharing a container, on the Action Pane, select **Container mixing constraints**, and then follow these steps:

    1. On the **Container mixing constraints** page, select **New**.
    1. In the **Table** field, select the table that contains the field to use as a criterion.
    1. In the **Field Select** field, select the field to use as a criterion.
    1. Repeat these steps until you add all of the criteria.

    The system starts a new container whenever the value of any of these fields changes. For example, if you add the customer account field, each container holds lines for only one customer.

    > [!NOTE]
    > If you use container mixing constraints, sort by the same fields in the filter criteria query. This action reduces the number of containers that the system creates.

1. On the Action Pane, select **Save**.

<a name="optimized-3d-packing"></a>

## Optimized 3D packing (production ready preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]
<!-- KFM: Preview until further notice -->

The *Optimized 3D packing* strategy uses the physical dimensions of each unit to track its position in a container. Instead of checking only whether the remaining volume is sufficient, the packing engine evaluates candidate positions against the units that it already placed, and it can rotate each unit into any of its six orientations to find a valid placement. It tries several container types from the container group and keeps the result that uses the space most efficiently, while respecting the **Maximum net weight** of the container type.

Because the engine works from real dimensions, it typically produces fewer and fuller containers than the other strategies. It also requires more complete master data. Every unit that it packs must have physical dimensions for the directive unit that work creation uses.

[!INCLUDE [production-ready-preview-dynamics365](~/../shared-content/shared/preview-includes/production-ready-preview-dynamics365.md)]

### Prerequisites

To use optimized 3D packing, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.49 or later.
- The feature named *(Production ready preview) Optimized 3D packing containerization algorithm* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- You must define the physical dimensions and a gross weight for each item's unit that you use as the directive unit during work creation.
- You must specify a **Maximum net weight** value, and **Length**, **Width**, and **Height** values in the **Maximums** section, for each container type in the container group.

> [!IMPORTANT]
> If an item doesn't have physical dimensions for its directive unit, the system skips the whole allocation line and adds a warning to the containerization history. The line isn't packed into a container. The same behavior applies to a container that has no dimensions when you use nesting.

### Set up optimized 3D packing

Configure the optimized strategy on the container build template that the wave uses. You can also save a packing layout to review how the algorithm placed each unit.

1. Go to **Warehouse management** > **Setup** > **Containers** > **Container build templates**.
1. Select a container build template to update, or create a new one.
1. Make the following settings for your selected or new template:
    - **Pack by directive unit** – Clear this check box. The system doesn't let you combine this setting with a container group, and it makes the **Container group ID**, **Allow split picks**, and **Container packing strategy** fields unavailable while it's selected.
    - **Container group ID** – Select the container group that contains the container types that the algorithm can choose among.
    - **Allow split picks** – Select this check box so the algorithm can divide work lines across multiple containers.
    - **Container packing strategy** – Select *Optimized 3D packing*.
    - **Save packing layout** – Select this check box if you want the containerization process to save the container packing layout as JSON code in the container table. This setting lets you review a visualization of the packing result later.

    Make other settings as described previously in this article.

1. On the Action Pane, select **Save**.

The optimized strategy uses the template query and container mixing constraints to separate allocation lines before it packs each shipment.

The **Container utilization percentage** setting on each container group line reserves space in the container. The system applies it to the container type in two ways:

- It reduces each of the **Length**, **Width**, and **Height** values so that the usable *volume* drops by the percentage that you specify. For example, a value of *80* leaves 80 percent of the original volume available, and each dimension is reduced to about 93 percent of its original value.
- It reduces the **Maximum net weight** value in direct proportion. For example, a value of *80* leaves 80 percent of the original maximum net weight available.

In addition to the various order query types, you can also use the optimized strategy when **Base query types** is set to *Container*. In this case, the algorithm uses the dimensions and calculated weight of each unnested container to place it in a parent container. Container mixing constraints don't apply to this nesting scenario.

### Review optimized packing results

After the wave runs, review the containerization history for packing diagnostics and warnings. For each containerization run, the history records the algorithm and the winning strategy that the engine selected, how many items it packed out of the total that it evaluated, a volume utilization percentage, and the processing time in milliseconds. It also records a line for each container that the strategy created.

To review the history, go to **Warehouse management** > **Packing and containerization** > **Containerization history**.

> [!NOTE]
>
> - The system records the containerization history only when **Create containerization history log** is set to *Yes* on the **Warehouse management parameters** page.
> - The reported volume utilization describes the first container that the engine packed in the run. It isn't an average across all the containers that the run created.

If you selected **Save packing layout**, follow these steps to review the three-dimensional layout:

1. Go to **Warehouse management** > **Packing and containerization** > **Containers**.
1. Open a container that the optimized strategy created.
1. Select the **Packing layout** tab. This tab shows the container type, its dimensions, and the position of each packed unit.

    > [!NOTE]
    > The **Packing layout** tab appears only while a saved layout exists for the selected container. The system deletes the saved layout when the container is closed.

## Related information

- [Wave templates](wave-templates.md)
- [Container packing strategies](container-packing-strategy-overview.md)
- [Wave creation and processing](wave-processing.md)
- [Packing work for packing outbound containers and processing shipments](packing-work.md)
