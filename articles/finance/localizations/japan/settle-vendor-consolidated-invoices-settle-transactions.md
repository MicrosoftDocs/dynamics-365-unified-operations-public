---
title: Settle vendor consolidated invoices by using settle transactions
description: In Japan, payments are made and settled against consolidated invoice.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: VendConsInvoice_JP, VendTable, VendOpenTrans
---
# Settle vendor consolidated invoices by using settle transactions

[!include [banner](../../includes/banner.md)]

In Japan, payments are made and settled against consolidated invoice.



This procedure walks you through settling a consolidated invoice using settle transactions.



You need to make sure that a consolidated invoice is created and confirmed, and a payment is posted before running this procedure. 



This procedure was created using the demo data company JPMF.


## Confirm Consolidation invoice to be settled
1. Go to Accounts payable > Periodic tasks > Consolidated invoice.
2. Note the value in the Consolidation ID field to reference later
    * Confirm that the consolidated invoice to settle has a status of Confirmed.    In this example: Consolidation ID - JPMF-000004  

## Settle Consolidation invoice 
1. Go to Accounts payable > Vendors > All vendors.
2. In the list, find and select the desired record.
    * Select the vendor that you want to settle the consolidated invoice for. In this example, we use JPMF-000002.  
3. On the Action Pane, click Invoice.
4. Click Settle transactions.
5. In the list, find and select the desired record.
    * Select the record with Consolidation ID = JPMF-000004.  
6. Select or clear the Mark check box.
    * Mark the Invoice.  
7. In the list, find and select the desired record.
    * Select the payment transaction, valued more than the Invoice amount.  
8. Select or clear the Mark check box.
    * Mark the payment transaction.  
9. Click Post.

## Validate Consolidation invoice status to Settled
1. Go to Accounts payable > Periodic tasks > Consolidated invoice.
    * Confirm that the status of the consolidated invoice is now "Settled".  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
