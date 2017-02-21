---
# required metadata

title: Post with derived books
description: This article describes how to use derived books.
author: twheeloc
manager: AnnBe
ms.date: 2015-09-10 21 - 03 - 22
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: AssetBookTable, LedgerJournalTransAsset
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 3421
ms.assetid: f5187c21-eec5-4148-b178-b8a5feff7f23
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.dyn365.ops.intro: 01-02-2016
ms.dyn365.ops.version: AX 7.0.0

---

# Post with derived books

This article describes how to use derived books.

When you post transactions for a book that contains derived books, the derived book transactions are posted automatically in journals, purchase orders, or free text invoices. However, if you prepare the primary book transactions in the Fixed assets journal, you can view and modify the amounts of the derived transactions before you post them.
-   Certain accounts, such as sales tax and customer or vendor accounts, are updated only once by postings of the primary book. The derived book transactions are posted to the accounts that have been defined for the derived book in the Fixed asset posting profiles page.
-   Acquisition is often used as the transaction type for the derived books. You use this when the book and the derived book should be applied to the fixed asset from the time of the acquisition of the fixed asset.
-   Other values for the transaction type can also apply. For example, if the primary book and the derived books have the same intervals regarding sale or disposal, all fixed asset transaction types are available for the setup of a derived book.

| **Caution**                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Depreciation posted in the derived book will be the same amount as was posted for the primary book. If the depreciation methods are different between the books, you should not generate depreciation transactions using the derived process. |

Example The following information describes how to set up acquisition transactions with the derived book functionality.
1.  Create the books on the Books page.
    -   The book for accounting: VM 1, Current posting layer
    -   The book for tax purposes: VM 2, Tax posting layer

2.  On VM 1, click the Derived books tab. Select VM 2 in the Book field, and Acquisition in the Transaction type field.

The books then can be attached to specific fixed assets. When an acquisition is posted for a fixed asset with book VM 1, the acquisition is posted not only on VM 1, but also on the derived book VM 2. The status of both fixed asset books is updated to Open.
| **Note**                                                                                                            |
|---------------------------------------------------------------------------------------------------------------------|
| If you do not use derived books, you must post the acquisition of the fixed asset both for book VM 1 and book VM 2. |

 
-



See also
--------

[Derived books](http://ax.help.dynamics.com/wiki/derived-value-models/)

