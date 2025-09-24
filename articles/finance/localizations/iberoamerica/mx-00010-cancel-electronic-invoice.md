---
title: MX-00010 Cancel an electronic invoice
description: Learn how to cancel a CFDI electronic invoice that was previously validated and certified by the PAC in Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/10/2025
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-06-30
ms.search.form: EInvoiceCFDIJournal_AR
---

# MX-00010 Cancel an electronic invoice

[!include [banner](../../includes/banner.md)]

This article explains how to cancel a Comprobante Fiscal Digital por Internet (CFDI) electronic invoice that was previously validated and certified by the PAC in Microsoft Dynamics 365 Finance.

## Cancel a CFDI electronic invoice

To cancel a CFDI electronic invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Inquiries and reports \> CFDI (electronic invoices)**.
1. Select an electronic invoice that has a status of **Approved**.
1. Select the invoice number to view the details.
1. On the Action Pane, select **Functions \> Cancel CFDI**.
1. Close the page.
1. Go to **Accounts receivable \> Invoices \> E-Invoices \> Export/import electronic invoice process**.
1. Select **OK**. When the cancellation is confirmed, the status of the electronic invoice is changed to **Canceled**.
1. Go to **Accounts receivable \> Inquiries and reports \> CFDI (electronic invoices)**.
1. Select the canceled invoice to verify the status.

> [!NOTE]
> You can't cancel a CFDI document if an associated document exists. For example, you can't cancel a prepayment if an invoice references that payment. Cancel the associated documents first, and then cancel the CFDI document.

To specify the reason for the cancellation, go to **Functions \> Cancel CFDI** on the Action Pane and select a cancellation reason. If you select **01** as the reason, fill in a replacement document to replace the current document.

## Manually cancel a CFDI electronic invoice

To manually cancel a CFDI electronic invoice, follow these steps.

1. Select an invoice that has a status of **Approved**.
1. On the Action Pane, select **Functions \> Manual cancel**.
1. Enter the date of the cancellation.
1. In the **Cancel key name** field, enter the reason for the cancellation.
1. Select **OK** to confirm the cancellation of the electronic invoice. The status of electronic invoice is changed to **Manual cancel**.

## Manually update the status of a CFDI document that's in progress after cancellation

If a CFDI document was canceled in a PAC application but has a status of **In progress** a long time after cancellation, you can use the **Update electronic document status** periodic task to update the status a CFDI document. 

To manually update the status of a CFDI document that's in progress after cancellation, follow these steps.

1. Go to **Accounts receivable \> Invoices \> E-invoices \> Update electronic invoice status**.
1. Filter the records to find those where the status must be updated.

> [!NOTE]
> The **To status** and **To message status** fields can't be updated. You can update only CFDI documents that have a status of **In progress**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
