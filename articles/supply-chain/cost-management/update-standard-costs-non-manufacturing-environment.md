---
# required metadata

title: Update standard costs in a non-manufacturing environment
description: This article provides guidance for updating standard costs in a non-manufacturing environment.
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CostingVersion, InventItemPrice
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 7ba0c408-2450-4042-9542-6fdf83c12e6c
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Update standard costs in a non-manufacturing environment

[!include [banner](../includes/banner.md)]

This article provides guidance for updating standard costs in a non-manufacturing environment.

The following guidelines assume that you use a two-version approach to update standard cost. In this approach, one costing version contains the standard costs that were originally defined for the frozen period, and the second costing version contains the incremental updates. Each update is entered as a cost record that is enclosed in the second costing version, and eventually it's enabled. An alternative, one-version approach uses the set of standard costs that was originally defined. The two-version approach requires that you define a second costing version. Here are the guidelines for defining this costing version:

-   Assign a costing type of **Standard costs**.
-   Assign a meaningful identifier that indicates the contents of the costing version, such as **2016-UPDATES**.
-   Make sure that the content includes cost records.
-   Allow cost records to be entered for all sites. If you specify a site, cost records can be entered only for that site.
-   Indicate a fallback principle of **None**. The fallback principle applies only to cost calculations for manufactured items.

To correct, adjust, or update standard costs for new items, follow these steps.

1.  Use the **Costing version** **setup** page to enable cost data to be entered into the second costing version. Optionally, prevent the activation of pending costs, so that activation will be allowed after pending costs have been completely and accurately defined. You can also optionally enter a date in the **From date** field. As a general guideline, use the date when you intend to enable the incremental updates. Alternatively, leave the **From date** field blank for the costing version, and then enter a date in the **From date** field for each cost record.
2.  Use the **Item price** page to enter updates as item cost records that are enclosed in the second costing version.
3.  Use the **Item prices** report to verify the completeness and accuracy of the item cost records that are enclosed in the second costing version.
4.  Use the **Costing version maintenance** page to change the blocking flag to allow activation of the pending cost records that are enclosed in the second costing version.
5.  Use the **Activate prices** page (which you open from the **Costing version maintenance** page) to activate all pending item cost records that are enclosed in the second costing version. You can also activate the pending cost records for individual items by clicking the **Activate pending price** button on the **Item price** page.
6.  To prevent additional data maintenance, use the **Costing version setup** page to change the blocking flags that are enclosed in the second costing version. The blocking policies will prevent the entry of new pending costs and the activation of pending costs.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]