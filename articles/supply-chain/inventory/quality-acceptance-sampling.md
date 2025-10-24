---
title:  Acceptance sampling (preview)
description: Learn how to set up acceptance sampling to control product quality by inspecting representative samples from lots.
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

*Acceptance sampling* is a quality control method that uses statistical analysis to evaluate a batch or lot of products. Instead of checking every item, you examine a subset of items to determine whether the entire lot meets predefined quality standards. This approach is widely used in manufacturing and supply chain operations to balance inspection effort with quality assurance.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Acceptance sampling overview

### Defect types and categories

In many practical applications, you inspect sampled items for different *types* of defects. Each defect type typically falls into one of the following *categories*:

- **Critical defects** – Might cause harm or render a product unsafe or unusable. Even a single critical defect can lead to rejection of the entire lot.
- **Major defects** – Significantly reduce the usability or performance of a product but don't pose safety risks. A limited number of major defects might be acceptable depending on the sampling plan.
- **Minor defects** – Don't affect a product's function or safety but might impact appearance or user satisfaction. A higher tolerance is usually allowed for minor defects.

You define acceptance criteria in advance, often using standards like ANSI/ASQ Z1.4 or ISO 2859-1. These standards specify permissible defects count per category before rejecting a lot. This structured, statistically supported approach ensures consistent product quality while optimizing inspection resources.

### Single and double sampling plans

Single and double sampling plans use two different strategies to decide if a lot meets quality standards.

- **Single sampling plan** – You inspect one sample from the lot. Based on the number of defects found, you either accept or reject the lot. Use this method when simplicity and speed are important.
- **Double sampling plan** – If the first sample gives an inconclusive result, you take a second sample. You base the final decision on the combined results of both samples. This strategy can reduce inspection effort over time while maintaining decision accuracy.

The current version of Supply Chain Management supports only the single sampling strategy, where each lot is evaluated by using one sample and a fixed acceptance threshold.

### Acceptance sampling charts

Acceptance sampling uses a chart with the following two components to validate whether a lot passes or fails an inspection:

- **Sampling code letter chart** – Defines code letters for each combination of lot size and inspection level.
- **Acceptable quality limit (AQL) chart** – Uses the code letter and AQL index to determine sample size and defect thresholds.

An *inspection level* is a code or category defined by a business user. It indicates the extent of inspection based on the importance of the product, the production history, and customer requirements. There are two categories of inspection levels:
    - *General inspection level* – Used for routine, thorough inspections
    - *Special inspection level* – Apply to less critical checks with smaller sample sizes.

The following image shows an example of a code letter chart. In this example, if you have a lot size between 151 and 280 and use a general inspection level II, then use code letter G as input in the acceptable quality limit chart.

:::image type="content" source="media/code-letter-chart.jpg" alt-text="Example of a code letter chart" lightbox="media/code-letter-chart.jpg":::

The AQL chart defines the acceptable quality level for each combination of sampling code letter and AQL index. Business users determine the AQL indexes based on how critical the product is, industry standards, customer requirements, and the acceptable level of risk. Lower indexes are used for high-risk or critical items, while higher AQLs are acceptable for less critical products where some defects are tolerable. For example, businesses can use index 0.1% for testing for critical defects, 0.65% for major defects, and 2.5% for minor defects. The selected code letter and AQL index resolve to find the sample size and acceptable quality level for the test.

The following image shows an example of an acceptable quality limit chart. In this example, if you use code letter G with an AQL index of 2.5%, then the sample size should be 32 units and up to two defects are accepted for the lot to pass, but three or more defects cause the lot to fail inspection. If you use code letter G for AQL index 0.65%, then the arrow in the chart indicates that an AQL level for a different code letter should be used. In this case, the code letter with the nearest AQL values is F, which has a different sample size than code letter G (so 20 units should be tested instead of 32), and zero defects are accepted for the lot to pass.

:::image type="content" source="media/sampling-plan-chart.jpg" alt-text="Example of an acceptable quality limit chart" lightbox="media/sampling-plan-chart.jpg":::

In Supply Chain Management, you can load all the data for generating the sampling code letter chart and the acceptable quality limit chart from a template. The template generates inspection levels, AQL indexes, and lot size ranges. After you load these values from the template, you can customize the charts as needed.

You can learn more about how to use the charts in the following video:

> [!VIDEO bb27c2c0-ffda-4768-9d06-2ca67c05d508]

<a name="orders-methods-associations"></a>

### Quality orders, item sampling methods, and quality associations

Supply Chain Management uses *quality orders* to schedule and manage testing based on acceptance sampling. To enable this functionality, you must define an appropriate item sampling method that supports acceptance sampling.

Item sampling methods define how much of a product you should inspect during a quality order. They specify the sample quantity or percentage to test from a lot, and are essential for enabling acceptance sampling in quality control processes. Learn more in [Quality management item sampling](quality-item-sampling.md).

Item sampling methods take effect when you assign them to *quality associations*. Supply Chain Management uses quality associations to establish and apply rules that automatically trigger a quality order based on specific events, such as product receipt, production output, or inventory movement. Each quality association links a product, process, or condition to a quality inspection requirement, ensuring consistent and automated quality control. Learn more in [Quality associations](quality-associations.md).

When a quality order is triggered based on an event defined in a quality association, the system automatically creates a quality order that you can use for acceptance sampling. The quality association links the triggering event (such as a product receipt or production output) to a specific test process. If the associated item sampling record is configured for acceptance sampling, the generated quality order uses the defined sampling criteria to determine how much of the lot you should inspect.

On the quality order for acceptance sampling, the various categories of tests (critical, major, and minor), their sample sizes, and acceptable quality levels are clearly indicated. If a test falls outside a quality level, the entire quality order fails during validation.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.45 or later.
- The feature named *Acceptance sampling* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up acceptance sampling charts

To set up your acceptance sampling charts, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Acceptance sampling chart**.
1. Use the buttons on the Action Pane to add a new chart or edit an existing one.
1. On the header of the new or selected chart, set the following fields:
    - **Acceptance sampling chart name** – Enter a name for the sampling chart.
    - **Description** – Enter a short description of the sampling chart.

1. On the Action Pane, select **Save**.
1. To get started quickly, you can either copy an existing chart or load a predefined template. If you choose to do so, select one of the following options in the Action Pane. Note that all the settings for the current chart (except name and description) are replaced with the template or copied chart.
    - **Load AQL chart template** – Load all required data from a predefined JSON file. The content of the file aligns with the ANSI/ASQ Z1.4 or ISO 2859-1 standards.
    - **Copy** – Copy data from another chart. The system asks you to choose an existing chart.

1. On the **Inspection levels to include** FastTab, use the buttons in the toolbar to add and remove inspection levels for the current chart. The inspection levels are used as a criteria to find the applicable code letter in the code letter chart. Learn more about inspection levels in [Acceptance sampling charts](#acceptance-sampling-charts).

1. On the **AQL indexes to include** FastTab, use the buttons in the toolbar to add and remove AQL indexes. The AQL index defines the maximum acceptable defect rate in a sample that determines whether a lot passes or fails inspection. You can learn about AQL indexes in [Acceptance sampling charts](#acceptance-sampling-charts).

1. On the **Lot/batch size ranges** FastTab, use the buttons in the toolbar to add and remove lot size ranges for the current chart. Use the **Unlimited** button in the toolbar to set a range to have no upper limit (this sets the **To** field to *Unlimited* for the selected row). The lot size ranges group total units in a lot and help find the applicable code letter. Learn more about lot size ranges in [Acceptance sampling charts](#acceptance-sampling-charts).

1. When you're done setting up the chart, select **Validate** in the Action Pane to check data integrity. If the chart is valid, it sets the **Validated** field to *Yes*. Only validated charts can be used for acceptance sampling.

    > [!TIP]
    > Validated charts are locked and can't be edited. If you need to edit a validated chart, select **Invalidate** from the Action Pane, make the required changes, and then validate the chart again.

## Set up inspection levels and acceptance sampling indexes

If you don't use the option to load your charts from a template, you must create the inspection levels and sampling indexes manually.

### Set up inspection levels

Follow these steps to create inspection levels manually:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Inspection levels**.
1. Select **New** to create a new inspection level and set the following fields:
    - **Inspection level** – The identification of the inspection level.
    - **Inspection level type** – Choose between the two types *General* or *Special*, which are used as a criteria to find the code letter in the code letter chart. Learn more about level designations in [Acceptance sampling charts](#acceptance-sampling-charts).
    - **Description** – User defined description of the inspection level.

1. On the Action Pane, select **Save**.

### Set up acceptance sampling indexes

Business users determine AQL indexes based on how critical the product is, industry standards, customer requirements, and the acceptable level of risk. If you don't want to use the option to generate the AQL indexes by loading the AQL chart template, then you can use the following steps to create them manually:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Acceptance sampling indexes**.
1. Select **New** to create a new inspection level and set the following fields:
    - **Acceptable quality limit index** – The identification of the acceptance sampling index. The AQL index defines the maximum acceptable defect rate in a sample that determines whether a lot passes or fails inspection.
    - **Description** – User defined description of the acceptance sampling index.

1. On the Action Pane, select **Save**.

## View the sampling size code letter chart

After you create and validate an acceptance sampling chart, you can view the sampling size code letter chart:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Acceptance sampling chart**.
1. Select the chart you want to view.
1. On the Action Pane, select **Sampling size code letter chart**. You can open the corresponding acceptable quality limit chart by selecting **Acceptable quality limit chart**.

## View or edit the acceptable quality limit chart

To view or edit the acceptable quality limit chart, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Acceptance sampling chart**.
1. Select the chart you want to edit.
1. On the Action Pane, select *Acceptable quality limit chart* to open the chart.
1. Use the following options to make edits:
    - **Up** – Adds an upward arrow in the selected cell, indicating the direction to find the AQL level and sample size. Learn more in [Acceptance sampling charts](#acceptance-sampling-charts).
    - **Down** – Adds a downward arrow in the selected cell, indicating the direction to find the AQL level and sample size. Learn more in [Acceptance sampling charts](#acceptance-sampling-charts).  
    - **Accept** – Sets the acceptance level in the selected cell, defining the maximum number of defects allowed for a given sample size and AQL index. Learn more in [Acceptance sampling charts](#acceptance-sampling-charts).

## Set up defect types

Defect types identify the types of defects that users test for, such as *paint chipped*, *screen cracked*, *packaging damaged*, and so on. Each defect type is categorized as *Critical*, *Major*, or *Minor*.

To set up defect types, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Defect types**.
1. Select **New** and set the following fields:
    - **Defect type** – Identify the type of defect to test for.
    - **Description** – Enter a detailed description of the defect type.
    - **Defect category** –  Categorize the defect type with one of the three following fixed categories:
        - *Critical* – Could cause harm or render a product unsafe or unusable. Even a single critical defect might lead to rejection of the entire lot.
        - *Major* – Significantly reduces the usability or performance of a product but don't pose safety risks. A limited number of major defects might be acceptable depending on the sampling plan.
        - *Minor* – Doesn't affect function or safety but might impact appearance or user satisfaction. A higher tolerance is usually allowed for minor defects

## Set up a test for acceptance sampling

You must define each of the tests that you want to use on quality orders, and each test must be associated with one of the defect types that  you set up in the previous section. Learn more about tests for quality orders in [Quality management tests](quality-tests.md).

## Set up a test group for acceptance sampling

Each of the tests that you use for acceptance sampling must be associated with a *test group*. A test group is a collection of tests needed on a quality order. Each quality association has an assigned test group, which it uses to automatically generate quality orders. Learn more about test groups in [Quality management test groups](quality-test-groups.md)

## Set up item sampling for acceptance testing

Use *item sampling* records to define how much of a product to inspect during a quality order. Each record specifies the sample quantity or percentage to test from a lot. These records are essential for enabling acceptance sampling in quality control processes. Learn more about item sampling in [Quality orders, item sampling methods, and quality associations](#orders-methods-associations) and [Quality management item sampling](quality-item-sampling.md).

To set up item sampling for acceptance sampling, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Item sampling**.
1. Select **New** to create a new item sampling and set the following fields:
    - **Item sampling** – Enter a name for the item sampling record.
    - **Description** – Enter a short description of the item sampling record.
    - **Sampling scope** – Select the scope to use when evaluating if quality work should be created. When set to *Shipment* or *Load*, those entities are used if available. If not, the *Order* is used. When you use acceptance sampling charts, the only supported sampling scope is *Order*.
    - **Use acceptance sampling charts** – Choose one of the following options:
        - *Single* – Use acceptance sampling. This value indicates that you'll use a single sampling plan. Learn more in [Single and double sampling plans](#single-and-double-sampling-plans).
        - *None* – Don't use acceptance sampling for quality inspection.

1. On the **Acceptance sampling** FastTab, set the following required fields:
    - **Acceptance sampling chart name** – Select the sampling chart you want to use for this item sampling.
    - **Description** – Displays the name of the selected acceptance sampling chart.
    - **Inspection level** – Select the inspection level you want to use for this item sampling. Learn more about the use of inspection levels in [Acceptance sampling charts](#acceptance-sampling-charts).
    - **Description** – Displays the description of the selected AQL index.
    - **Minor AQL%** – Enter the AQL index for minor defects for the item sampling. Learn more about how to use AQL indexes in [Acceptance sampling charts](#acceptance-sampling-charts).
    - **Description** – Displays the description of the selected AQL index.
    - **Major AQL%** – Enter the AQL index for major defects for the item sampling. Learn more about AQL indexes in [Acceptance sampling charts](#acceptance-sampling-charts).
    - **Description** – Displays the description of the selected AQL index.
    - **Critical AQL%** – Enter the AQL index for critical defects for the item sampling. Learn more about AQL indexes in [Acceptance sampling charts](#acceptance-sampling-charts).
    - **Description** – Displays the description of the selected AQL index.

## Set up a quality association for acceptance sampling

Supply Chain Management uses quality associations to define and apply rules that automatically trigger a quality order based on specific events, such as product receipt, production output, or inventory movement. Each quality association links a product, process, or condition to a quality inspection requirement, ensuring consistent and automated quality control. Learn more in [Quality associations](quality-associations.md).

When an event defined in a quality association triggers a quality order, the system automatically creates a quality order that you can use for acceptance sampling. The quality association links the triggering event (such as a product receipt or production output) to a specific test process. If the associated item sampling is configured for acceptance sampling, the generated quality order uses the defined sampling criteria to determine how much of the lot you should inspect.

To set up a quality association for acceptance sampling, follow the instructions in [Quality associations](quality-associations.md). When you set up your quality associations on the **Quality associations** page, pay special attention to the following settings, which are specific to acceptance sampling:

- Use the **Item sampling** field on the **Specifications** FastTab to select an item sampling record. Choose an item sampling record that's configured to use acceptance sampling charts. This setting is required to enable acceptance sampling for the quality association.
- Use the **Test group** field on the **Specifications** FastTab to select a test group that contains the tests you want to use for acceptance sampling. The test group must contain tests that are associated with defect types that you set up in [Set up defect types](#set-up-defect-types). The test group can include at most one of each defect type.

## Using acceptance sampling on quality orders

Quality orders created for acceptance sampling include an **Acceptance sampling** tab on the **Quality orders** page. This tab contains a grid with line items for each test that you need to conduct. The grid provides the following information:

- **Defect category** – Indicates one of the three fixed categories of the test: *Critical*, *Major*, or *Minor*.
- **Defect type** – Indicates the type of the test defined in the configuration. Learn more in [Set up defect types](#set-up-defect-types).
- **Acceptable quality level index** – Indicates the AQL index for the specific test as specified in the configuration of the item sampling for the quality order.
- **Sample size** – The number of items to test.
- **Target Ac** – Maximum number of defects accepted for the test to pass.
- **Target Re** – Minimum number of defects for the test to fail.
- **Test result** – Graphical indication of whether the test passed or failed.

To record test results for a selected quality order, either enter them directly into the test lines or select **Quick results entry** from the Action Pane to use the [quick-entry form](quality-quick-results-entry.md).
