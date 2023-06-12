---
title: Titres de recette in the public sector in France
description: The titre de recette is used by the director to notify and authorize the accountant to collect and deposit a specific amount from another entity.
author: brpotter
ms.date: 10/31/2017
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
ms.search.form: CustFreeInvoice
---

# Titres de recette in the public sector in France

[!include [banner](../includes/banner.md)]

The director uses the titre de recette to notify and authorize the accountant to collect and deposit a specific amount from another entity. The director or the accountant may delegate a representative to perform the task. However, the responsibility for each task remains with the director or the accountant. The titre maintains the strict separation that is required between the director's operational role and the accountant's accounting role.

In Dynamics 365 Finance, each titre is assigned a single free text invoice line. This assignment guarantees that each titre concerns only one debtor and includes only one budgetary account. A group of related titres, together with all supporting documentation, are assigned to a bordereau de titre for submittal to the accountant.

## Director’s tasks
From the **Maintain titres de recette** page, the director can complete the following tasks:

-   **Assign invoice lines to a titre de recette.** To find the invoice lines that haven’t yet been assigned to a titre, you can filter the retrieved lines by the **Titre** column.
-   **Authorize collection of invoice lines that are assigned to titres.** Authorization can also be completed from the **Titre de recette** tab on the **Free text invoice** page.
-   **Assign titres to a bordereau de titre.** To find the invoice lines that haven’t yet been assigned to a bordereau de titre, use the **Bordereau de titre** column to filter the retrieved lines.

To submit titres to the accountant for deposit, the director collects the printed titres and their related documentation under a borderau de titre.

-   Print the titres assigned to a bordereau from the **Records to include** FastTab on the **Titre de recette report** page.
-   Print the bordereau from the **Records to include** FastTab on the **Bordereau de titre report** page.

## Accountant’s tasks
From the **Maintain titres de recette** page or from the **Titre de recette** tab on the free text invoice page, the accountant can accept, reject, or hold titres. When a titre is rejected, the director status changes to Not reviewed. The titre and bordereau de titre numbers are cleared.

## Using the Database inquiry page
To open the **Database inquiry** page from the **Maintain titres de recette** page, specify the range of dates you want to select invoices from. Then click **Retrieve lines**. Thhe **Database inquiry** page opens and you can specify the criteria for the invoice lines you want to retrieve. When you close the page, all the invoice lines that meet the selected criteria are retrieved into the grid. Lines from the invoices that are being edited will not be retrieved. 

Use the following criteria in the database inquiry page to retrieve lines.

- Invoice lines that have not been reviewed by the director.

  | Table | Derived table |             Field             |    Criteria    |
  |-------|---------------|-------------------------------|----------------|
  | Titre |     Titre     | Director authorization status | "Not reviewed" |


- Invoice lines from titres that have been authorized for collection by the director, but not yet approved by the accountant.

  | Table | Derived table |             Field             |    Criteria    |
  |-------|---------------|-------------------------------|----------------|
  | Titre |     Titre     | Director authorization status |  "Authorized"  |
  | Titre |     Titre     | Accountant acceptance status  | "Not reviewed" |


- Invoice lines from titres that were rejected by the accountant.

  | Table | Derived table | Field                        | Criteria   |
  |-------|---------------|------------------------------|------------|
  | Titre | Titre         | Accountant acceptance status | "Rejected" |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
