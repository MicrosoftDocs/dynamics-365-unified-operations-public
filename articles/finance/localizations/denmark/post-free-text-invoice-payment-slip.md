--- 
title: Post a free text invoice with a payment slip
description: Learn how to post a free text invoice with a payment slip attachment in a specified format, including a process that uses the DEMF demo data company. 
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 03/05/2026
ms.reviewer: johnmichalak  
ms.search.region: Denmark
ms.search.validFrom: 2016-06-30
ms.search.form: CustFreeInvoice, CustTableLookup, CustPostInvoiceJob, SRSPrintDestinationSettingsForm
ms.custom: 
  - bap-template
---

# Post a free text invoice with a payment slip

[!include [banner](../../includes/banner.md)]

You can post a free text invoice with a payment slip attachment in a specified format. The payment slip prints with the creditor identification number and invoice number to identify the payment.

This procedure shows you how to post a free text invoice with a payment slip.

Before you can complete this procedure, you must set up a payment slip format and set up a payment slip for customer invoices.

This procedure uses the demo data company DEMF. 

This functionality is available for legal entities whose primary address is in Denmark.

1. Go to **Accounts receivable** > **Invoices** > **All free text invoices**.
1. Select **New**.
1. In the **Customer account** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Currency** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
    * You can print the payment slip only for free text invoices with currency Danish kroner (DKK).  
1. In the list, select the link in the selected row.
1. In the list, mark the selected row.
1. In the **Description** field, type a value.
1. In the **Main account** field, specify the desired values.
1. In the **Unit price** field, enter a number.
1. Select **Save**.
1. Select **Post**.
1. Select **OK**.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
