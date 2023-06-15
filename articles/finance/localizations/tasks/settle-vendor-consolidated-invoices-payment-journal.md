---
title: Settle vendor consolidated invoices by using a payment journal
description: In Japan, payments can be made and settled against vendor consolidated invoices.
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
ms.search.form: VendConsInvoice_JP, LedgerJournalTable, LedgerJournalTransVendPaym, VendPaymProposalEdit
---
# Settle vendor consolidated invoices by using a payment journal

[!include [banner](../../includes/banner.md)]

In Japan, payments are made and settled against consolidated invoices.



This procedure walks you through settling a consolidated invoice using a payment journal and payment proposal feature. 



Before you complete this procedure, be sure that you have a consolidated invoice created and confirmed. 



This procedure was created using the demo data company JPMF.

1. Go to Accounts payable > Periodic tasks > Consolidated invoice.
2. Note the value in the Consolidation ID field to reference later
    * You can use JPMF-000002 from the demo data company JPMF.  
3. Go to Accounts payable > Payments > Payment journal.
4. Click New.
5. In the Name field, click the drop-down button to open the lookup.
6. In the list, click the link in the selected row.
7. Click Lines.
8. Click Payment proposal.
9. Click Create payment proposal.
10. Expand or collapse the Advanced parameters section.
11. In the Consolidation ID field, type a value.
    * You can use the value noted previously on the Consolidated invoice page.  
12. Click OK.
13. Click Create payments.
    * Confirm that the payment line was generated based on the proposal and then provide a date for posting.  
    * When there are multiple invoices tied on one consolidated invoice, multiple lines might be generated on the payment journal.  
14. Click Post.
15. Go to Accounts payable > Periodic tasks > Consolidated invoice.
    * Confirm that the status of the consolidated invoice has been updated to be Settled.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
