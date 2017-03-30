---
# required metadata

title: Fixed assets disposal for Estonia and Lithuania
description: This topic provides information about credit notes for fixed assets disposal posted by a free text invoice for users in legal entities in Estonia and Lithuania.
author: ShylaThompson
manager: AnnBe
ms.date: 2017-01-11 14 - 59 - 00
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CustFreeCreditNote_W, CustFreeInvoice
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 266944
ms.assetid: 353ac18b-bc81-4cb4-b182-1e6e0759f961
ms.search.region: Estonia, Lithuania
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Fixed assets disposal for Estonia and Lithuania

This topic provides information about credit notes for fixed assets disposal posted by a free text invoice for users in legal entities in Estonia and Lithuania.

Fixed assets can be sold using disposal functionality through a free text invoice, fixed asset journal, or general journal in General ledger. For more information, see [Fixed asset disposal posting accounts](../fixed-assets/fixed-asset-disposal-posting-accounts.md). Fixed assets disposal credit note functionality allows users in legal entities in Estonia and Latvia to create a credit note for a free text invoice with sales of a fixed asset and then post it. To create a credit note to reverse a free text invoice that was generated for the sale of a fixed asset, complete the following steps:

1.  Click **Accounts receivable** &gt; **Invoices** &gt; **All free text invoices**.
2.  Select the free text invoice that you are creating a credit note for.
3.  On the Action Pane, in the **Cancel** group of the **Invoice** tab, click **Create credit note**. **Note:** When you create a credit note, you must include each transaction line from the free text invoice.
4.  Select the **Create corrective lines** check box to add a reversal line and a corrective line to the credit note for each transaction line in the original free text invoice.
5.  Post the credit note.

The fixed asset disposal transactions, created when you posted the credit note, are reversed. The status of the fixed asset remains **Sold**. You can still change the status of the fixed asset manually, if necessary.

