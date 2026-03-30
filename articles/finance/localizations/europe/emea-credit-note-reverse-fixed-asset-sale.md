---
title: Fixed assets disposal for Estonia and Lithuania
description: Learn about credit notes for fixed assets disposal posted by a free text invoice for users in legal entities in Estonia and Lithuania.
author: mrolecki
ms.author: johnmichalak
ms.topic: article
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Estonia, Lithuania
ms.search.validFrom: 2016-05-31
ms.search.form: CustFreeCreditNote_W, CustFreeInvoice
ms.dyn365.ops.version: AX 7.0.1
---

# Fixed assets disposal for Estonia and Lithuania

[!include [banner](../../includes/banner.md)]

This article provides information about credit notes for fixed assets disposal that users in legal entities in Estonia and Lithuania post by using a free text invoice.

You can sell fixed assets by using the disposal functionality through a free text invoice, fixed asset journal, or general journal in General ledger. For more information, see [Fixed asset disposal posting accounts](../../fixed-assets/fixed-asset-disposal-posting-accounts.md). The fixed assets disposal credit note functionality enables users in legal entities in Estonia and Latvia to create and post a credit note for a free text invoice with sales of a fixed asset. To create a credit note to reverse a free text invoice that you generated for the sale of a fixed asset, complete the following steps:

1. Select **Accounts receivable** &gt; **Invoices** &gt; **All free text invoices**.
1. Select the free text invoice that you want to create a credit note for.
1. On the Action Pane, in the **Cancel** group of the **Invoice** tab, select **Create credit note**.

   > [!NOTE]
   > When you create a credit note, include each transaction line from the free text invoice.

1. Select the **Create corrective lines** check box to add a reversal line and a corrective line to the credit note for each transaction line in the original free text invoice.
1. Post the credit note.

The fixed asset disposal transactions are reversed when you post the credit note. The status of the fixed asset remains **Sold**. You can still change the status of the fixed asset manually, if necessary.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
