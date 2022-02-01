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
1. Go to **Accounts receivable** > **Inquiries and reports** > **CFDI (electronic invoices)**.
2. Select an electronic invoice with a status of **Approved**.
3. Select the invoice number link to see the details.
4. On the Action Pane, select **Functions**.
5. Select **Cancel CFDI** and then close the page.
6. Go to **Accounts receivable** > **Invoices** > **E-Invoices** > **Export/import electronic invoice process**.
8. Select **OK**. When the cancellation is confirmed, the status of the electronic invoice is changed to **Canceled**.  
9. Go to **Accounts receivable** > **Inquiries and reports** > **CFDI (electronic invoices)**.
10. Select the canceled invoice to verify the status.

>[!NOTE] 
> You can't cancel a CFDI document if an associated document exists. For example, you can't cancel a prepayment if an invoice references that payment. Cancel associated documents, and then cancel the CFDI document.

Starting in Dynamics 365 Finance version 10.0.23, you can specify the reason for the cancellation. When you select **Functions** > **Cancel CFDI** on Action Pane, you can select a cancellation reason. If the reason is 01, fill out a replacement document to replace the current one.   

## Manually cancel a CFDI electronic invoice
1. Select an invoice with the status **Approved**.
2. On the Action Pane, select **Functions**.
3. Select **Manual cancel**.
4. Enter the date of the cancellation.
5. In the **Cancel key name** field, enter the reason for the cancellation.
6. Select **OK** to confirm the cancellation of the electronic invoice. The status of electronic invoice is now **Manual cancel**.  


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
