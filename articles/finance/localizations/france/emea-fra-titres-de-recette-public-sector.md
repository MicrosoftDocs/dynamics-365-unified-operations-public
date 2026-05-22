---
title: Titres de recette in the public sector in France
description: Learn about the titres de recette in the public sector in France.
author: brpotter
ms.author: brpotter
ms.topic: how-to
ms.date: 03/11/2026
ms.reviewer: johnmichalak
ms.search.region: France
ms.search.validFrom: 2016-02-28
ms.search.form: CustFreeInvoice
ms.custom: 
  - bap-template
---

# Titres de recette in the public sector in France

[!include [banner](../../includes/banner.md)]

The director uses the titre de recette to notify and authorize the accountant to collect and deposit a specific amount from another entity. The director or the accountant can delegate a representative to perform the task. However, the director or the accountant remains responsible for each task. The titre maintains the strict separation that is required between the director's operational role and the accountant's accounting role.

In Dynamics 365 Finance, each titre is assigned a single free text invoice line. This assignment guarantees that each titre concerns only one debtor and includes only one budgetary account. You assign a group of related titres, together with all supporting documentation, to a bordereau de titre for submittal to the accountant.

## Director’s tasks

From the **Maintain titres de recette** page, the director can complete the following tasks:

- **Assign invoice lines to a titre de recette.** To find the invoice lines that aren't yet assigned to a titre, filter the retrieved lines by the **Titre** column.
- **Authorize collection of invoice lines that are assigned to titres.** Authorize collection from the **Titre de recette** tab on the **Free text invoice** page.
- **Assign titres to a bordereau de titre.** To find the invoice lines that aren't yet assigned to a bordereau de titre, use the **Bordereau de titre** column to filter the retrieved lines.

To submit titres to the accountant for deposit, the director collects the printed titres and their related documentation under a borderau de titre.

- Print the titres assigned to a bordereau from the **Records to include** FastTab on the **Titre de recette report** page.
- Print the bordereau from the **Records to include** FastTab on the **Bordereau de titre report** page.

## Accountant’s tasks

From the **Maintain titres de recette** page or from the **Titre de recette** tab on the free text invoice page, the accountant can accept, reject, or hold titres. When the accountant rejects a titre, the director status changes to Not reviewed. The titre and bordereau de titre numbers are cleared.

## Using the Database inquiry page

To open the **Database inquiry** page from the **Maintain titres de recette** page, specify the range of dates you want to select invoices from. Then select **Retrieve lines**. The **Database inquiry** page opens and you can specify the criteria for the invoice lines you want to retrieve. When you close the page, the system retrieves all the invoice lines that meet the selected criteria into the grid. The system doesn't retrieve lines from the invoices that you're editing.

Use the following criteria in the **Database inquiry** page to retrieve lines.

- Invoice lines that the director hasn't reviewed.

  | Table | Derived table |             Field             |    Criteria    |
  |-------|---------------|-------------------------------|----------------|
  | Titre |     Titre     | Director authorization status | "Not reviewed" |

- Invoice lines from titres that the director authorized for collection, but the accountant didn't yet approve.

  | Table | Derived table |             Field             |    Criteria    |
  |-------|---------------|-------------------------------|----------------|
  | Titre |     Titre     | Director authorization status |  "Authorized"  |
  | Titre |     Titre     | Accountant acceptance status  | "Not reviewed" |

- Invoice lines from titres that the accountant rejected.

  | Table | Derived table | Field                        | Criteria   |
  |-------|---------------|------------------------------|------------|
  | Titre | Titre         | Accountant acceptance status | "Rejected" |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
