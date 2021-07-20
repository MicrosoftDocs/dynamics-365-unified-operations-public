---
# required metadata

title: Stock card report for Thailand
description: This topic provides information about stock card reports for legal entities in Thailand. 
author: ShylaThompson
ms.date: 03/21/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TaxWithholdGroup, TaxWithholdTable, TaxWithholdTrans
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 265184
ms.assetid: 1ce8c70b-c6af-4171-98d2-2aa8e9563c5b
ms.search.region: Thailand
# ms.search.industry: 
ms.author: leguo
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Stock card report for Thailand

[!include [banner](../includes/banner.md)]

This topic provides information about stock card reports for legal entities in Thailand. A stock card report contains information about inventory movement, quantity, and cost for each item and warehouse, and must be generated when the government requests it. The stock card report is generated either before or after the inventory close process. 

You can generate the following stock card reports:

-   **Physical stock card** – View information that is related to one site or all sites, per location and warehouse, after packing slips are posted.
-   **Financial stock card** – View information that is related to one site or all sites, per location and warehouse, after invoices are posted.
-   **Stock card summary** – View item or warehouse details by item group, site, warehouse, and cost.

## Set up the generation of stock card reports
Complete the following tasks before you generate a stock card report:

-   Create an item that has the required information. **Note:** Assign a tax branch to a site.
-   Create a tax branch.
-   Set up a tax branch for a legal entity.
-   Set up a tax branch for a vendor or a customer.
-   Assign a tax branch to a site.
-   Create and post required purchase, sale, and inventory transfer transactions.

## Recalculate inventory and generate the financial stock card report
Use the **Closing and adjustment** page to recalculate inventory after the inventory close process is run, and generate the financial stock card report.

## Generate the stock card report
You can group items by site, warehouse, location, item number, or item group, and then generate the stock card reports. Use the **Stock card – Physical** report to generate the physical stock card report. Use the **Stock card – Financial** report to generate the financial stock card report. You can generate a detailed or summarized stock card report.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]