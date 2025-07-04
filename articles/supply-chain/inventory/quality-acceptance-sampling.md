---
title:  Acceptance sampling (preview)
description: Learn how to set up acceptance sampling to quality control products batches by inspecting representative samples.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: QMSAQLDefectType, QMSAQLInspectionLevel, QMSAQLChart, InventTestTable, InventTestGroup, InventItemSampling, InventTestAssociationTable, QMSAQLIndex
ms.topic: how-to
ms.date: 07/28/2025
ms.custom: 
  - bap-template
---

# Acceptance sampling (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.46 GA -->

*Acceptance sampling* is a quality control method used to evaluate a batch of products by inspecting a representative sample. Instead of checking every item, a subset of items is examined to determine whether the entire lot meets predefined quality standards. This approach is widely used in manufacturing and supply chain operations to balance inspection effort with quality assurance. In many practical applications, sampled items are inspected for different *types* of defects, each of which is typically placed in one of the following *categories*:

- **Critical defects** – Defects that could cause harm or render a product unsafe or unusable. Even a single critical defect may lead to rejection of the entire lot.
- **Major defects** – Defects that significantly reduce the usability or performance of a product but don't pose safety risks. A limited number of major defects may be acceptable depending on the sampling plan.
- **Minor defects** – Defects that don't affect a product's function or safety but may impact appearance or user satisfaction. A higher tolerance is usually allowed for minor defects.

Acceptance criteria are defined in advance, often using standards like ANSI/ASQ Z1.4 or ISO 2859-1, which specify how many defects of each type <!-- KFM: do we mean *type* or *category* here? --> are permissible in a sample before the lot is rejected. This structured approach helps ensure consistent product quality while optimizing inspection resources.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.45 or later.
- The feature that is named *(Preview) Acceptance sampling* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

<!-- KFM: any other prerequisites? -->

## Set up defect types

<!-- KFM: Intro needed. Explain what defect types are and what we will use them for. -->

To set up defect types, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Defect types**.
1. Select **New** to create a new defect type and set the following fields:
    - **Defect type** – <!-- KFM: description needed -->
    - **Defect category** – <!-- KFM: description needed --> Choose one of the following categories:
        - *Critical** – Could cause harm or render a product unsafe or unusable. Even a single critical defect may lead to rejection of the entire lot.
        - *Major** – Significantly reduces the usability or performance of a product but don't pose safety risks. A limited number of major defects may be acceptable depending on the sampling plan.
        - *Minor** – Doesn't affect function or safety but may impact appearance or user satisfaction. A higher tolerance is usually allowed for minor defects.

    - **Description** – <!-- KFM: description needed -->

> [!NOTE]
> In acceptance sampling, the defect types are typically named: *Critical*, *Major*, and *Minor*. <!-- KFM: So, these are the same as the values offered for the category? It seems like some businesses would instead use terms like "paint chipped", "screen cracked", "packaging damaged", etc. -->

## Set up inspection levels

<!-- KFM: Intro needed. Explain what inspection levels are and what we will use them for. -->

To set up inspection levels, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Inspection levels**.
1. Select **New** to create a new inspection level and set the following fields:
    - **Inspection level** – <!-- KFM: description needed -->
    - **Inspection level type** – <!-- KFM: description needed -->
    - **Description** – <!-- KFM: description needed -->

## Set up acceptance sampling indexes

<!-- KFM: Explain what these are, how they are used, and how to set them up. -->


## Set up acceptance sampling charts

<!-- KFM: Start by briefly explaining what an acceptance chart is and what to use it for. -->

An *acceptance sampling chart* is a collection of the following charts:

- Sampling size code letter chart <!-- KFM: define/explain this. We probably also need a section for how to understand this chart and a procedure for how to create and work with this chart. -->
- Acceptable quality limit chart <!-- KFM: define/explain this. We probably also need a section for how to understand this chart and a procedure for how to create and work with this chart.  -->

Acceptance sampling charts also include the following supporting data for each chart:

- Inspection levels <!-- KFM: define/explain this -->
- AQL indexes <!-- KFM: define/explain this. Spell out "AQL" -->
- Lot/batch size ranges <!-- KFM: define/explain this -->

Learn more about how to use the charts in the following video: <!-- KFM: your video isn't being hosted in the right way to be embedded. And I'm not sure whether we can share it using the host/URL you provided. We should check with Tammy. -->

> [!VIDEO 1e6ef0b8-0c35-4560-9f2a-926da8a6fd9b]

To set up an acceptance sampling chart, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Acceptance sampling chart**.
1. Use the buttons on the Action Pane to add a new chart or edit a selected one.
1. On the header of the new or selected chart, set the following fields:
    - **Acceptance sampling chart name** – Enter a name for the sampling chart.
    - **Description** – Enter a short description of the sampling chart.

1. To get started quickly, you can choose start by copying an existing cart or loading a predefined template. If you'd like to do this, select one of the following options in the Action Pane. Be careful, because all of the settings for the current chart (other than name and description) will be replaced with the template or copied chart.
    - **Load AQL chart template** – Load all the data needed for the acceptance sampling chart from a predefined template. <!-- KFM: Where does this template come from? Can I customize it? What is the one we supply designed for/after? -->
    - **Copy** – Copy data from another chart. The system asks you to choose an existing chart to copy from.

1. On the **Inspection levels to include** FastTab, use the buttons in the toolbar to add and remove inspection levels for the current chart. <!-- KFM: explain what these do and how they affect the chart. Maybe link to earlier section where we describe how to set these up. -->

1. On the **AQL indexes to include** FastTab, use the button in the toolbar to add and remove AQL indexes for the current chart. <!-- KFM: explain what these do, where they come from, and how they affect the chart. This is a lookup--how do we manage these? What do they mean? Are these the same as "acceptance sampling indexes"? -->

1. On the **Lot/batch size ranges** FastTab, use the buttons in the toolbar to add and remove Lot/batch size ranges for the current chart. Use the **Unlimited** button in the toolbar to set a range to have no upper limit (this sets the **To** field to *Unlimited* for the selected row). <!-- KFM: explain what these do and how they affect the chart. Explain any rules that apply (no overlaps, continuous, etc.) -->

1. When you're done setting up the chart, select **Validate** in the Action Pane to validate the integrity of the data in the plan. The system checks your settings and if the chart is valid, it sets the **Validated** field to *Yes*. Only validated charts can be used for acceptance sampling.

<!-- KFM: What about the **Sampling size code letter chart** and **Acceptable quality limit chart** Action Pane buttons. What do they do and how to we understand and use the pages they open? I suppose they are somehow relevant here? We probably need a section about each of these.-->

## Set up a test for acceptance sampling

<!-- KFM: We already have a topic about QC tests ([Quality management tests](quality-tests.md)). Update that topic to mention the new Defect type setting (with link back to here). Use this section to just mention what is needed to acceptance sampling and then give a link to the existing topic for details/instructions. -->

To set up a test to be used in acceptance sampling, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Tests**.
1. Select **New** to create a new defect type and set the following fields:
    - **Test** – <!-- KFM: description needed -->
    - **Description** – <!-- KFM: description needed -->
    - **Type** – <!-- KFM: description needed -->
    - **Test instrument** – <!-- KFM: description needed -->
    - **Unit** – <!-- KFM: description needed -->
    - **Defect type** – Choose between the defect types as described in the previous section.

## Set up a test group for acceptance sampling

<!-- KFM: Intro needed. Briefly explain what test groups are and how they are used in acceptance sampling? Link to the existing topic [Quality management test groups](quality-test-groups.md) for more info) -->

To set up test groups for acceptance sampling, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test groups**.
1. Use the buttons on the Action Pane to add a new test group or edit a selected one. You can also delete existing test groups, but you can't delete a test group if it is currently being used in a quality association or if quality orders are tracked against it.
1. The upper grid establishes the header settings for each test group. Make the following settings here:
    - **Test group** – Enter a name for the test group.
    - **Description** – Enter a short description of the test group.

    > [!NOTE]
    > All other fields on the header are not required for acceptance sampling. <!-- KFM: not required, or do nothing? -->

1. With your new or selected test group still selected, go to the lower grid, which is the lines section of the test group. This is where you define the tests that are included in the test group. Add a line for each test that you want to include in the group and make the following settings for each line:
    - **Sequence** – Enter an integer value, that sets the sorting order of the tests in the group.
    - **Test** – Choose a test with an associated defect type. <!-- KFM: link (and/or explain) for more info about how to create tests and how to use them. -->

    > [!NOTE]
    > All other fields on the test group line are not required for acceptance sampling.  <!-- KFM: not required, or do nothing? -->

## Set up up item sampling for acceptance testing

<!-- KFM: Intro needed. Briefly explain what item sampling records are and how they are used in acceptance sampling? Link to the existing topic [Quality management item sampling](quality-item-sampling.md) for more info. -->

To set up item samplings for acceptance sampling, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Item sampling**.
1. Select **New** to create a new item sampling and set the following fields:
    - **Item sampling** – Identification of the item sampling.
    - **Description** – <!-- KFM: description needed -->
    - **Sampling Scope** – Use the default value: *Order*. <!-- KFM: Describe what this setting does and how to use each of its options -->
    - **Use acceptance sampling charts** – Select: *Single*. <!-- KFM: Describe what this setting does and how to use each of its options -->

1. On the **Acceptance sampling** FastTab, set the following required fields:
    - **Acceptance sampling chart name** – Select the sampling chart you want to use for this item sampling.
    - **Description** – <!-- KFM: Description needed. It's a bad thing that we have multiple fields with identical names in the UI. Maybe we can combine these into a single entry in this list and say something like "a **Description** field is provided under each filed on this FastTab. You can use these to add notes about each setting. -->
    - **Inspection level** – <!-- KFM: description needed -->
    - **Description** – <!-- KFM: again... -->
    - **Minor AQL%** – Enter the percentage value for the minor acceptable quality level. <!-- KFM: Percentage of what? What do we mean by "minor". What is the effect of this setting?  -->
    - **Description** – <!-- KFM: again... -->
    - **Major AQL%** – Enter the percentage value for the major acceptable quality level. <!-- KFM: Percentage of what? What do we mean by "major". What is the effect of this setting?  -->
    - **Description** – <!-- KFM: again... -->
    - **Critical AQL%** – Enter the percentage value for the critical acceptable quality level. <!-- KFM: Percentage of what? What do we mean by "critical". What is the effect of this setting?  -->
    - **Description** – <!-- KFM: again... -->

## Set up a quality association for acceptance sampling

<!-- KFM: Intro needed. What are we about to do and why? Link to existing topic [Quality associations](quality-associations.md). Review that topic to see if we should expand it after adding this feature, and maybe link back to here. -->

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Quality associations**.
1. On the Action Pane, select **New** to create a new quality association and fill out the required fields for references and conditions. <!-- KFM: we should list and describe these fields. -->
1. On the **Specifications** FastTab, set the following required fields:
    - **Test group** – Select a test group with tests defined for acceptance sampling.
    - **Item sampling** – Select an item sampling defined for acceptance sampling.

<!-- KFM: We should maybe have a topic that walks through the procedure for how to do the test, sort of like the video does. -->