--- 
# required metadata 
 
title: Settle customer consolidated invoices by using settle transactions
description: This topic provides information about payments that are made and settled against consolidated invoices. 
author: ShylaThompson
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustConsInvoice_JP, CustTable, CustOpenTrans   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Settle customer consolidated invoices by using settle transactions

[!include [banner](../../includes/banner.md)]

In Japan, payments are made and settled against consolidated invoice.

This procedure walks you through settling a consolidated invoice using settle transactions.

Before you begin this procedure, make sure that a consolidated invoice is created and confirmed, and a payment has been posted. 

This procedure was created using the demo data company JPMF.

1. Go to Accounts receivable > Periodic tasks > Consolidated invoice.
    * Confirm the consolidated invoice you want to settle is at status of Confirmed.  
    * Create and confirm a consolidated invoice.  
2. Go to Accounts receivable > Customers > All customers.
3. In the list, mark the selected row.
    * Select the customer that you want to settle the consolidated invoice for.  
4. On the Action Pane, click Collect.
5. Click Settle transactions.
    * Use Consolidation ID field to confirm the consolidated invoice that you want to settle.  
6. Find a line to settle and select the check box for that line
    * If you're running this procedure as a task guide, you might need to unlock the task guide before you can select the record.  
7. Find another line to settle and click the check box for that line
    * If you're running this procedure as a task guide, you might need to unlock the task guide before you can select the record.  
8. Click Post.
9. Go to Accounts receivable > Periodic tasks > Consolidated invoice.
    * Confirm that the status of the Consolidated invoice is updated to Settled.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]