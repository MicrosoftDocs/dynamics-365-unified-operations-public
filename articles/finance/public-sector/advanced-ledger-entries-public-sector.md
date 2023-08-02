---
# required metadata

title: Advanced ledger entries in the public sector
description: This article explains how organizations in the public sector can use advanced ledger entries to create, adjust, and reverse ledger entries.
author: v-kiarnd
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AdvancedLedgerEntry, BudgetControlConfiguration, LedgerParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 3db0233e-d767-4dc0-b008-733098b6ca70
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Advanced ledger entries in the public sector

[!include [banner](../includes/banner.md)]

This article explains how organizations in the public sector can use advanced ledger entries to create, adjust, and reverse ledger entries. For example, advanced ledger entries can be used to reclassify expenditures if invoices are mistakenly posted to the wrong account or project.

## How do I set up advanced ledger entries?

Verify that the **Advanced ledger entry** **License configuration** key is selected in the **License configuration** page. Advanced ledger entries require General ledger posting definitions. These posting definitions can be set up to generate multiple, balanced ledger entries based on the ledger account entered in the **Advanced ledger entries** page. For more information about posting definitions for advanced ledger entries, see [Posting definitions in the public sector](posting-definitions-public-sector.md).

## Can I use budget control with advanced ledger entries?
Yes. If your organization uses budget control, you can enable budget control for advanced ledger entries on the **Budget control configuration** page.

## Can I use advanced ledger entries with projects?
Yes. If you want users to be able to change the financial dimensions for a project on the advanced ledger entry line, you’ll need to select the **Allow the financial dimensions to be edited on the advanced ledger entry form** option on the **General ledger parameters** page. If you don’t select this option, users can change the financial dimensions in the **Ledger account** field only if the financial dimensions are not the default financial dimensions for a project.

## How do I use advanced ledger entries to record year-end accrual entries?
Create an advanced ledger entry, select the **Reversing entry** option, and enter a reversing date. The reversing advanced ledger entry is created when the advanced ledger entry is posted. The reversing advanced ledger entry will have a new transaction number and a draft status. The reversing date will be used as the accounting date and the debit or credit amount on each line of the original entry will be reversed. The same posting definition will be used. The transaction text for the header and lines will contain the words “Reversing entry from,” the transaction number of the original advanced ledger entry, and the transaction text of the original advanced ledger entry.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
