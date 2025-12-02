---
title: Settle vendor consolidated invoices using a payment journal
description: Learn how to settle vendor consolidated invoices for Japan using a payment journal in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 05/09/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: VendConsInvoice_JP, LedgerJournalTable, LedgerJournalTransVendPaym, VendPaymProposalEdit
ms.custom: 
  - bap-template
---

# Settle vendor consolidated invoices by using a payment journal

[!include [banner](../../includes/banner.md)]

This article explains how to settle vendor consolidated invoices for Japan using a payment journal in Microsoft Dynamics 365 Finance.

In Japan, payments are made and settled against consolidated invoices.

The following procedure walks you through how to settle a consolidated invoice using a payment journal and the payment proposal feature. 

Before you complete the procedure, ensure that you have a consolidated invoice created and confirmed. 

The procedure uses the demo data company JPMF.

To settle vendor consolidated invoices using a payment journal, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Periodic tasks \> Consolidated invoice**.
1. In the **Consolidation ID** field, copy the value to reference later. You can use "JPMF-000002" from the demo data company JPMF.  
1. Go to **Accounts payable \> Payments \> Payment journal**.
1. Select **New**.
1. In the **Name** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Lines**.
1. Select **Payment proposal**.
1. Select **Create payment proposal**.
1. Expand or collapse the **Advanced parameters** section.
1. In the **Consolidation ID** field, enter a value. You can use the value you copied from the **Consolidated ID** field.  
1. Select **OK**.
1. Select **Create payments**.
1. Confirm that the payment line was generated based on the proposal and then provide a date for posting. When there are multiple invoices tied on one consolidated invoice, multiple lines might be generated on the payment journal.  
1. Select **Post**.
1. Go to **Accounts payable \> Periodic tasks \> Consolidated invoice**.
1. Confirm that the status of the consolidated invoice has been updated to be **Settled**.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
