---
title: GB-00009 Create a credit note on the settlement discount
description: Learn how to create a credit note on the settlement discount for the United Kingdom in Microsoft Dynamics 365 Finance.
author: EricWangChen
ms.author: wangchen
ms.topic: how-to
ms.date: 08/04/2025
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2016-06-30
ms.search.form: CustFreeInvoice, CustTableLookup, CustPostInvoiceJob, LedgerJournalTable, LedgerJournalTransCustPaym, CustOpenTrans, CustTable, CustInvoiceJournal
ms.custom: 
  - bap-template
---

# GB-00009 Create a credit note on the settlement discount

[!include [banner](../../includes/banner.md)]

This article explains how to create a credit note on the settlement discount for the United Kingdom in Microsoft Dynamics 365 Finance.

The following procedure walks you through how to create a customer invoice that includes a cash discount. 

The procedure using the demo company DEMF with country context switched to the United Kingdom (country/region: GBR). 

Before you complete the procedure, you must complete the Setup parameters for credit note on prompt payment discount procedure.

To create a credit note on the settlement discount, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
1. Select **New**.
1. In the **Customer account** field, select the drop-down, and then select **DE-010**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Cash discount** field, select the drop-down, and then select **4%10d**.  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the list, mark the selected row.
1. In the **Description** field, enter "service".  
1. In the **Main account** field, select **170250**.  
1. In the **Unit price** field, enter "10000".  
1. Select **Post**.
1. Select **OK**.
1. Select the **TabPageGrid** tab.
1. Close the page.
1. Go to **Accounts receivable** \> **Payments** \> **Payment journal**.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Name** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Lines**.
1. In the list, mark the selected row.
1. In the **Account** field, select **DE-010**.
1. Select **Settlement**.
1. In the list, find and select the invoice posted in the previous task.  
1. Select or clear the **Mark** checkbox.
1. Select **OK**.
1. Select **Post**.
1. Close the page.
1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. In the list, find and select **DE-010**. 
1. On the Action Pane, select **Invoice**.
1. Select **Invoice journal**.
1. In the list, find and select the credit note created on the cash discount posted when invoice and payment were settled.  
1. On the Action Pane, select **Invoice**.
1. Select **View**.
1. Select **Original preview**.
1. Verify that the reason for the cash discount and original invoice number and date are printed in the credit note for the discount.  
1. Close the page.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
