---
# required metadata

title: Wave creation and processing
description: This topic describes how to create, process, and release a wave to create picking work for a load, shipment, production order, or kanban order.
author: Mirzaab
manager: tfehr
ms.date: 03/08/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  WHSWaveTemplateTable, WHSParameters, whswavetablecreatenew, WHSWaveTable, WHSWaveAttributes, WHSKanbanWaveTable, WHSWaveTableListPage, WHSKanbanWaveTableListPage
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2021-03-08
ms.dyn365.ops.version: Release 10.0.18
---

# Wave creation and processing

[!include [banner](../includes/banner.md)]

This topic describes how to create, process, and release a wave to create picking work for a load, shipment, production order, or kanban order. You can create waves for the following types of orders:

- **Sales orders** – Use shipping waves to include lines from sales orders. When a sales order is released to the warehouse, the sales order lines can be included in the wave.
- **Production orders** – Use production waves to include lines from the bill of materials (BOM) for a product.
- **Kanban orders** – Kanban waves include picking list lines from kanban orders.

For sales orders and kanban orders, inventory must be reserved before the order is released to the warehouse. Otherwise, the items or allocation lines can't be processed in a wave. However, production orders are slightly more flexible. For production orders, you can choose either of the following options:

- Require that all materials are reserved before an order can be released to the warehouse.
- Allow production orders to be released to the warehouse even though all materials can't be reserved. If you select this option, you must manually repeat the release to warehouse process when the additional materials become available. For example, this is useful if you have the materials that you need to start a production, and can wait until the additional materials become available.

You can specify which of these production order options to use by default using the **Requirement for material reservation** field on the **Production control parameters** page. However, you can change the setting for each specific production order as needed. More information: [Warehouse parameters for wave processing](wave-warehouse-parameters.md)

## Creation and process a wave

The following diagram shows the flow for how shipping waves are created, processed, and released. The numbers correspond to the sections later in this section.

![Process for creating a wave](media/wave-processing-diagram.png "Process for creating a wave")

### Prerequisites

Before you start, a wave template must be available for the type of wave you want to create (shipping, production, or kanban). The wave template establishes may settings for how the wave will be generated and processed, including which steps must be done manually and which are done automatically. For more information, see [Wave templates](wave-templates.md).

### Step 1: Create a wave

#### Automatically create waves based on warehouse and order type

To create waves automatically, set up a [Wave templates](wave-templates.md) that apply for each relevant order type and warehouse and make sure each has its **Automate wave creation** option set to *Yes*.

#### Manually create waves

To manually create a wave, follow these steps:

1. Make sure that the relevant [Wave templates](wave-templates.md) aren't set to automatically create a wave for the warehouse and order types where you want to do so manually.
1. Depending on the type of wave to create, do one of the following:

    - Go to **Warehouse management** \> **Common** \> **Waves** \> **Shipment waves** \> **All waves**. On the Action Pane, select **Wave**.
    - Go to **Warehouse management** \> **Common** \> **Waves** \> **Production waves** \> **All production waves**. On the Action Pane, select **Production wave**.
    - Go to **Warehouse management** \> **Common** \> **Waves** \> **Kanban waves** \> **All kanban waves**. On the Action Pane, select **Create wave**.

1. In the **Description** field, enter a short description of the wave. This should indicate what you are processing in the wave.

1. In the **Wave template name** field, select the wave template for the type of wave to create. The wave template contains the wave methods that will perform actions such as creating work for the wave. For example, the wave template for shipping waves can contain methods for creating loads, allocating lines to waves, replenishment, and creating picking work for the wave.

1. If you want to use wave attributes as additional query criteria for the wave, select the attributes in the **Wave attributes** fields.

### Step 2: Specify what to include in a wave

Once a wave has been created, you are ready to start adding content to it.

> [!NOTE]
> If needed, you can add lines to a wave even after it has been processed, provided it has not yet been released.

#### Automatically specify what to include in a wave

To automatically specify what to include in a wave based on the order(s) that created it, make the following settings for each relevant [Wave template](wave-templates.md) that you created in step 1:

<!-- KFM: I need these details. -->

#### Manually specify what to include in a wave

When a wave has been created but not yet released, you can manually specify what to include in it. To add lines to a wave manually:

1. Depending on the type of wave to add lines to, do one of the following:

    - Go to **Warehouse management** \> **Common** \> **Waves** \> **Shipment waves** \> **All waves**. On the Action Pane, select **Wave**.
    - Go to **Warehouse management** \> **Common** \> **Waves** \> **Production waves** \> **All production waves**. On the Action Pane, select **Production wave**.
    - Go to **Warehouse management** \> **Common** \> **Waves** \> **Kanban waves** \> **All kanban waves**. On the Action Pane, select **Create wave**.

1. Select the wave. On the Action Pane, select one of the following:

      - **Maintain shipments**
      - **Maintain productions**
      - **Maintain kanban job picking lists**

1. In the upper part of the window, select the line to add to the wave, and then select **Add to wave**. The line is moved to the **Wave lines** FastTab.

    Repeat this step for each line to add. To add all lines, select **Add all**.

    > [!TIP]
    > For shipment waves, you can quickly find a particular order by selecting a custom filter in the **Wave filter code** field. Wave filter codes contain query criteria for shipments, which are created in the **Wave filters** form. This field is not available for production waves or kanban waves.
    > A green check mark in the **On wave** column indicates that the shipment has been added to the wave.

### Step 3: Process the wave to create the picking work

Once a wave has been created and contains all of its required lines, you are ready to process it to create the corresponding picking work.

#### Automatically process a wave

To automatically process a wave, make the following settings for each relevant [Wave template](wave-templates.md) that you created in step 1:

<!-- KFM: I need these details. -->

#### Manually process a wave

You can process a wave only when the **Wave status** is *Created*. After you process a wave, the **Wave status** will be changed to *Held*.

To manually process a wave that has all of its required content, follow these steps:

1. Depending on the type of wave to process, do one of the following:

    - Select **Warehouse management** \> **Common** \> **Waves** \> **Shipment waves** \> **All waves**. On the Action Pane, select **Wave**.
    - Select **Warehouse management** \> **Common** \> **Waves** \> **Production waves** \> **All production waves**. On the Action Pane, select **Production wave**.
    - Select **Warehouse management** \> **Common** \> **Waves** \> **Kanban waves** \> **All kanban waves**. On the Action Pane, select **Create wave**.

1. Select the wave to process. On the Action Pane, select **Process**.

### Step 4: Release the wave to the warehouse to start picking and packing

You must process a wave before you can release it. When you release the wave, the picking work is available in the warehouse. You can cancel a wave after it is released, and add more lines, but you can't change the lines.

#### Automatically release a wave

To automatically release a wave, make the following settings for each relevant [Wave template](wave-templates.md) that you created in step 1:

<!-- KFM: I need these details. -->

#### Manually release a wave

To release a wave manually, follow these steps:

1. Depending on the type of wave to release, do one of the following:

      - Select **Warehouse management** \> **Common** \> **Waves** \> **Shipment waves** \> **All waves**. On the Action Pane, select **Wave**.
      - Select **Warehouse management** \> **Common** \> **Waves** \> **Production waves** \> **All production waves**. On the Action Pane, select **Production wave**.
      - Select **Warehouse management** \> **Common** \> **Waves** \> **Kanban waves** \> **All kanban waves**. On the Action Pane, select **Create wave**.

1. Select the wave to release. On the Action Pane, select **Release wave**.

## Containerize a wave

<!-- KFM: Give a short intro to what this is and why. Then just link to [Containerization](wave-containerization.md) -->

## Cancel a wave

If needed, you can cancel a wave that has been processed. To cancel a wave, and the picking work that was created, follow these steps:

1. Depending on the type of wave to cancel, do one of the following:

      - Go to **Warehouse management** \> **Common** \> **Waves** \> **Shipment waves** \> **All waves**.
      - Go to **Warehouse management** \> **Common** \> **Waves** \> **Production waves** \> **All production waves**.
      - Go to **Warehouse management** \> **Common** \> **Waves** \> **Kanban waves** \> **All kanban waves**.

1. Select the wave to cancel. On the Action Pane, on the **Work** tab, select **Cancel**.

<!-- KFM: The following sections came from this PR: https://github.com/MicrosoftDocs/Dynamics-365-Operations/pull/10570/files  Please consider whether they belong here and review my edits. -->

## Review wave batch job details

<!-- KFM: Add to what's new in 10.0.17, and add preview banner here?  -->

Use the **Wave batch job details** page to inspect the batch jobs and related tasks associated with any wave. This is especially useful for troubleshooting a wave that has failed. Without this feature, only administrators will typically have access to batch job details. The **Wave batch job details** page can be made available to non-admin users and provides a read-only view of batch jobs and related tasks.

### Enable the Wave batch job details page

If your system doesn't already include the **Wave batch job details** page, go to [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and turn on the *Wave batch job details* feature.

### Use the Wave batch job details page

The **Wave batch job details** page combines batch jobs and batch job tasks, which lits you investigate all the wave steps without needing to navigate back and forth between a single batch job and the batch tasks list. The page also provides access to the batch log and, provided you have the suitable permissions, provides a link to the **Batch job** page.

To open this page, select a wave on any of several different wave pages and then selecting the appropriate option from the Action Pane.

## Load validation and error messages

<!-- KFM: Add to what's new in 10.0.17, and add preview banner here?  -->
<!-- KFM: I'm not sure this section is clear.  -->

The system validates all load lines to make sure no errors occur during wave processing. For each load line that fails validation, the following error is shown: "Found invalid load lines in wave. Please remove the invalid load lines." This helps you to address all the failure in one go without requiring your to rerun to the wave process for each load line failure. <!-- KFM: I don't see how it does this. --> The **Wave processing history log** is still available for viewing all the warnings provided the **Create wave processing history log** option is enabled on the **Warehouse management parameters** page. <!-- KFM: Is this something different? -->
