---
# required metadata

title: Report BOMs as finished
description: This article provides information about reporting BOMs as finished.
author: johanhoffmann
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BOMReportFinish, BOMReportFinishMax, BOMSetupReportFinish
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 510d05a3-0073-438d-b0c4-b6a6df1882ea
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Report BOMs as finished

[!include [banner](../includes/banner.md)]

This article provides information about reporting BOMs as finished.

The **Report as finished** and **Max. report as Finished** pages are used to report bills of materials (BOMs) as finished. Conceptually, the process for reporting a BOM as finished is the same as the process for reporting a production order as finished. This process can be used in, for example, simple assembly and kitting processes, where the more advanced capabilities of production orders aren't required. The **Report as finished** page lets you report multiple BOMs as finished in a batch. The **Max. report as Finished** page lets you report only one BOM as finished at a time. The **Report as finished** page is available from a menu item in Inventory management, and both pages are available as a menu items on the **Released products** page.

## Report as finished page
If you open the **Report as finished** page from a released product, the page suggests that you report the standard inventory default quantity as finished. By default, the active BOM version is shown, but you can change the BOM version if there are other approved versions. The page also lets you delete records and create new records for released products that should be reported as finished. To use a query to select products, click the **Select** menu item. You can manually confirm reporting as finished for the selected products by clicking **OK**. Alternatively, you can set up the process to run in a batch. When the report as finished process is confirmed, the system generates a BOM journal where the posting to inventory is processed. This journal consists of one line item for the finished product and a line item for each BOM line. You can control whether the journal is automatically posted or whether it is left open for additional adjustments.

## Max. report as finished page
On the **Max. report as finished** page, each BOM line indicates the number of pieces of the product that can be reported as finished. This calculation is based on the physical available on-hand inventory of each material line. In the following example, one piece of item number FG consumes two pieces of raw material RM10 and one piece of raw material RM20. Because there are only 10 pieces of RM10 on hand, the maximum quantity of FG that can be reported as finished is five pieces. This value is shown in the **Max. Report as finished** field.

| Level | Item number | Quantity | On-hand | Max. Report as finished |
|-------|-------------|----------|---------|-------------------------|
| 0     | FG          |  1       | 0       | 5                       |
| 1     | RM10        | -2       | 10      | 5                       |
| 1     | RM20        | -1       |  8      | 8                       |

## BOMs that have multiple levels
When a BOM has multiple levels, you can control how materials are accounted for at all levels by using the **Explosion** field. This field is available on both the **Report as finished** page and the **Max. report as Finished** page. The following options are available:

-   **Never** – Underlying BOMs aren't exploded if there is a material shortage.
-   **Always** – All underlying BOMs are fully exploded. Therefore, any free on-hand inventory for semi-finished component items isn't used.
-   **Shortage** – Underlying BOMs are exploded only if the full quantity of the material that is wanted isn't available.

### Example

In this example, three pieces of the finished product (item number FG) are ready to be reported as finished. There is a two-level BOM, as shown here.

| Level | Item number | BOM-line quantity | On-hand |
|-------|-------------|-------------------|---------|
| 0     | FG          |                   |         |
| 1     | COMP        | 1                 | 2       |
| 1     | RM          | 1                 |         |

The following tables show how the setting of the **Explosion** field affects the way that BOM journal lines are generated. **Explosion: Never**

| Level | Item number | Quantity |
|-------|-------------|----------|
| 0     | FG          | 3        |
| 1     | COMP        | -3       |

As the preceding table shows, only item number COMP is considered deducted in the journal. Item number RM, which is part of COMP, isn't exploded to the journal line, and the two on-hand pieces of COMP aren't considered. **Explosion: Always**

| Level | Item number | Quantity |
|-------|-------------|----------|
| 0     | FG          | 3        |
| 1     | RM          | -3       |

In this case, item number COMP is exploded into its raw material, item number RM. The two on-hand pieces of COMP aren't considered in the quantity of RM to consume. **Explosion: Shortage**

| Level | Item number | Quantity |
|-------|-------------|----------|
| 0     | FG          | 3        |
| 1     | COMP        | -2       |
| 1     | RM          | -1       |

In this case, the two on-hand pieces of item number COMP are considered. However, because three pieces of item number FG are required, one piece of item number RM is also required in order to make the additional one piece of COMP.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]