---
# required metadata

title: Production parameters in manufacturing execution 
description: This topic provides information about production parameter setup in the Manufacturing execution. 
author: johanhoffmann
manager: AnnBe
ms.date: 06/16/2017
ms.topic: 
ms.prod: 
ms.service: 
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: global
ms.industry: Manufacturing
ms.author: johanhoffmann
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Production parameters in manufacturing execution

This topic provides information about production parameter setup in the Manufacturing execution. 

The **Manufacturing execution** module is primarily targeted at manufacturing companies. It can be used to register time and item consumption on production jobs or projects. Before you start to use the module for job registrations, you must first set up various production parameters that define how and when registrations are posted in the production process. Production parameter settings affect inventory management, production management, and cost calculation.

You should carefully consider all settings in the **Production parameters** form before workers start making registrations on production jobs. Click **Production control** &gt; **Setup** &gt; **Manufacturing execution** &gt; **Production parameters**. If your company uses the multisite functionality, you may want to set up different production parameters by site. The parameters for integrating to the **Production** module are set up on the following tabs in the **Production parameters** page:

-   **General** - General parameter settings for production jobs in **Manufacturing execution**.
-   **Start** - Parameters that are used when production operations are started.
-   **Operations** - Parameters that are applied to production operations and feedback on operations during the production process.
-   **Report as finished** - Parameters that are applied when items are reported as finished on the last operation of a production order.
-   **Quantity validation** - Parameters for validating start and feedback quantities on production orders.

## Types of production jobs
On the **Operations** tab, you select which types of production jobs require registration on the **Job registration** page.

Typically, workers make registrations on setup jobs and process jobs. But if job scheduling is applied, you can select other job types, for example transport jobs, on which workers must also make registrations when processing a production order.

> [!IMPORTANT]
> Make sure that all relevant job types are selected. Otherwise, jobs may not be available for registration in the **Job registration** form. Align your selections with selections made in the **Job management** column in the **Route groups** form. Click **Production control** &gt; **Setup** &gt; **Routes** &gt; **Route groups**. Then select the **Setup** tab. 

If **Job management** is selected on the route group, this job type will be reported as finished on the production order. This will occur when the job is reported as finished in **Manufacturing execution**. When all job types for which **Job management** is selected have been reported as finished on an operation, **Manufacturing execution** will also report the operation as finished.

> [!NOTE]
> Some job types may be reported manually through production journals. If that is the case, select **Job management** for this job type, but do not select the job type for registration on the **Operations** tab in the **Production parameters** form in **Manufacturing execution**. 

## BOM consumption and picking list journals
It is important that the BOM consumption setup is consistent to make sure that inventory management is efficient. For example, if BOM consumption parameters are not set up correctly in **Manufacturing execution**, it may result in materials deducted from inventory two times or not at all.

In the **Production parameters** form, **Automatic BOM consumption** is set up in three stages:
-   At the start of a production. Set this up on the **Start** tab.
-   During the production process when an operation is completed. Set this up on the **Operations** tab.
-   When a production order is reported as finished. Set this up on the **Report as finished** tab.

For each of the three stages, there are three methods for picking items for a production order in the **Automatic BOM consumption** field:

1.  **Flushing principle** – This option is used in combination with an option defined in the BOM in the Production module. Click **Production control** &gt; **Common** &gt; **Production orders** &gt; **All production orders**. From the **All production orders** form, select a production order from the list and in the Action Pane, click the **BOM** button. From the **BOM** form, click the **Setup** tab, **Flushing principle** field. The **Flushing principle** options in **Production** are as follows:

    -   **Start**
    -   **Finish**
    -   **Manual**
    -   Blank – No option is selected.
    -   **Available at location**

In the **Manufacturing execution** module, if **Flushing principle** is selected on the **Start** tab in the **Automatic BOM consumption** field, it means that all materials set to the **Start** value in the BOM will be deducted from inventory when the operation is started.
    
> [!NOTE]
> If the **Flushing principle** field is selected on the **Start** tab in **Manufacturing execution**, you must also select that same principle on either the **Operations** tab or the **Report as finished** tab. This is to make sure that materials are deducted from inventory on the BOMs that use **Finish** as a flushing principle on the production order. It is important that either the **Operations** tab or the **Report as finished** tab – contains the **Flushing principle** selection. This is to prevent materials from being deducted two times from inventory. 

In the BOM, the deduction of materials from inventory is based on the value set on every item. This value is mandatory for all items created in Microsoft Dynamics AX. This occurs when the **Flushing principle** is set to “blank”, and you have selected **Flushing principle** on, for example, the **Start** tab and the **Operations** tab in the **Production parameters** form in **Manufacturing execution**.
    
2.  **Always** – If you select this option at a particular stage, materials are always deducted from inventory at that stage. For example, materials for the production will be deducted when the production order is started. This setting requires a “Never” selection on the **Operations** and **Report as finished** tabs. This will prevent items from being deducted two times from inventory.

3.  **Never** – This means no BOM consumption occurs at a particular stage. For example, if “Never” is selected on all three **Start**, **Operations**, and **Report as finished** tabs, materials must be deducted manually from inventory.

> [!IMPORTANT]
> Carefully consider your production parameter setup and make sure that the parameters selected on different tabs in the **Production parameters** form do not contradict each other. 

The following examples illustrate parameter settings that support different BOM consumption principles. The parameters are set up in the **Production parameters** form in **Manufacturing execution**.

### Example 1 - Backflushing on operations

Use the following settings if picking list journals and BOM item consumption should be generated when items are reported as finished on an operation.

| Tab / Field                                                 | Setting                             |
|-------------------------------------------------------------|-------------------------------------|
| **Start** <br> **Update start on-line**                        | **Status** or **Status + quantity**<br> |
| **Start** <br> **Automatic BOM consumption**                   |  **Never**<br>                           |
| **Operations** <br> **Automatic BOM consumption**              | **Always**<br>                          |
| **Report as finished** <br> **Automatic BOM consumption**      | **Never**<br>                           |
| **Report as finished** <br> **Update finished report on-line** | **Status + quantity**               |

### Example 2 - Backflushing on production

Use the following settings if picking list journals and BOM item consumption should be generated when items are reported as finished on the production order.

| Tab / Field                                                 | Setting                             |
|-------------------------------------------------------------|-------------------------------------|
| **Start** <br> **Update start on-line**                        | **Status** or **Status + quantity**<br> |
| **Start** <br> **Automatic BOM consumption**                   | **Never**<br>                           |
| **Operations** <br> **Automatic BOM consumption**              | **Never**<br>                           |
| **Report as finished** <br> **Automatic BOM consumption**      | **Always**<br>                          |
| **Report as finished** <br> **Update finished report on-line** | **Status + quantity**               |

### Example 3 - Flushing principle

Use the following settings if picking list journals and BOM item consumption should be generated according to the flushing principle setting of the BOM items.

| Tab / Field                                                 | Setting                       |
|-------------------------------------------------------------|-------------------------------|
| **Start** <br> **Update start on-line**                        | **Status + quantity**<br>  |
| **Start** <br> **Automatic BOM consumption**                   | **Flushing principle**<br> |
| **Operations** <br> **Automatic BOM consumption**              | **Flushing principle**<br> |
| **Report as finished** <br> **Automatic BOM consumption**      | **Never**<br>              |
| **Report as finished** <br> **Update finished report on-line** | **Status + quantity**  |

### Example 4 – Deducting materials during start-up of a production order

Use the following settings if picking list journals and BOM item consumption should be generated when a production is started.

| Tab / Field                                                 | Setting                             |
|-------------------------------------------------------------|-------------------------------------|
| **Start** <br> **Update start on-line**                        | **Status + quantity**<br>               |
| **Start** <br> **Automatic BOM consumption**                   | **Always**<br>                          |
| **Operations** <br> **Automatic BOM consumption**              | **Never**<br>                           |
| **Report as finished** <br> **Automatic BOM consumption**      | **Never**<br>                           |
| **Report as finished** <br> **Update finished report on-line** | **Status** or **Status + quantity** |

Based on the selections described earlier in this section, picking list journals are posted at various stages of the production order process:
-   When an operation is started.
-   When quantity feedback is reported on an operation.
-   When items are reported as finished on the production order.

### Example 5 – Manual BOM consumption

The following settings can be used if materials should always be deducted from inventory manually. In this case, picking list journals are not posted.

| Tab / Field                                                 | Setting    |
|-------------------------------------------------------------|------------|
| **Start** <br> **Update start on-line**                        | **Status**<br> |
| **Start** <br> **Automatic BOM consumption**                   | **Never**<br>  |
| **Operations** <br> **Automatic BOM consumption**              | **Never**<br>  |
| **Report as finished** <br> **Automatic BOM consumption**      | **Never**<br>  |
| **Report as finished** <br> **Update finished report on-line** | **Status** |

 



