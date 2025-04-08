--- 
title: Create an advanced ledger entry in the public sector
description: Learn about how public-sector organizations can use advanced ledger entries to create, adjust, and reverse ledger entries, including a step-by-step process.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 02/14/2022
ms.custom:
ms.reviewer: twheeloc
audience: Application User 
ms.search.region: Global
ms.search.industry: Public sector
ms.search.validFrom: 2016-06-30
ms.search.form: AdvancedLedgerEntry, AdvancedLedgerEntryCreate, ProjTableLookup, ProjCategoryLookUp
ms.dyn365.ops.version: Version 7.0.0 
---

# Create an advanced ledger entry in the public sector

[!include [banner](../../includes/banner.md)]

Public-sector organizations can use advanced ledger entries to create, adjust, and reverse ledger entries. For example, advanced ledger entries can be used to reclassify expenditures if invoices are mistakenly posted to the wrong account or project. This procedure was created using the PSUS demo company data in the public sector partition.

1. Go to **General ledger > Journal entries > Advanced ledger entries**.
2. Click **New**.
3. In the **Accounting date** field, enter a date.
4. In the **Transaction text** field, click the drop-down button to open the lookup.
5. In the list, click the transaction text for this advanced ledger entry.
6. In the **Posting definition** field, click the drop-down button to open the lookup.
7. In the list, click the **Posting definition** for this advanced ledger entry.
8. In the **Reason code** field, click the drop-down button to open the lookup.
9. In the list, click the **Reason code** for this advanced ledger entry.
10. In the **Reason comment** field, type a value.
11. Click **OK**.
12. Click **Add line**.
13. In the **Project ID** field, click the drop-down button to open the lookup.
14. In the list, click a project ID.
15. In the **Project category** field, click the drop-down button to open the lookup.
16. In the list, click a project category.
    * If you select the project category, the ledger account is entered automatically.  
    * Add a debit or a credit amount to this line. If needed, click Add line to add more lines.  
17. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
