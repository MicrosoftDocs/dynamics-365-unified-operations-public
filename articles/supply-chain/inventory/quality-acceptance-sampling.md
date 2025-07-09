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

Acceptance criteria are defined in advance, often using standards like ANSI/ASQ Z1.4 or ISO 2859-1, which specify how many defects of each category are permissible in a sample before the lot is rejected. This structured approach helps ensure consistent product quality while optimizing inspection resources. 

In acceptance sampling, single and double sampling plans represent two different strategies for determining whether a lot meets quality standards. A single sampling plan involves selecting and inspecting one sample from the lot. Based on the number of defects found, the lot is either accepted or rejected. This method is straightforward and commonly used when simplicity and speed are important. A double sampling plan introduces a second step. If the first sample yields an inconclusive result, a second sample is taken. The final decision is then based on the combined results of both samples. This strategy can reduce inspection effort over time while maintaining decision accuracy. In this solution, only the single sampling strategy is supported, meaning each lot is evaluated using one sample and a fixed acceptance threshold.

Acceptance sampling uses the following two charts to validate if a lot has passed or failed: **Sampling code letter chart** and **Acceptable quality limit chart**. In the Sampling code letter chart, a code letter is found based on the lot size to inspect and the selected inspection level chosen by the user. An inspection level is a code or category that indicates the extent of inspection based on the importance of the product, the production history, and customer requirements. The inspection level is divided into the following two categories: General inspection level and Special inspection level. General inspection levels are used for routine, more thorough inspections, while special inspection levels apply to less critical checks with smaller sample sizes. By using the lot size range and a chosen inspection level, the user can find the code letter. The code letter found is now used as input to the Acceptable quality limit chart. In the acceptable quality limit chart, the code letter found is used in combination with the AQL indexes. The AQL indexes are determined by the business user and are based on how critical the product is, industry standards, customer requirements, and the acceptable level of risk. Lower indexes are used for high-risk or critical items, while higher AQLs are acceptable for less critical products where some defects are tolerable. Businesses can, for example, use index 0.1% for testing for critical defects, 0.65% for major defects, and 2.5% for minor defects. With the use of the code letter and the AQL index, the sample size and acceptable quality levels can be found. Using the example from the acceptable quality limit chart, using code letter G with an AQL index of 2.5%, up to two defects will be accepted for the lot to pass, but three or more defects will cause the lot to fail inspection. If the code letter G is used for AQL index 0.65%, then the arrow in the chart indicates that an AQL level for a different code letter should be used. In this case, the code letter with the nearest AQL values is F, which has a different sample size than code letter G, and zero defects will be accepted for the lot to pass.

In Dynamics Supply Chain Management, all the data for generating the sampling code letter chart and the acceptable quality limit chart can be loaded from a template. This routine includes the generation of inspection levels, AQL indexes, and lot size ranges. Once these values are loaded from the template, business users can make changes as required to the loaded data. 

In Dynamics Supply Chain Management, a quality order is used to perform testing based on acceptance sampling. To enable this functionality, you must first define an appropriate Item sampling method that supports acceptance sampling. An item sampling in Dynamics Supply Chain Management defines how much of a product should be inspected during a quality order. It specifies the sample quantity or percentage to be tested from a lot, and is essential for enabling acceptance sampling in quality control processes. Learn more about item sampling here: [Quality management item sampling](quality-item-sampling.md). When the item sampling method is defined, associate it to a quality association. A quality association in Dynamics Supply Chain Management is a rule that automatically triggers a quality order based on specific events, such as product receipt, production output, or inventory movement. It links a product, process, or condition to a quality inspection requirement, ensuring consistent and automated quality control. Learn more about quality associations here: [Quality associations](quality-associations.md). 

When a quality order is triggered based on an event defined in a quality association, the system automatically creates a quality order that can be used for acceptance sampling. The quality association links the triggering event—such as a product receipt or production output—to a specific test process. If the associated item sampling is configured for acceptance sampling, the generated quality order will use the defined sampling criteria to determine how much of the lot should be inspected.

On the quality order for acceptance sampling, the different categories of tests (critical, major, and minor), their sample sizes, and acceptable quality levels are clearly indicated. If a test falls outside a quality level, then the entire quality order will fail during validation. 


[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.45 or later.
- The feature that is named *(Preview) Acceptance sampling* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

<!-- KFM: any other prerequisites? -->

## Set up defect types

First, define the types of defects that the users will be testing for when using acceptance sampling. 

To set up defect types, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Defect types**.
1. Select **New** to create a new defect type and set the following fields:
    - **Defect type** – Identification of the types of defects defect the users will test for such as *paint chipped*, *screen cracked*, *packaging damaged*, etc. 
    - **Description** – Elaborated description of the defect type.
    - **Defect category** –  Categorize the defect type with one of the three following fixed categories:
        - *Critical** – Could cause harm or render a product unsafe or unusable. Even a single critical defect may lead to rejection of the entire lot.
        - *Major** – Significantly reduces the usability or performance of a product but don't pose safety risks. A limited number of major defects may be acceptable depending on the sampling plan.
        - *Minor** – Doesn't affect function or safety but may impact appearance or user satisfaction. A higher tolerance is usually allowed for minor defects

## Set up inspection levels

An inspection level is a code or category that indicates the extent of inspection based on the importance of the product, the production history, and customer requirements. It is used as input to the code letter chart, and guides how many samples you take from a lot. 

To set up inspection levels, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Inspection levels**.
1. Select **New** to create a new inspection level and set the following fields:
    - **Inspection level** – <!-- KFM: description needed -->
    - **Inspection level type** – <!-- KFM: description needed -->
    - **Description** – <!-- KFM: description needed -->

## Set up acceptance sampling indexes

<!-- KFM: Explain what these are, how they are used, and how to set them up. -->

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Acceptance sampling indexes**.
1. Select **New** to create a new inspection level and set the following fields:
    - **Acceptable quality limit index** – <!-- KFM: description needed -->
    - **Description** – <!-- KFM: description needed -->

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

1. On the **AQL indexes to include** FastTab, use the buttons in the toolbar to add and remove AQL indexes for the current chart. <!-- KFM: explain what these do, where they come from, and how they affect the chart. This is a lookup--how do we manage these? What do they mean? Are these the same as "acceptance sampling indexes"? -->

1. On the **Lot/batch size ranges** FastTab, use the buttons in the toolbar to add and remove lot/batch size ranges for the current chart. Use the **Unlimited** button in the toolbar to set a range to have no upper limit (this sets the **To** field to *Unlimited* for the selected row). <!-- KFM: explain what these do and how they affect the chart. Explain any rules that apply (no overlaps, continuous, etc.) -->

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

<!-- KFM: Intro needed. Briefly explain what test groups are and how they are used in acceptance sampling. Link to the existing topic [Quality management test groups](quality-test-groups.md) for more info) -->

To set up test groups for acceptance sampling, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test groups**.
1. Use the buttons on the Action Pane to add a new test group or edit a selected one. You can also delete existing test groups, but you can't delete a test group if it is currently being used in a quality association or if quality orders are tracked against it.
1. The upper grid establishes the header settings for each test group. Make the following settings here:
    - **Test group** – Enter a name for the test group.
    - **Description** – Enter a short description of the test group.

    > [!NOTE]
    > All other fields on the header don't affect acceptance sampling.

1. With your new or selected test group still selected, go to the lower grid, which is the lines section of the test group. This is where you define the tests that are included in the test group. Add a line for each test that you want to include in the group and make the following settings for each line:
    - **Sequence** – Enter an integer value, that sets the sorting order of the tests in the group.
    - **Test** – Choose a test with an associated defect type. <!-- KFM: link (and/or explain) for more info about how to create tests and how to use them. -->

    > [!NOTE]
    > All other fields on the test group line don't affect acceptance sampling.

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

<!-- KFM: It looks like we have a new **Acceptance sampling** tab on the **Quality orders** page. We should describe that somewhere. Link to and maybe also update [Quality orders](quality-orders.md) -->