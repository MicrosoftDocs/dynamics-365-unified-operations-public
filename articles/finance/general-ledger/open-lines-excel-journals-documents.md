---
# required metadata

title: Publish journal lines and documents from Excel
description: This article explains how to enter and publish lines for general journals from Microsoft Excel. It includes information about the various templates that you can use, depending on the type of transactions that you're entering.
author: kweekley
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 211874a7-4bf0-4a0c-96c2-fa05042777d3
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Publish journal lines and documents from Excel

[!include [banner](../includes/banner.md)]

This article explains how to enter and publish lines for general journals from Microsoft Excel. It includes information about the various templates that you can use, depending on the type of transactions that you're entering.

Users can enter and publish lines for financial journals from Microsoft Excel. After a user creates a journal, the **Open lines in Excel** button displays the templates that are available. Templates are designed to support specific scenarios, however not every combination of account type is supported in the journal. The following table shows the templates that are available and the account types which they support.

| Template             | Supported account types | How to access the template                                                          |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| Ledger journal lines     | Account: Ledger, Customer, Vendor, Bank Offset account: Ledger, Customer, Vendor, Bank Intercompany is supported.       | General journal                                                                         |
| Invoice register         | Account: Vendor Offset account: Ledger Intercompany isn't supported.                                                    | AP invoice register                                                                     |
| Invoice journal          | Accounts: Vendor Offset account: Ledger Intercompany is supported.                                                      | AP invoice journal                                                                      |
| Vendor invoice           |                                                                                                                         | Vendor invoice                                                                          |
| Customer invoice journal | Account: Customer Offset account: Ledger Intercompany is supported.                                                     | General journal                                                                         |
| Free text invoice        |                                                                                                                         | On the **Free text invoice** page, click **Open in Excel** (the Microsoft Office icon). |
| Fixed assets journal     | Asset to ledger, bank, customer, or vendor. Intercompany isn't supported.                                               | Fixed asset journal                                                                     |
| Vendor payment journal   | Account: Vendor Offset account: Ledger, Bank Intercompany is supported.                                                 | Vendor payment journal                                                                  |
| Customer payment journal | Account: Customer Offset account: Ledger, Bank Intercompany is supported.                                               | Customer payment journal                                                                |
| Project expense journal  | Account: Project, Ledger, Customer, Vendor Offset account: Project, Ledger, Customer, Vendor Intercompany is supported. | General journal Expense (under Project management and accounting)                       |

When the lines are published, they are validated to make sure that they comply with the rules that are set up in the financial journals. After the lines are published, users can edit or post the vouchers from Dynamics 365 Finance. 

To add financial dimensions to a template, additional changes are required. For additional information, see [Add dimensions to the Microsoft Excel template](../../fin-ops-core/dev-itpro/financial/add-dimensions-excel-templates.md). After dimensions are added to the entity, they are available in the Excel designer and can be added to the template.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
