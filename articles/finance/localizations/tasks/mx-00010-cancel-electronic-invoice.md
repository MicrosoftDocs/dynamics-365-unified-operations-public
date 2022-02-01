--- 
# required metadata 
 
title: MX-00010 Cancel an electronic invoice
description: You can cancel a CFDI electronic invoice that was previously validated and certified by the PAC. 
author: sndray
ms.date: 01/31/2022
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: EInvoiceCFDIJournal_AR   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Mexico
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# MX-00010 Cancel an electronic invoice

[!include [banner](../../includes/banner.md)]

You can cancel a CFDI electronic invoice that was previously validated and certified by the PAC. You can also cancel a CFDI electronic invoice by using the manual process.

## Cancel a CFDI electronic invoice

1. Go to **Accounts receivable** \> **Inquiries and reports** \> **CFDI (electronic invoices)**.
2. Select an electronic invoice that has a status of **Approved**.
3. Select the invoice number to view the details.
4. On the Action Pane, select **Functions** \> **Cancel CFDI**.
5. Close the page.
6. Go to **Accounts receivable** \> **Invoices** \> **E-Invoices** \> **Export/import electronic invoice process**.
7. Select **OK**. When the cancellation is confirmed, the status of the electronic invoice is changed to **Canceled**.
8. Go to **Accounts receivable** \> **Inquiries and reports** \> **CFDI (electronic invoices)**.
9. Select the canceled invoice to verify the status.

> [!NOTE]
> You can't cancel a CFDI document if an associated document exists. For example, you can't cancel a prepayment if an invoice references that payment. Cancel the associated documents, and then cancel the CFDI document.

As of Microsoft Dynamics 365 Finance version 10.0.23, you can specify the reason for the cancellation. When you select **Functions** \> **Cancel CFDI** on the Action Pane, you can select a cancellation reason. If you select **01** as the reason, fill in a replacement document to replace the current document.

## Manually cancel a CFDI electronic invoice

1. Select an invoice that has a status of **Approved**.
2. On the Action Pane, select **Functions** \> **Manual cancel**.
3. Enter the date of the cancellation.
4. In the **Cancel key name** field, enter the reason for the cancellation.
5. Select **OK** to confirm the cancellation of the electronic invoice. The status of electronic invoice is changed to **Manual cancel**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
