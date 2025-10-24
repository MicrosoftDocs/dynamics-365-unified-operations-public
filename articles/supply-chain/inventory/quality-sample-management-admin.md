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

# Enable and configure sample management (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article provides step-by-step instructions for enabling and configuring sample management. It covers key aspects such as designing sample label layouts, setting up parameters and number sequences, defining lifecycle states, and configuring quality associations. By following these instructions, manufacturing managers and system administrators can ensure that they manage samples efficiently, accurately, and in compliance with industry standards.

## Prerequisites

To use sample management, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.46 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):
    - *Advanced quality management*
    - *(Preview) Sample management*

## Set up the sample ID number sequence

The sample ID number sequence ensures that each sample has a unique identifier for traceability and compliance. As with other number sequences in Supply Chain Management, you can define the format and scope of the sample ID number sequence to meet your organization's requirements.

Follow these steps to create and assign a number sequence for sample IDs:

1. Go to **Organization administration** \> **Number sequences** \> **Number sequences**.
1. Create and configure a number sequence for generating sample IDs, as described in [Set up number sequences on an individual basis](../../fin-ops-core/fin-ops/organization-administration/tasks/set-up-number-sequences-individual-basis.md). The number sequence must be defined to use a non-shared scope.
1. Note the **Number sequence code** that you assign to this number sequence.
1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters**.
1. Open the **Number sequences** tab.
1. Find the row with a **Reference** of *Sample ID* and set the **Number sequence code** field for that row to the number sequence that you created previously in this procedure.
1. On the Action Pane, select **Save**.

## Set up sample labels

Sample labels play an important role in the sample management process. They make sure that each sample is properly identified and traceable throughout its lifecycle. A well-designed label layout includes essential information such as the sample ID, type, and other relevant details. This information helps with efficient handling and reduces the risk of errors.

Sample labels are designed and printed in Zebra Programming Language (ZPL) format, which is a standard format for printing labels on Zebra printers. Sample labels can include information such as the sample ID, sample type, lot ID, and more.

### Design sample label layouts

To design and configure sample label layouts, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Sample management** \> **Sample label layouts**.
1. Use the buttons on the Action Pane to create a new calibration label layout or edit an existing one as required. You can also delete existing layouts.
1. On the header of the new or selected layout, enter details such as the name, description, and dimensions.
1. On the **Label layout** FastTab, use the large field to design your label layout. For help, consult a ZPL reference.
1. The page helps you find the codes that you need to insert field values. To add a field value to your layout, follow these steps:

    1. Set the **Use fields from** field to the type of database record that you want to use a field from (such as *Samples*).
    1. In the **Labels** list, select a field name.
    1. Select **Insert at end of text** to add the reference code to the end of the label layout text.
    1. Use a cut-and-paste operation to move the reference code to the desired location in the label layout text.

### Assign which labels to use when printing

Make one or both of the following assignments to specify which label layout to use for printing sample labels:

- Assign the default label layout, which applies to all samples that don't have a more specific layout assigned to them. To do this, go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters**. Open the **Quality management** tab, and then set the **Default sample label layout** field to the desired label layout.
- Assign a custom label layout to each specific sample type as needed (overrides the default). To do this, go to **Inventory management** \> **Setup** \> **Sample management** \> **Sample types**. Select a sample type, and then set the **Label layout** field to the desired label layout.

## Configure lifecycle states

Lifecycle states represent the various stages a sample goes through during its lifecycle. Lifecycle states ensure that you track samples accurately and update their status consistently as they progress through the management process.

Follow these steps to manage your lifecycle states:

1. Go to **Inventory management** \> **Setup** \> **Sample management** \> **Sample lifecycle states**.
1. Use the buttons on the Action Pane to create a new lifecycle state or edit an existing one as required. You can also delete existing lifecycle states.
1. Enter the following details for your new or selected lifecycle state:
   - **Sample lifecycle state** – Enter a unique name for the lifecycle state, such as *Registered*, *Tested*, *Archived*, or *Scrapped*.
   - **Sample lifecycle state description** – Add a brief description of the lifecycle state.
   - **Quality order created** – Select this check box for the lifecycle state that a sample should be updated to when you create a quality order for it.
   - **Quality order validated** – Select this check box for the lifecycle state that a sample should be updated to when you validate a quality order against it.
   - **Sample scrapped** – Select this check box for the lifecycle state which, when you assign it manually, triggers an audit trail logging for *Scrapped by* and *Scrapped date/time*. Only samples with this property selected can be deleted from the **Sample management workbench**.

1. On the Action Pane, select **Save**.

## Configure sample procedure types

Sample procedure types define categories and groups for organizing procedures. These configurations ensure that you process samples consistently and in compliance with organizational and regulatory requirements.

Follow these steps to manage your procedure types:

1. Go to **Inventory management** \> **Setup** \> **Sample management** \> **Sample procedure types**.
1. Use the buttons on the Action Pane to create a new procedure type or edit an existing one as required. You can also delete existing procedure types.
1. Enter the following details for your new or selected procedure type:
   - **Sample procedure type** – Provide a unique name for the procedure type.
   - **Description** – Add a brief description of the procedure type.

1. On the Action Pane, select **Save**.

<a name="configure-sample-procedures"></a>

## Define sample procedures

Sample procedures define the specific steps or actions required for handling samples. These configurations ensure that you process samples consistently and in compliance with organizational and regulatory requirements.

Follow these steps to manage your sample procedures:

1. Go to **Inventory management** \> **Setup** \> **Sample management** \> **Sample procedures**.
1. Use the buttons on the Action Pane to create a new procedure or edit an existing one as required. You can also delete existing procedures.
1. Enter the following details in the header of your new or selected procedure:
   - **Sample procedure ID** – Provide a unique name for the procedure.
   - **Description** – Add a brief description of the procedure.
   - **Sample procedure type** – Select the relevant [procedure type](#configure-sample-procedure-types) for the procedure.
   - **Sample inspections method** – Choose which [inspection methods](quality-sample-management-overview.md) the procedure is intended for (*Inline process*, *Continuous process*, or *Both*).

1. On the **Procedure** FastTab, enter or paste detailed instructions for the procedure.
1. On the Action Pane, select **Save**.

## Define sample types

Sample types define the classification and processing methods for samples. When you configure sample types, you ensure that samples are managed according to their specific requirements and that appropriate workflows are applied.

To manage your sample types, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Sample management** \> **Sample types**.
1. Use the buttons on the Action Pane to create a new sample type or edit an existing one as required. You can also delete existing sample types.
1. Enter the following details in the header of your new or selected sample type:
   - **Sample type** – Enter a unique name for the sample type, such as *Inline* or *Continuous*.
   - **Description** – Add a brief description of the sample type.
   - **Sample inspections method** – Choose which inspection methods the sample type applies to (*Inline process*, *Continuous process*, or *Both*).
   - **Label layout** – Select the [label layout](#set-up-sample-labels) to use for this sample type.
   - **Description** – Shows the description configured for your selected [label layout](#set-up-sample-labels) (read only).

1. On the Action Pane, select **Save**.
1. Use the **Sample lifecycle states** FastTab to select the [lifecycle states](#configure-lifecycle-states) that are relevant to this sample type. Use the buttons between the columns to move the relevant states between the **Available** and **Selected** lists as needed. Selecting lifecycle states ensures that the sample type follows a defined progression through its lifecycle, from creation to completion or disposal. These states trigger specific system behaviors, such as updating the sample when a quality order is created or validated, or logging audit trail details when a sample is scrapped. By configuring the relevant states, you enable consistent handling, tracking, and automation of sample-related processes.
1. On the Action Pane, select **Save**.

## Set up sample associations

A sample association defines how and when quality samples are taken for a specific item. It supports both inline and continuous sampling methods, using designated sample types with configurable retention periods and automated expiration tracking. Linking sampling procedures to items and test groups ensures consistent quality control, supports regulatory compliance, and enables efficient inspection workflows tailored to operational needs.

Follow these steps to define and configure sample associations:

1. Go to **Inventory management** \> **Setup** \> **Sample management** \> **Sample associations**.
1. Use the buttons on the Action Pane to create a new sample association or edit an existing one as required. You can also delete existing sample associations.
1. Enter the following details in the top section to set up your new or selected sample association:
   - **Item code** – Select the scope of products to include in the rule. Choose one of the following values:
        - *Table* – A specific product.
        - *Group* – A group of products.
        - *All* – All products.
   - **Item** – Depending on what you selected for **Item code**, choose the specific product or product group for which this rule should apply. Leave blank if **Item code** is set to *All*.
   - **Inline sample type** – Select the sample type that defines how inline samples for this item should be inspected, including their applicable lifecycle states. This sample type governs the inspection method used for inline sampling and ensures that the correct procedures and validations are applied throughout the sample's lifecycle.
   - **Inline sample scrap in days** – Specify how many days inline samples should be retained before being automatically scrapped. This setting helps manage sample lifecycle and storage by defining the retention period for inline samples associated with the item.
   - **Default item sampling for inline** – Specifies the default [item sampling](#configure-item-samplings) policy applied to inline samples during production. Item sampling policies define the criteria for selecting samples. When initiating inline sampling from the production orders list or details page, this value is prefilled in the create dialog but can be adjusted as needed.
   - **Default inline test group** – Specify the default [test group](#test-groups) used for inline samples from production. When initiating inline sampling from the production orders list or details page, this value is prefilled in the create dialog but can be adjusted as needed.
   - **Continuous sample type** – Select the sample type that defines how continuous samples for this item should be inspected, including their applicable lifecycle states. This sample type governs the inspection method used for continuous sampling and ensures that the correct procedures and validations are applied throughout the sample's lifecycle.
   - **Continuous sample scrap in days** – Select the number of days that continuous samples for this item should be saved before being scrapped.

1. In the bottom section, with the relevant row still selected in the top section, add each of the [sample procedures](#configure-sample-procedures) that workers should follow when handling samples for this association. Use the toolbar buttons to add or remove procedures as needed.
1. On the Action Pane, select **Save**.

<a name="configure-item-samplings"></a>

## Configure item sampling policies

Item sampling policies define the criteria for selecting samples. Configuring these settings ensures that you select samples consistently and in compliance with quality standards.

Follow these steps to define an item sampling policy:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Item sampling**.
1. Use the buttons on the Action Pane to create a new item sampling policy or edit an existing one as required. You can also delete existing policies.
1. Set up the item sampling policy as described in [Quality management item sampling](../inventory/quality-item-sampling.md).
1. On the **Sample management** FastTab, set up the settings that are specific for sample management. Make the following settings here.

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

The following subsections describe other important settings for sample management. These records and settings are shared by other kinds of quality management processes supported by Supply Chain Management, but they are also essential for sample management.

### Quality associations

Configure quality associations to trigger sample management when production orders are reported as finished for specific items. This setup references test groups and item sampling policies to ensure consistency and automation in quality control. For inline samples, you don't need a quality association because you collect these samples on demand directly from the production order. Learn more in [Quality associations](../inventory/quality-associations.md). The following settings for quality associations are particularly relevant for sample management:
    - **Reference type** – Select *Production* which is the only supported type for sample management.
    - **Event type** – Select *Report as finished*.
    - **Execution** – Select *After*.
    - **Test group** – Select the test group that should be used for quality orders generated for samples.
    - **Item sampling** – Select the item sampling configuration used for sample management. This configuration determines whether the *Inline* or *Continuous* sampling method is applied, along with related details for how each method is used.

### Configure default item status

The default item status establishes the initial inventory status assigned to new items in inventory. This is relevant when samples are configured to be generated for each license plate produced. Typically, you should define the default inventory status as *On-hold*, which indicates that the license plate is awaiting inspection. You can configure the default item status to apply for an individual item or for all transactions at a specific warehouse.

To configure the default item status for a specific item follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Inventory** \> **Default item status**.
1. On the Action Pane, select **New** to create a new record.
1. Enter the following details for your new record:
    - **Item number** – Select the product you want to configure for sample management.
    - **Module** – Select *Inventory* which is the only applicable value for sample management.
    - **Default inventory status ID** – From the list, select the inventory status that should be used as default when a sample with an associated license plate is created in sample management. <!-- KFM: The system won't let me choose a status set to blocking, but that is what we are asking for. What should we do? -->

To configure the default item status that is applicable for all item transactions at a specific warehouse, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Inventory breakdown** \> **Warehouses**.
1. Find and select the warehouse where you want to configure the default item status.
1. On the **Warehouse** FastTab, set the default inventory status in the **Default inventory status ID** field.

<!-- KFM: There is also a default settings stats in Warehouse management parameters--is that relevant here. What is the hierarchy among these three? -->

### Test groups

[Test groups](../inventory/quality-test-groups.md) define the set of tests applied while processing quality orders. On each test group, you also define the status the system should apply to license plates or product batches based on the outcome of the quality order test results.

If you configured sample management to generate samples per license plate, then the **Inventory status** is used to control the status of the license plate. To control the initial status of the license plates generated during production report as finished, set the following fields on the relevant test group:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test groups**
1. Select and existing test group or create a new one.
1. Select the **General** Tab and make the following settings:
    - **Update inventory status** – Set to *Yes* to enable inventory status updates based on test results.
    - **Failed quality order status** – Specify the inventory status to apply to the license plate when a quality order fails. This setting only applies when **Update inventory status** is set to *Yes*.
    - **Passed quality order status** – Specify the inventory status to apply to the license plate when a quality order passes. This setting only applies when **Update inventory status** is set to *Yes*.

If you configured sample management to generate samples per product batch number, then the batch disposition master is used to control the status of the individual batch number. To control the initial status on batch numbers generated during report as finished, set the following fields on each test group:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test groups**
1. Select and existing test group or create a new one.
1. Select the **General** Tab and make the following settings:
    - **Update batch disposition** – Set to *Yes* to enable update of the tested batch number based on whether the quality order is failing or passing.
    - **Failed quality order batch disposition** – Specify the batch disposition master to apply to the tested batch number when a quality order fails. This setting only applies when **Update batch disposition** is set to *Yes*.
    - **Passed quality order batch disposition** – Specify the batch disposition master to apply to the tested batch number when a quality order passes. This setting only applies when **Update batch disposition** is set to *Yes*.

Learn more in [Batch disposition codes](../inventory/batch-disposition-codes.md).
