---
title: Wave creation and processing
description: Learn how to create, process, and release a wave to create picking work for a load, shipment, production order, or kanban order.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 4/27/2026
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form:  WHSWaveTemplateTable, WHSParameters, whswavetablecreatenew, WHSWaveTable, WHSWaveAttributes, WHSKanbanWaveTable, WHSWaveTableListPage, WHSKanbanWaveTableListPage, WHSProdWaveTable
---

# Wave creation and processing

[!include [banner](../includes/banner.md)]

This article describes how to create, process, and release a wave to create picking work for a load, shipment, production order, or kanban order. You can create waves for the following types of orders:

- **Sales orders**, **Transfer orders**, and **Outbound shipment orders** – Use shipping waves to include lines from sales orders, transfer orders, and outbound shipment orders. When an order is released to the warehouse, you can include its order lines in the wave.
- **Production orders** – Use production waves to include lines from the bill of materials (BOM) for a product.
- **Kanban orders** – Kanban waves include picking list lines from kanban orders.

For sales orders and kanban orders, inventory must be reserved before the order is released to the warehouse. Otherwise, the items or allocation lines can't be processed in a wave. However, production orders are slightly more flexible. For production orders, you can choose either of the following options:

- Require that all materials are reserved before an order can be released to the warehouse.
- Allow production orders to be released to the warehouse even though all materials can't be reserved. If you select this option, you must manually repeat the release to warehouse process when the additional materials become available. For example, this option is useful if you have the materials that you need to start a production, and can wait until the additional materials become available.

You can specify which of these production order options to use by default by using the **Requirement for material reservation** field on the **Production control parameters** page. However, you can change the setting for each specific production order as needed. For more information, see [Warehouse parameters for wave processing](wave-warehouse-parameters.md).

## Create and process a wave

The following diagram shows the flow for how shipping waves are created, processed, and released. The numbers correspond to the sections later in this article.

:::image type="content" source="media/wave-processing-diagram.png" alt-text="Screenshot of the process flow for creating a wave.":::

### Prerequisites

Before you start, a wave template must be available for the type of wave you want to create (shipping, production, or kanban). The wave template establishes many settings for how the wave is generated and processed, including which steps must be done manually and which steps are done automatically. For more information, see [Wave templates](wave-templates.md).

### Create a wave

#### Automatically create waves based on warehouse and order type

To automatically create waves, set up [Wave templates](wave-templates.md) that apply to each relevant order type and warehouse. Make sure each template has the **Automate wave creation** option set to *Yes*.

#### Manually create waves

To manually create a wave, follow these steps:

1. Make sure that the relevant [Wave templates](wave-templates.md) aren't set to automatically create a wave for the warehouse and order types where you want to create waves manually.
1. Depending on the type of wave you want to create, go to one of the following locations:

    - **Warehouse management** > **Outbound waves** > **Shipment waves** > **All waves**. On the Action Pane, select **Wave**.
    - **Warehouse management** > **Outbound waves** > **Production waves** > **All production waves**. On the Action Pane, select **Production wave**.
    - **Warehouse management** > **Outbound waves** > **Kanban waves** > **All kanban waves**. On the Action Pane, select **Create wave**.

1. In the **Description** field, enter a short description of the wave. This description should indicate what you're processing in the wave.

1. In the **Wave template name** field, select the wave template for the type of wave to create. The wave template contains the wave methods that perform actions such as creating work for the wave. For example, the wave template for shipping waves can contain methods for creating loads, allocating lines to waves, replenishment, and creating picking work for the wave.

1. If you want to use wave attributes as additional query criteria for the wave, select the attributes in the **Wave attributes** fields.

### Specify what to include in a wave

After you create a wave, add content to it.

> [!NOTE]
> If needed, you can add lines to a wave even after it’s processed as long as it’s not released.

#### Automatically specify what to include in a wave

To create waves automatically, set up [Wave templates](wave-templates.md) that apply for each relevant order type and warehouse. Make sure each template has the **Automate wave creation** option set to *Yes*. Alternatively, your template could automatically assign lines to any qualifying open wave if the **Assign to open waves** option is set to *Yes*.

#### Manually specify what to include in a wave

When a wave is created but isn't yet released, you can manually specify what to include in it. To add lines to a wave manually:

1. Depending on the type of wave to add lines to, go to one of the following locations:

    - **Warehouse management** > **Outbound waves** > **Shipment waves** > **All waves**. On the Action Pane, select **Wave**.
    - **Warehouse management** > **Outbound waves** > **Production waves** > **All production waves**. On the Action Pane, select **Production wave**.
    - **Warehouse management** > **Outbound waves** > **Kanban waves** > **All kanban waves**. On the Action Pane, select **Create wave**.

1. Select the wave. On the Action Pane, select one of the following options:

      - **Maintain shipments**
      - **Maintain productions**
      - **Maintain kanban job picking lists**

1. In the upper part of the window, select the line to add to the wave, and then select **Add to wave**. The line moves to the **Wave lines** FastTab.

    Repeat this step for each line to add. To add all lines, select **Add all**.

    > [!TIP]
        > For shipment waves, you can quickly find a specific order by selecting a custom filter in the **Wave filter code** field. Wave filter codes contain query criteria for shipments created in the **Wave filters** form. This field isn't available for production waves or kanban waves.
    > A green check mark in the **On wave** column indicates that the shipment is added to the wave.

### Process the wave to create the picking work

After you create a wave and add all required lines, you're ready to process it and create the corresponding picking work.

#### Automatically process a wave

To automatically process a wave, set up the relevant [Wave templates](wave-templates.md) with the automatic processing options you need.

#### Manually process a wave

You can process a wave only when the **Wave status** is *Created*. After you process a wave, the **Wave status** changes to *Held*.

To manually process a wave that contains all required content, follow these steps:

1. Depending on the type of wave to process, do one of the following steps:

    - Select **Warehouse management** > **Outbound waves** > **Shipment waves** > **All waves**. On the Action Pane, select **Wave**.
    - Select **Warehouse management** > **Outbound waves** > **Production waves** > **All production waves**. On the Action Pane, select **Production wave**.
    - Select **Warehouse management** > **Outbound waves** > **Kanban waves** > **All kanban waves**. On the Action Pane, select **Create wave**.

1. Select the wave to process. On the Action Pane, select **Process**.

### Release the wave to the warehouse to start picking and packing

You must process a wave before you can release it. When you release the wave, the picking work is available in the warehouse. You can cancel a wave after it is released, and add more lines, but you can't change the lines.

#### Automatically release a wave

To automatically process a wave, set up the relevant [Wave templates](wave-templates.md) with the automatic processing options you need.

#### Manually release a wave

To release a wave manually, follow these steps:

1. Depending on the type of wave to release, do one of the following:

      - Select **Warehouse management** > **Outbound waves** > **Shipment waves** > **All waves**. On the Action Pane, select **Wave**.
      - Select **Warehouse management** > **Outbound waves** > **Production waves** > **All production waves**. On the Action Pane, select **Production wave**.
      - Select **Warehouse management** > **Outbound waves** > **Kanban waves** > **All kanban waves**. On the Action Pane, select **Create wave**.

1. Select the wave to release. On the Action Pane, select **Release wave**.

## Containerize a wave

Automated containerization creates containers and the picking work for shipments when a wave is processed. For details about how to set it up, see [Containerization](wave-containerization.md).

## Work with the scheduled work creation

The following flowchart shows how planned work is created during wave processing.

:::image type="content" source="media/schedule-work-creation-process.png" alt-text="Screenshot of the scheduled work creation flowchart during wave processing.":::

### Planned work

The **Planned work details** page (**Warehouse management \> Work \> Planned work details**) shows information about the planned work, which is initially created during wave processing. The following **Process status** values are available:

- **Queued** - The planned work is waiting to be used to create work.
- **Completed** - The planned work is used to create work.
- **Failed** – The wave processing failed. The planned work can be in a **Failed** state with or without related actual work. When the actual work creation process fails, the actual work remains in status *Cancelled*.

### Batch job for the work creation process

To view the batch jobs for processing waves, select **Batch jobs** on the Action Pane on the **All waves** page.

From here, you can view all the batch task details for each of the batch job IDs.

## Cancel a wave

If needed, you can cancel a wave that you processed. To cancel a wave, and the picking work that's created, follow these steps:

1. Depending on the type of wave to cancel, go to one of the following locations:

            - **Warehouse management** > **Outbound waves** > **Shipment waves** > **All waves**.
            - **Warehouse management** > **Outbound waves** > **Production waves** > **All production waves**.
            - **Warehouse management** > **Outbound waves** > **Kanban waves** > **All kanban waves**.

1. Select the wave to cancel. On the Action Pane, on the **Work** tab, select **Cancel**.

## Review wave batch job details

Use the **Wave batch job details** page to inspect the batch jobs and related tasks associated with any wave. This is especially useful for troubleshooting a wave that has failed. Without this feature, only administrators will typically have access to batch job details. The **Wave batch job details** page can be made available to non-admin users and provides a read-only view of batch jobs and related tasks.

### Use the Wave batch job details page

The **Wave batch job details** page combines batch jobs and batch job tasks. You can investigate all the wave steps without needing to navigate back and forth between a single batch job and the batch tasks list. The page also provides access to the batch log and, if you have the required permissions, provides a link to the **Batch jobs** page.

To open this page, select a wave on any of several different wave pages and then select **Wave batch job details** from the Action Pane.

## Review load validation and error messages

During wave processing, the system validates and displays the status for each load line in the wave. If no warnings occur, it continues to the next wave step. If warnings do occur, it shows the following error after it finishes validating the entire wave:

> Found invalid load lines in wave. Please remove the invalid load lines.

You can review the final status of each load line in the wave and correct all warnings before trying again. This process lets you address all the warnings at once before reprocessing the wave. (In previous releases, the system stopped processing the wave after the first warning, so you could only fix warnings one at a time.)

The way the system displays your wave processing status messages depends on how you set the **Create wave processing history log** option on the **Warehouse management parameters** page.

- When **Create wave processing history log** is set to *No*, the load line status messages are shown in the Action center.
- When **Create wave processing history log** is set to *Yes*, the load line status messages are shown on the **Wave processing history log** page. To view the log, go to **Warehouse management** > **Outbound waves** > **Wave processing history log**.

## Related information

- [Configure wave processing example](tasks/configure-wave-processing.md)
- [Wave templates](wave-templates.md)
- [Containerization](wave-containerization.md)
