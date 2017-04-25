---
# required metadata

title: Titres de recette in the public sector in France
description: The titre de recette is used by the director to notify the accountant that the organization is entitled to collect a specific amount from another entity, and to authorize the accountant to deposit that amount. The director or the accountant may delegate a representative to perform the task, but the responsibility for each task remains with the director or the accountant. The titre maintains the strict separation that is required between the operational role of the director and the accounting role of the accountant.
author: rschloma
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CustFreeInvoice
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 19931
ms.assetid: 01d7ba2b-32b7-43aa-8edb-7a2ed700363a
ms.search.region: France
ms.search.industry: Public sector
ms.author: brpotter
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Titres de recette in the public sector in France

[!include[banner](../includes/banner.md)]


The titre de recette is used by the director to notify the accountant that the organization is entitled to collect a specific amount from another entity, and to authorize the accountant to deposit that amount. The director or the accountant may delegate a representative to perform the task, but the responsibility for each task remains with the director or the accountant. The titre maintains the strict separation that is required between the operational role of the director and the accounting role of the accountant.

In Microsoft Dynamics 365 for Operations, each titre is assigned a single free text invoice line. This guarantees that each titre concerns only one debtor and includes only one budgetary account. A group of related titres, together with all supporting documentation, are assigned to a bordereau de titre for submittal to the accountant.

## Director’s tasks
From the **Maintain titres de recette** page, the director can complete the following tasks:

-   **Assign invoice lines to a titre de recette.** To find the invoice lines that haven’t yet been assigned to a titre, you can filter the retrieved lines by the **Titre** column.
-   **Authorize collection of invoice lines that are assigned to titres.** This can also be done from the **Titre de recette** tab on the free text invoice page.
-   **Assign titres to a bordereau de titre.** To find the invoice lines that haven’t yet been assigned to a bordereau de titre, you can filter the retrieved lines by the **Bordereau de titre** column.

To submit titres to the accountant for deposit, the director collects the printed titres and their related documentation under a borderau de titre.

-   Print the titres assigned to a bordereau from the **Records to include** FastTab on the **Titre de recette report** page.
-   Print the bordereau from the the **Records to include** FastTab on the **Bordereau de titre report** page.

## Accountant’s tasks
From the **Maintain titres de recette** page or from the **Titre de recette** tab on the free text invoice page, the accountant can accept, reject, or hold titres. When a titre is rejected, the director status changes to Not reviewed, and the titre and bordereau de titre numbers are cleared.

## Using the database inquiry page
To open the database inquiry page on the **Maintain titres de recette** page, specify the range of dates you want to select invoices from. Then click **Retrieve lines**. This opens the database inquiry page where you can specify the criteria for the invoice lines you want to retrieve. When you close the form, all the invoice lines that meet the selected criteria are retrieved into the grid. Lines from the invoices that are being edited will not be retrieved. **Tip**: Use the following criteria in the database inquiry page to retrieve lines.

-   Invoice lines that have not been reviewed by the director.
    | Table | Derived table | Field                         | Criteria       |
    |-------|---------------|-------------------------------|----------------|
    | Titre | Titre         | Director authorization status | "Not reviewed" |

-   Invoice lines from titres that have been authorized for collection by the director, but not yet approved by the accountant.
    | Table | Derived table | Field                         | Criteria       |
    |-------|---------------|-------------------------------|----------------|
    | Titre | Titre         | Director authorization status | "Authorized"   |
    | Titre | Titre         | Accountant acceptance status  | "Not reviewed" |

-   Invoice lines from titres that were rejected by the accountant.
    | Table | Derived table | Field                        | Criteria   |
    |-------|---------------|------------------------------|------------|
    | Titre | Titre         | Accountant acceptance status | "Rejected" |





