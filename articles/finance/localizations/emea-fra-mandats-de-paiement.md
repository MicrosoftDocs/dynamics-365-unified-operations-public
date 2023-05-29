---
title: Mandats de paiement in the public sector in France
description: The mandat de paiement is used by the director to notify and authorize the accountant to pay a specific amount to another entity.
author: brpotter
ms.date: 12/02/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: France
ms.author: brpotter
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.search.industry: Public sector
---

# Mandats de paiement in the public sector in France

[!include [banner](../includes/banner.md)]

The mandat de paiement is used by the director to notify and authorize the accountant to pay a specific amount to another entity. As required, the mandat maintains strict separation between the director's operational role and the accountant's accounting role.

## Director’s tasks

From the **Maintain mandats de paiement** page, the director can complete the following tasks:

-   **Assign invoice lines to a mandat de paiement.** To find the invoice lines not yet assigned to a mandat, use the **Mandat** column to filter the retrieved lines.
-   **Authorize payment of invoice lines that are assigned to mandats.** Payments can also be authorized from the **Mandat de paiement** tab on the **Vendor invoice** page or the **Vendor transactions** page.
-   **Assign mandats to a bordereau de mandat.** To find the invoice lines that haven’t yet been assigned to a bordereau de mandat, you can filter the retrieved lines by the **Bordereau de mandat** column.
-   **Issue a requisition order.** Assign the invoice line to a new mandat before submitting it to the accountant as a requisition order.

To submit mandats to the accountant for payment, the director collects the printed mandats and their related documentation under a bordereau de mandat.

-   Print the mandats assigned to a bordereau from the **Records to include** FastTab on the **Mandat de paiement report** page.
-   Print the bordereau from the **Records to include** FastTab on the **Bordereau de mandat report** page.

## Accountant’s tasks
The accountant can acceps, reject, or hold mandats from the following locations:

  - The **Maintain mandats de paiement** page
  - The **Pending vendor invoices** page, on the **Mandat de paiement** tab  
  - The **Open vendor invoices** page, on the **Mandat de paiement** tab
  
When a mandat is rejected, the director status changes to **Not reviewed**. The mandat and bordereau de mandat numbers are cleared.

## Using the Database inquiry page
To open the **Database inquiry** page from the **Maintain mandats de paiement** page, specify whether you want to work with pending or posted invoices. Indicate the date range you want to select invoices from, and then select **Retrieve lines**. The **Database inquiry** page opens and you can specify the criteria for the invoice lines you want to retrieve. When you close the page, all invoice lines that meet the selected criteria are retrieved into the grid. Lines from invoices that are being edited will not be retrieved. 

Use the following criteria in the database inquiry page to retrieve lines.

- Invoice lines that have not been reviewed by the director.

  | Table  | Derived table |             Field             |    Criteria    |
  |--------|---------------|-------------------------------|----------------|
  | Mandat |    Mandat     | Director authorization status | "Not reviewed" |


- Invoice lines from mandats that have been authorized for payment by the director, but not yet approved by the accountant.

  | Table  | Derived table |             Field             |    Criteria    |
  |--------|---------------|-------------------------------|----------------|
  | Mandat |    Mandat     | Director authorization status |  "Authorized"  |
  | Mandat |    Mandat     | Accountant acceptance status  | "Not reviewed" |


- Invoice lines from mandats that were rejected by the accountant.

  | Table  | Derived table | Field                        | Criteria   |
  |--------|---------------|------------------------------|------------|
  | Mandat | Mandat        | Accountant acceptance status | "Rejected" |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
