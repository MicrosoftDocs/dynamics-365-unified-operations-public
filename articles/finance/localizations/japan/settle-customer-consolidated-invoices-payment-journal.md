---
title: Settle customer consolidated invoices by using a payment journal
description: In Japan, payments can be made and settled against customer consolidated invoices.
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
ms.search.form: CustConsInvoice_JP, LedgerJournalTable, LedgerJournalTransCustPaym, CustPaymProposalEdit
---
# Settle customer consolidated invoices by using a payment journal

[!include [banner](../../includes/banner.md)]

In Japan, payments are made and settled against consolidated invoices.



This procedure walks you through settling a consolidated invoice using a payment journal and payment proposal feature. 



Before you complete this procedure, be sure that you have a consolidated invoice created and confirmed. 



This procedure was created using the demo data company JPMF.

1. Go to Accounts receivable > Periodic tasks > Consolidated invoice.
2. Note the value in the Consolidation ID field to reference later
    * You can use JPMF-000002 from the demo data company JPMF.  
3. Go to Accounts receivable > Payments > Payment journal.
4. Click New.
5. In the Name field, type a value.
6. Click Lines.
7. Click Payment proposal.
8. Click Create payment proposal.
9. Expand the Advanced parameters section.
10. In the Consolidation ID field, type a value.
    * You can use the value noted previously on the Consolidated invoice page.  
11. Click OK.
12. Click Create payments.
    * Confirm the payment line is generated based on the proposal.  Provide a Date for posting.  
    * When there are multiple invoices tied on one consolidated invoice, there may be multiple lines on the payment journal been generated.  
13. Click Post.
14. Go to Accounts receivable > Periodic tasks > Consolidated invoice.
    * Confirm that the status of the consolidated invoice has been updated to be Settled.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
