---
title: Settle customer consolidated invoices by using a payment journal
description: Learn how to settle customer consolidated invoices using a payment journal for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 05/09/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: CustConsInvoice_JP, LedgerJournalTable, LedgerJournalTransCustPaym, CustPaymProposalEdit
ms.custom: 
  - bap-template
---

# Settle customer consolidated invoices by using a payment journal

[!include [banner](../../includes/banner.md)]

This article explains how to settle customer consolidated invoices using a payment journal for Japan in Microsoft Dynamics 365 Finance.

In Japan, payments are made and settled against consolidated invoices.

The following procedure walks you through how to settle a consolidated invoice using a payment journal and payment proposal feature. 

The procedure uses the demo data company JPMF.

Before you complete the procedure, ensure that you've first created and confirmed a consolidated invoice. 

To settle customer consolidated invoices using a payment journal, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Periodic tasks \> Consolidated invoice**.
1. In the **Consolidation ID** field, copy the value to reference later. You can use "JPMF-000002" from the demo data company JPMF.  
1. Go to **Accounts receivable \> Payments \> Payment journal**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Select **Lines**.
1. Select **Payment proposal**.
1. Select **Create payment proposal**.
1. Expand the **Advanced parameters** section.
1. In the **Consolidation ID** field, enter a value. You can use the value noted previously on the **Consolidated invoice** page.  
1. Select **OK**.
1. Select **Create payments**.
1. Confirm the payment line is generated based on the proposal, and then enter a date for posting. When there are multiple invoices tied to one consolidated invoice, there may be multiple lines generated in the payment journal.  
1. Select **Post**.
1. Go to **Accounts receivable \> Periodic tasks \> Consolidated invoice**.
1. Confirm that the status of the consolidated invoice is updated to **Settled**.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
