---
# required metadata

title: Calculate capacity load on scheduled work orders
description: This topic explains how to calculate capacity load on scheduled work orders in Enterprise Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/28/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Calculate capacity load on scheduled work orders

This topic explains how to calculate capacity load on scheduled work orders in Enterprise Asset Management. You can calculate capacity load on scheduled work orders to get an overview of the work load on resources for a specific period. Calculations can be made for the following resources: Workers, worker groups, tools, and objects.

1. Click **Enterprise asset management** > **Inquiries** > **Schedule** > **Scheduled capacity load**.

2. Click **Calculate**.

3. In the **Show** field, select which load type you want to calculate: "Capacity", "Reserved", or "Remainder".

4. Select "Yes" on the **Skip zero** toggle button if you do not want to show results containing zero.

5. Select the resource types for which you want to calculate capacity load by selecting "Yes" on the relevant toggle buttons: **Worker**, **Worker group**, **Tool**, and **Object**.

6. Select the start date for the calculation in the **From date** field.

7. In the **Interval type** field, select the interval for the calculation: "Day", "Week", "Month", or "Quarter".

8. In the **Interval** field, insert the number of intervals you want to calculate. For example, if you have selected "Day" as the interval type, and you insert the number "5" in this field, a calculation of five days from the start date will be made.

9. Click **OK** to start the calculation.

The figure below shows a screenshot of the interface.

![Figure 1](media/08-work-order-scheduling.png)

>[!NOTE]
>If you select the load types "Capacity" or "Remainder" for your calculation, the same result will be displayed if no reservations have been made for the resources in the selected period.

Refer to [Calculate capacity load](../capacity-planning/calculate-capacity-load.md) for information about how to calculate capacity load on object calendar lines and not scheduled work orders.
