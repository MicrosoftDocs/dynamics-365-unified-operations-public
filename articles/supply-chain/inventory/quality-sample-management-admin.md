---
title: Enable and configure sample management (preview)
description: Learn how to enable and configure sample management, including how to design sample label layouts, set up parameters and number sequences, define lifecycle states, and configure quality associations.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 10/24/2025
ms.custom: 
  - bap-template
---

<!-- KFM: 

Johan: I have edited and verified nearly all of this text so it should be in very good shape (but please review it anyway). I've added a few notes for what I know is missing and with a few suggestions.

-->

# Enable and configure sample management (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.45 GA -->

This topic provides step-by-step instructions for enabling and configuring sample management. It covers key aspects such as designing sample label layouts, setting up parameters and number sequences, defining lifecycle states, and configuring quality associations. By following these instructions, manufacturing managers and system administrators can ensure that they manage samples efficiently, accurately, and in compliance with industry standards.

## Prerequisites

To use sample management, your system must meet the following requirements:

- You're running Microsoft Dynamics 365 Supply Chain Management version 10.0.46 or later.
- The following features are turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):
    - *Advanced quality management*
    - *(Preview) Sample management*

## Set up the sample ID number sequence

The sample ID number sequence ensures that each sample has a unique identifier for traceability and compliance. As with other number sequences in Supply Chain Management, you can define the format and scope of the sample ID number sequence to meet your organization's requirements.

Follow these steps to create and assign a number sequence for sample IDs:

1. Go to **Organization administration** > **Number sequences** > **Number sequences**.
1. Select **New** to create a number sequence for sample IDs.
1. Configure the following details:
   - **Name** – Provide a unique name for the number sequence (for example, *Sample ID Sequence*).
   - **Scope** – Define the scope of the number sequence (for example, *Company* or *Legal entity*).
   - **Format** – Specify the format for the number sequence (for example, *SMP-######*).
1. Go to **Inventory management** > **Setup** > **Inventory and warehouse management parameters**.
1. Open the **Number sequences** tab.
1. Find the row with a **Reference** of *Sample ID* and set the **Number sequence code** field for that row to the number sequence that you created previously in this procedure.
1. Save the changes.

## Set up sample labels

Sample labels play an important role in the sample management process. They make sure that each sample is properly identified and traceable throughout its lifecycle. A well-designed label layout includes essential information such as the sample ID, type, and other relevant details. This information helps with efficient handling and reduces the risk of errors.

Sample labels are designed and printed in Zebra Programming Language (ZPL) format, a standard format for printing labels on Zebra printers. Sample labels can include information such as the sample ID, sample type, lot ID, and more.

### Design sample label layouts

To design and configure sample label layouts, follow these steps:

1. Go to **Inventory management** > **Setup** > **Sample management** > **Sample label layouts**.
1. Use the buttons on the Action Pane to create a new calibration label layout or edit an existing one as required. You can also delete existing layouts.
1. On the header of the new or selected layout, enter details such as the name, description, and dimensions.
1. On the **Label layout** FastTab, use the large field to design your label layout. For help, use a ZPL reference.
1. The page helps you find the codes that you need to insert field values. To add a field value to your layout, follow these steps:

    1. Set the **Use fields from** field to the type of database record that you want to use a field from (such as *Samples*).
    1. In the **Labels** list, select a field name.
    1. Select **Insert at end of text** to add the reference code to the end of the label layout text.
    1. Use a copy-and-paste operation to move the reference code to the desired location in the label layout text.

### Assign which labels to use when printing

Make one or both of the following assignments to specify which label layout to use for samples:

- Assign the default label layout, which applies to all samples that don't have a more specific layout assigned to them. To do this, go to **Inventory management** > **Setup** > **Inventory and warehouse management parameters**. Open the **Quality management** tab, and then set the **Default sample label layout** field to the desired label layout.
- Assign a custom label layout to each specific sample type as needed (overrides the default). To do this, go to **Inventory management** > **Setup** > **Sample management** > **Sample types**. Select a sample type, and then set the **Label layout** field to the desired label layout.

## Configure lifecycle states

Lifecycle states represent the various stages a sample goes through during its lifecycle. Lifecycle states ensure that samples are tracked accurately and that their status is updated consistently as they progress through the management process.

Follow these steps to manage your lifecycle states:

1. Go to **Inventory management** > **Setup** > **Sample management** > **Sample lifecycle states**.
1. On the Action Pane, select **New** to create a new lifecycle state or select **Edit** to modify an existing one.
1. Enter the following details for your new or selected lifecycle state:
   - **Sample lifecycle state** – Provide a unique name for the lifecycle state, such as *Created*, *Received in Lab*, or *Tested*.
   - **Sample lifecycle state description** – Add a brief description of the lifecycle state.
   - **Quality order created** – Specifies the lifecycle state to which the sample should be updated when a quality order is created.
   - **Quality order validated** – Specifies the lifecycle state to update the sample to when a quality order is validated against it.
   - **Sample scrapped** – Specifies the lifecycle state that, when manually set, triggers audit trail logging for 'Scrapped By' and 'Scrapped Date/Time'.

1. On the Action Pane, select **Save**.

## Configure sample procedure types

Sample procedure types define the categories and groups for organizing procedures. These configurations ensure that you process samples consistently and in compliance with organizational and regulatory requirements.

Follow these steps to manage your procedure types:

1. Go to **Inventory management** > **Setup** > **Sample management** > **Sample procedure types**.
1. On the Action Pane, select **New** to create a new procedure type or select **Edit** to modify an existing one.
1. Enter the following details for your new or selected procedure type:
   - **Sample procedure type** – Provide a unique name for the procedure type.
   - **Description** – Add a brief description of the procedure type.

1. On the Action Pane, select **Save**.

## Configure sample procedures

Sample procedures define the specific steps or actions required for handling samples. These configurations ensure that you process samples consistently and in compliance with organizational and regulatory requirements.

Follow these steps to manage your sample procedures:

1. Go to **Inventory management** > **Setup** > **Sample management** > **Sample procedures**.
1. On the Action Pane, select **New** to create a new sample procedure or select **Edit** to modify an existing one.
1. Enter the following details in the header of your new or selected procedure:
   - **Sample procedure ID** – Provide a unique name for the procedure.
   - **Description** – Add a brief description of the procedure.
   - **Sample procedure type** – Select the relevant [procedure type](#configure-sample-procedure-types) for the procedure.
   - **Sample inspections method** – Choose which inspection methods the procedure is intended for (*Inline process*, *Continuous process*, or *Both*).

1. On the Procedure FastTab, enter or paste detailed instructions for the procedure.
1. On the Action Pane, select **Save**.

## Define sample types

Sample types define the classification and processing methods for samples. When you configure sample types, you ensure that samples are managed according to their specific requirements and that appropriate workflows are applied.

To manage your sample types, follow these steps:

1. Go to **Inventory management** > **Setup** > **Sample management** > **Sample types**.
1. On the Action Pane, select **New** to create a new sample type or select **Edit** to modify an existing one.
1. Enter the following details in the header of your new or selected sample type:
   - **Sample type** – Enter a unique name for the sample type, such as *Inline* or *Continuous*.
   - **Description** – Add a brief description of the sample type.
   - **Sample inspections method** – Choose which inspection methods the sample type applies to (*Inline process*, *Continuous process*, or *Both*).
   - **Label layout** – Select the [label layout](#set-up-sample-labels) to use for this sample type.
   - **Description** – Shows the description configured for your selected [label layout](#set-up-sample-labels) (read only).

1. Use the **Sample lifecycle states** FastTab to select the [lifecycle states](#configure-lifecycle-states) that are relevant to this sample type. Use the buttons between the columns to move the relevant states between the **Available** and **Selected** lists as needed. 

Selecting lifecycle states ensures that the sample type follows a defined progression through its lifecycle—from creation to completion or disposal. These states are used to trigger specific system behaviors, such as updating the sample when a quality order is created or validated, or logging audit trail details when a sample is scrapped. By configuring the relevant states, you enable consistent handling, tracking, and automation of sample-related processes.

1. On the Action Pane, select **Save**.

## Set up sample associations

A sample association defines how and when quality samples are taken for a specific item. It supports both inline and continuous sampling methods, using designated sample types with configurable retention periods and automated expiration tracking. By linking sampling procedures to items and test groups, it ensures consistent quality control, supports regulatory compliance, and enables efficient inspection workflows tailored to operational needs.

Follow these steps to define and configure sample associations:

1. Go to **Inventory management** > **Setup** > **Sample management** > **Sample associations**.
1. On the Action Pane, select **New** to create a new sample association or select **Edit** to modify an existing one.
1. Enter the following details in the top section to set up your new or selected sample association:
   - **Item code** – Select which products should be included in the rule. Choose one of the following values:
        - *Table* – A specific product.
        - *Group* – A group of products.
        - *All* – All products.
   - **Item** – Depending on what you selected for **Item code**, choose the specific product or product group for which this rule should apply. Leave blank if **Item code** is set to *All*.
   - **Inline sample type** – Select the sample type that defines how the inline sample should be inspected, including its applicable lifecycle states. This sample type governs the inspection method used for inline sampling and ensures that the correct procedures and validations are applied throughout the sample's lifecycle.
   - **Inline sample scrap in days** – Specify how many days inline samples should be retained before being automatically scrapped. This setting helps manage sample lifecycle and storage by defining the retention period for inline samples associated with the item.
   - **Default item sampling for inline** – Specifies the default item sampling method applied to inline samples during production. When initiating inline sampling from the production orders list or details page, this value is pre-filled in the create dialog but can be adjusted as needed.
   - **Default inline test group** – Specify the default test group used for inline samples from production. When initiating inline sampling from the production orders list or details page, thsi value is pre/filled in the create dialog but can be adjusted as needed.
   - **Continuous sample type** – Select the sample type that defines how the continuous sample should be inspected, including its applicable lifecycle states. This sample type governs the inspection method used for continuous sampling and ensures that the correct procedures and validations are applied throughout the sample's lifecycle.
   - **Continuous sample scrap in days** – Select the number of days that continuous samples for this item should be saved before being scrapped.

1. With the relevant row still selected in the top section, add each of the [sample procedures](#configure-sample-procedures) that workers should follow when handling samples for this association. Use the toolbar buttons to add or remove procedures as needed.
1. On the Action Pane, select **Save**.

## Configure item samplings

Item samplings define the criteria for selecting samples. Configuring these settings ensures that you select samples consistently and in compliance with quality standards.

Follow these steps to define item sampling criteria:

1. Go to **Inventory management** > **Setup** > **Quality control** > **Item sampling**.
1. On the Action Pane, select **New** to create a new item sampling record or select **Edit** to modify an existing one.
1. Set up the item sampling policy as described in [Quality management item sampling](../inventory/quality-item-sampling.md).
1. Settings that are specific for sample management are provided on the **Sample management** FastTab. Make the following settings here.

    - To set up inline sampling, make the following settings on the **Sample management** FastTab:
        - **Sample inspections method** – Select *Inline process*.
        - **Sample size** – Enter the desired sample size.
        - **Unit** – Select the unit of measurement for the sample size (such as *Pieces* or *Milliliters*).

    - To set up continuous sampling, make the following settings on the **Sample management** FastTab:
        - **Sample inspections method** – Select *Continuous process*.
        - **Sample size** – Enter the desired sample size.
        - **Unit** – Select the unit of measurement for the sample size (such as *Pieces* or *Milliliters*).
        - **One sample every** – Specify how often samples should be taken and then choose whether to count batches or license plates (for example, enter *10* and select *Batch* to take a sample from every tenth batch that's reported as finished).
        - **Number of samples per quality order generated** – Specify how often samples should be tested (for example, enter *4* to test every fourth sample).

1. On the Action Pane, select **Save**.

## Configure related quality management records

The following describes some other important topics for sample management.

### Quality associations

Quality associations are configured to trigger sample management when production orders are reported as finished for specific items. This setup references test groups and item sampling configurations to ensure consistency and automation in quality control. For inline samples, a quality association is not required, as these samples are collected on demand directly from the production order. Learn more in [Quality associations](../inventory/quality-associations.md).

### Configure default item status

Default item status is a configuration that determines the initial inventory status assigned to items during various supply chain transactions—such as receiving, production, or returns. It helps control how items are treated in terms of availability, blocking, and reservation. For sample management, the default inventory status is used when samples are configured on the license plate level. Typically, the default inventory status should be defined as *On-hold* using a status that is configured as *blocking*. Use the following steps to configure the default item status:

For sample management, the default status can be set on following two levels:

- **Item level** 
    1. Go to **Warehouse management** > **Setup** > **Inventory** > **Default item status**.
    1. On the Action Pane, select **New** to create a new record.
    1. Enter the following details for your the new record:
       - **Item number** – Select the product for sample management
       - **Description** – Add a brief description of the procedure type.

- **Warehouse level**
    1. Go to **Warehouse management** > **Setup** > **Inventory breakdown** > **Warehouses**.
    1. Select or search for an applicable warehouse where the policy should apply.
    1. On the **Warehouse** FastTab, set the default inventory status in the **Default inventory status ID** field.

### Test groups

Test groups define the set of tests applied during quality orders. When configuring test groups for quality orders, especially when samples are taken out using license plates, the following fields are important for managing inventory status:
    - **Update inventory status** - Enables inventory status updates based on test results.
    - **Failed quality order status** - Specifies the inventory status to apply when a quality order fails. Only applicable if Update Inventory Status is enabled. License plates are updated to this status.
    - **Passed quality order status** - Specifies the inventory status to apply when a quality order passes. Only applicable if Update Inventory Status is enabled. License plates are updated to this status.

Learn more in [Quality management test groups](../inventory/quality-test-groups.md) 

### Batch disposition codes

A batch disposition code is assigned at the batch level and indicates whether a batch is available or unavailable for operational use. These codes help organizations manage inventory restrictions and support quality control compliance.
Learn more in: [Batch disposition codes](../inventory/batch-disposition-codes.md). When using the continuous sample method with a sample plan based on batches, the results of quality inspections directly determine whether inventory is blocked or released through batch disposition codes. Specifically:
    - If a quality order fails, the related inventory batch is blocked (made unavailable for use) by updating its batch disposition code.
    - If a quality order passes, the batch is released (made available for use) by updating its batch disposition code accordingly.
This process ensures that only batches meeting quality standards are available for operational activities, while those that fail inspection are restricted from use.
