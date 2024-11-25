---
title: Production parameters for manufacturing execution 
description: Learn about the setup of Production parameters for manufacturing execution, including an outline on types of production jobs.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:  JmgProdParameters
ms.topic: how-to
ms.date: 06/28/2024
ms.custom: 
  - bap-template
---

# Production parameters for manufacturing execution

[!include [banner](../includes/banner.md)]

This article provides information about the setup of production parameters for manufacturing execution.

Manufacturing execution can be used to register time and item consumption on production jobs or projects. Before you start to use manufacturing execution for job registrations, you must set up various production parameters that define how and when registrations are posted during the production process. The settings of production parameters affect inventory management, production management, and cost calculation.

Before workers start to make registrations on production jobs, you should carefully consider all settings on the **Production order defaults** page. Go to **Production control** \> **Setup** \> **Manufacturing execution** \> **Production order defaults**. If your company uses the multisite functionality, you might want to set up different production parameters for each site. The following tabs are provided on the **Production order defaults** page:

- **General** – General parameter settings for production jobs.
- **Start** – Parameters that are used when production operations are started.
- **Operations** – Parameters that are applied to production operations and feedback about operations during the production process.
- **Report as finished** – Parameters that are used when items are reported as finished on the last operation of a production order.
- **Quantity validation** – Parameters that are used to validate start and feedback quantities on production orders.

## Types of production jobs

On the **Operations** tab, you select which types of production jobs require registration.

Typically, workers make registrations on setup jobs and process jobs. However, if job scheduling is applied, you can select other job types that workers must make registrations on when production orders are processed. For example, you can require registrations on transport jobs.

> [!IMPORTANT]
> Make sure that you select all relevant job types. Otherwise, jobs might not be available for registration. Your selections should match the selections in the **Job management** column on the **Setup** FastTab of the **Route groups** page (**Production control** \> **Setup** \> **Routes** \> **Route groups**).

If **Job management** is selected on the route group, this job type is reported as finished on the production order when a job is reported as finished. When all job types that **Job management** is selected for have been reported as finished on an operation, the operation is reported as finished.

> [!NOTE]
> Some job types can be manually reported through production journals. In this case, select **Job management** for the job type, but don't select the job type for registration on the **Operations** tab on the **Production order defaults** page.

## BOM consumption and picking list journals

A consistent setup for bill of materials (BOM) consumption is important because it helps guarantee that inventory management is efficient. For example, if BOM consumption parameters aren't set up correctly, materials might be deducted from inventory two times or not at all.

On the **Production order defaults** page, automatic BOM consumption is set up in three stages:

- At the start of a production. Set up this stage on the **Start** tab.
- During the production process when an operation is completed. Set up this stage on the **Operations** tab.
- When a production order is reported as finished. Set up this stage on the **Report as finished** tab.

For each stage, the **Automatic BOM consumption** field lets you select one of three methods for picking items for a production order:

- *Flushing principle* – This option is used in combination with an option that is defined for the BOM. Select **Production control** \> **Production orders** \> **All production orders**. On the **All production orders** page, select a production order in the list, and then, on the Action Pane, open the **Production order** tab and select **BOM**. On the **BOM** page, open the BOM line you want to set. Then open the **Setup** FastTab and select one of the following options in **Flushing principle** field:

    - *Start*
    - *Finish*
    - *Manual*
    - *Available at location*
    - Blank (No option is selected.)

    If *Flushing principle* is selected in the **Automatic BOM consumption** field on the **Start** tab of the **Production order defaults** page, all materials that are set to *Start* in the BOM are deducted from inventory when the operation is started. The *Available at location* option is used for products that are enabled for warehouse management processes (WMS). If you select this flushing principle, material is flushed when warehouse work for raw material picking is completed. Material is also flushed when a BOM line that uses this flushing principle is released to warehouse and the material is available at the production input location.

    > [!NOTE]
    > If *Flushing principle* is selected in the **Automatic BOM consumption** field on the **Start** tab of the **Production order defaults** page, you must select the same value on either the **Operations** tab or the **Report as finished** tab. This requirement helps guarantee that materials are deducted from inventory on BOMs that use *Finish* as a flushing principle on the production order. If *Flushing principle* isn't selected on either the **Operations** tab or the **Report as finished** tab, materials might be deducted from inventory two times.

- *Always* – If you select this option for a stage, materials are always deducted from inventory at that stage. For example, materials for the production are deducted when the production order is started. This setting requires that *Never* be selected on the **Operations** and **Report as finished** tabs. This requirement helps prevent items from being deducted from inventory two times.
- *Never* – If you select this option for a stage, no BOM consumption occurs at that stage. For example, if you select *Never* on all three tabs (**Start**, **Operations**, and **Report as finished**), materials must be manually deducted from inventory.

> [!IMPORTANT]
> Carefully consider your setup of the production order defaults, and make sure that the defaults that are selected on the various tabs of the **Production order defaults** page don't contradict each other.

The following examples illustrate parameter settings that support various BOM consumption principles. The parameters are set up on the **Production order defaults** page.

### Example 1: Backflushing on operations

Use the following settings if picking list journals and BOM item consumption should be generated when items are reported as finished on an operation.

| Tab | Field | Setting |
|--|--|--|
| **Start** | **Update start on-line** | *Status* or *Status + quantity* |
| **Start** | **Automatic BOM consumption** | *Never* |
| **Operations** | **Automatic BOM consumption** | *Always* |
| **Report as finished** | **Automatic BOM consumption** | *Never* |
| **Report as finished** | **Update finished report on-line** | *Status + quantity* |

### Example 2: Backflushing on production

Use the following settings if picking list journals and BOM item consumption should be generated when items are reported as finished on the production order.

| Tab | Field | Setting |
|--|--|--|
| **Start** | **Update start on-line** | *Status* or *Status + quantity* |
| **Start** | **Automatic BOM consumption** | *Never* |
| **Operations** | **Automatic BOM consumption** | *Never* |
| **Report as finished** | **Automatic BOM consumption** | *Always* |
| **Report as finished** | **Update finished report on-line** | *Status + quantity* |

### Example 3: Flushing principle

Use the following settings if picking list journals and BOM item consumption should be generated according to the flushing principle that is set for the BOM items.

| Tab | Field | Setting |
|--|--|--|
| **Start** | **Update start on-line** | *Status + quantity* |
| **Start** | **Automatic BOM consumption** | *Flushing principle* |
| **Operations** | **Automatic BOM consumption** | *Flushing principle* |
| **Report as finished** | **Automatic BOM consumption** | *Never* |
| **Report as finished** | **Update finished report on-line** | *Status + quantity* |

### Example 4: Deduction of materials during startup of a production order

Use the following settings if picking list journals and BOM item consumption should be generated when a production is started.

| Tab | Field | *Setting* |
|--|--|--|
| **Start** | **Update start on-line** | *Status + quantity* |
| **Start** | **Automatic BOM consumption** | *Always* |
| **Operations** | **Automatic BOM consumption** | *Never* |
| **Report as finished** | **Automatic BOM consumption** | *Never* |
| **Report as finished** | **Update finished report on-line** | *Status* or *Status + quantity* |

Based on the selections that are described earlier in this section, picking list journals are posted at various stages of the production order process:

- When an operation is started
- When quantity feedback is reported on an operation
- When items are reported as finished on the production order

### Example 5: Manual BOM consumption

You can use the following settings if materials should always be manually deducted from inventory. In this case, picking list journals aren't posted.

| Tab | Field | Setting |
|--|--|--|
| **Start** | **Update start on-line** | *Status* |
| **Start** | **Automatic BOM consumption** | *Never* |
| **Operations** | **Automatic BOM consumption** | *Never* |
| **Report as finished** | **Automatic BOM consumption** | *Never* |
| **Report as finished** | **Update finished report on-line** | *Status* |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
