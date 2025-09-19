---
title: Settle customer consolidated invoices by using settle transactions
description: Learn how to settle customer consolidated invoices for Japan by using settle transactions functionality in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 05/09/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: CustConsInvoice_JP, CustTable, CustOpenTrans
ms.custom: 
  - bap-template
---

# Settle customer consolidated invoices by using settle transactions

[!include [banner](../../includes/banner.md)]

This article explains how to settle customer consolidated invoices for Japan by using settle transactions functionality in Microsoft Dynamics 365 Finance.

In Japan, payments are made and settled against consolidated invoices.

Before you begin the procedure, ensure that a consolidated invoice is created and confirmed, and that a payment has been posted. 

The procedure usese the demo data company JPMF.

To settle customer consolidated invoices by using settle transactions functionality, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Periodic tasks \> Consolidated invoice**.
1. Confirm that the consolidated invoice you want to settle has a status of **Confirmed**.  
1. Create and confirm a consolidated invoice.  
1. Go to **Accounts receivable \> Customers \> All customers**.
1. In the list, mark the selected row.
1. Select the customer that you want to settle the consolidated invoice for.  
1. On the Action Pane, select **Collect**.
1. Select **Settle transactions**.
1. In the **Consolidation ID** field, confirm the consolidated invoice that you want to settle.  
1. Find a line to settle and select the checkbox for that line. If you're running this procedure as a task guide, you might need to unlock the task guide before you can select the record.  
1. Find another line to settle and select the checkbox for that line. 
1. Select **Post**.
1. Go to **Accounts receivable \> Periodic tasks \> Consolidated invoice**.
1. Confirm that the consolidated invoice you want to settle has a status of **Settled**.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
