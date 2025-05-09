---
title: Post with derived books
description: Learn how to use derived books, which include transactions that are posted automatically in journals, purchase orders, and free text invoices.
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 08/12/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: AssetBookTable, LedgerJournalTransAsset
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: f5187c21-eec5-4148-b178-b8a5feff7f23
---

# Post with derived books

[!include [banner](../includes/banner.md)]

This article describes how to use derived books.

When you post transactions for a book that contains derived books, the derived book transactions are posted automatically in journals, purchase orders, or free text invoices. However, if you prepare the primary book transactions in the Fixed assets journal, you can view and modify the amounts of the derived transactions before you post them.
-   Certain accounts, such as sales tax and customer or vendor accounts, are updated only once by postings of the primary book. The derived book transactions are posted to the accounts that have been defined for the derived book in the Fixed asset posting profiles page.
-   Acquisition is often used as the transaction type for the derived books. You use this when the book and the derived book should be applied to the fixed asset from the time of the acquisition of the fixed asset.
-   Other values for the transaction type can also apply. For example, if the primary book and the derived books have the same intervals regarding sale or disposal, all fixed asset transaction types are available for the setup of a derived book.

> [!WARNING]
> Depreciation that is posted in the derived book is the same amount that was posted for the primary book. If the depreciation methods differ between the books, you should not use the derived process to generate depreciation transactions.

In version 10.0.41, the **Consider split transaction in derived books posting** feature automates the process of splitting transactions from the main book to designated derived books based on asset book configurations. This feature ensures accurate recording across primary and secondary ledgers without manual input. It also helps maintain consistency. After the feature is enabled, split transactions are automatically posted according to the predefined settings in the asset book. Therefore, no manual intervention is required, derived books remain updated in real time.

## Example 
The following information describes how to set up acquisition transactions with the derived book functionality.

1.  Create the books on the Books page.
    -   The book for accounting: VM 1, Current posting layer
    -   The book for tax purposes: VM 2, Tax posting layer

2.  On VM 1, click the Derived books tab. Select VM 2 in the Book field, and Acquisition in the Transaction type field.

The books then can be attached to specific fixed assets. 

When an acquisition is posted for a fixed asset with book VM 1, the acquisition is posted not only on VM 1, but also on the derived book VM 2. The status of both fixed asset books is updated to Open.

> [!NOTE]
> If you do not use derived books, you must post the acquisition of the fixed asset both for book VM 1 and book VM 2.

For more information, see [Derived books](derived-books.md).





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
