---
title:  Acceptance sampling (preview)
description: Learn how to set up acceptance sampling to quality control products batches by inspecting representative samples.
author: johanho-ms
ms.author: johanho
ms.topic: how-to
ms.date: 04/11/2024
ms.custom:
ms.reviewer: kamaybac
ms.search.form:
---

# Acceptance sampling (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.46 GA -->

*Acceptance sampling* is a quality control method used to evaluate a batch of products by inspecting a representative sample. Instead of checking every item, a subset of items is examined to determine whether the entire lot meets predefined quality standards. This approach is widely used in manufacturing and supply chain operations to balance inspection effort with quality assurance. In many practical applications, sampled items are inspected for different types of defects, typically categorized as:

- **Critical defects** – Defects that could cause harm or render a product unsafe or unusable. Even a single critical defect may lead to rejection of the entire lot.
- **Major defects** – Defects that significantly reduce the usability or performance of a product but don't pose safety risks. A limited number of major defects may be acceptable depending on the sampling plan.
- **Minor defects** – Defects that don't affect a product's function or safety but may impact appearance or user satisfaction. A higher tolerance is usually allowed for minor defects.

Acceptance criteria are defined in advance, often using standards like ANSI/ASQ Z1.4 or ISO 2859-1, which specify how many defects of each type are permissible in a sample before the lot is rejected. This structured approach helps ensure consistent product quality while optimizing inspection resources.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Set up an acceptance sampling chart

<!-- KFM: Start by briefly explaining what an acceptance chart is and what to use it for. -->

The *acceptance sampling chart* is a collection of the following charts:

- Sampling size code letter chart
- Acceptable quality limit chart

The acceptance sampling chart also include the following supporting data for the charts:

- Inspection levels
- AQL indexes
- Lot/batch size ranges

Learn more about how to use the charts in the following video:

> [!VIDEO 1e6ef0b8-0c35-4560-9f2a-926da8a6fd9b]

To set up a chart, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Acceptance sampling chart**.
1. On the Action Pane, use the following buttons as required:

    - **New** – Add a new acceptance sampling chart.
    - **Delete** – Remove an existing sampling chart. (You can't delete a chart if quality orders use it or activities are tracked against it.)
    - **Validate** – Validate the integrity of the data in the plan.
    - **Load AQL chart template** – Load the all data needed for the acceptance sampling chart from a predefined template.
    - **Copy** – Copy data from another chart.
    - **Functions** – Options to import or export the chart in a json file format.

1. On the header of the new or selected chart, set the following fields:

    - **Acceptance sampling chart name** – Enter a name for the sampling chart.
    - **Description** – Enter a short description of the sampling chart.
    - **Validated** – Set the plan to the *Validated* state. Only plans in the *Validated* state can be used for acceptance sampling.

1. On the Action Pane in the **Inspection levels to include** tab, use the following buttons as required:

    - **Add** – Add a new inspection level.
    - **Remove** – Remove an existing inspection level.

1. On the Action Pane in the **AQL indexes to include** FastTab, use the following buttons as required:

    - **Add** – Add a new AQL index.
    - **Remove** – Remove an existing AQL index.

1. On the Action Pane in the **Lot/batch size ranges** FastTab, use the following buttons as required:

    - **Add** – Add a new inspection level.
    - **Remove** – Remove an existing inspection level.
    - **Unlimited** – Use this option to indicate that there is no upper limit for the range. The **To** field on the record is in this case prefield with the value *Unlimited*.

## Set up defect types

To setup defect types, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Defect types**.
1. Select **New** to create a new defect type and set the following fields:
    - **Defect type** – <!-- KFM: description needed -->
    - **Defect category** – <!-- KFM: description needed --> Choose between: *Critical*, *Major*, and *Minor*.
    - **Description** – <!-- KFM: description needed -->

> [!NOTE]
> In acceptance sampling, the defect types are typically named: *Critical*, *Major*, and *Minor*. <!-- KFM: So, these are the same as the values offered for the category? -->

## Setup test for acceptance sampling

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

To setup test groups used in acceptance sampling, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test groups**.
1. On the Action Pane, use the following buttons as required:

    - **New** – Create a new test group.
    - **Delete** – Remove an existing test group. (You can't delete a plan if quality orders use it or activities are tracked against it.)

1. On the header of the new or selected test group, set the following fields:

    - **Test group** – Enter a name for the test group.
    - **Description** – Enter a short description of the test group.

    > [!NOTE]
    > All other fields on the header are not required for acceptance sampling.

1. On the Action Pane in the lines section, use the following buttons to create the tests in the test group:
    - **Sequence** – Enter an integer value, that sets the sorting order of the tests in the group.
    - **Test** – Choose a test with an associated defect type.

    > [!NOTE]
    > All other fields on the test group line are not required for acceptance sampling.

## Set up up item sampling for acceptance testing

To set up item samplings for acceptance sampling, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Item sampling**.
1. Select **New** to create a new item sampling and set the following fields:
    - **Item sampling** – Identification of the item sampling.
    - **Description** – <!-- KFM: description needed -->
    - **Sampling Scope** – Use the default value: *Order*. <!-- KFM: Describe what this setting does and how to use each of its options -->
    - **Use acceptance sampling charts** – Select: *Single*. <!-- KFM: Describe what this setting does and how to use each of its options -->

1. On the **Acceptance sampling** FastTab, set the following required fields:
    - **Acceptance sampling chart name** – Select the sampling chart you want to use for this item sampling.
    - **Minor AQL%** – Enter the percentage value for the minor acceptable quality level. <!-- KFM: Percentage of what? What do we mean by "minor". What is the effect of this setting?  -->
    - **Major AQL%** – Enter the percentage value for the major acceptable quality level. <!-- KFM: Percentage of what? What do we mean by "major". What is the effect of this setting?  -->
    - **Critical AQL%** – Enter the percentage value for the critical acceptable quality level. <!-- KFM: Percentage of what? What do we mean by "critical". What is the effect of this setting?  -->

## Set up a quality association for acceptance sampling

<!-- KFM: Intro needed. What are we about to do and why? -->

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Quality associations**.
1. On the Action Pane, select **New** to create a new quality association and fill out the required fields for references and conditions. <!-- KFM: we should list and describe these fields. -->
1. On the **Specifications** FastTab, set the following required fields:
    - **Test group** – Select a test group with tests defined for acceptance sampling.
    - **Item sampling** – Select an item sampling defined for acceptance sampling.
