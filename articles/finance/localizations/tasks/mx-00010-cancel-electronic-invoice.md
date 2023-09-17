---
title: MX-00010 Cancel an electronic invoice
description: You can cancel a CFDI electronic invoice that was previously validated and certified by the PAC.
author: AdamTrukawka
ms.date: 06/29/2022
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Mexico
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: EInvoiceCFDIJournal_AR
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

You can specify the reason for the cancellation. When you select **Functions** \> **Cancel CFDI** on the Action Pane, you can select a cancellation reason. If you select **01** as the reason, fill in a replacement document to replace the current document.

## Manually cancel a CFDI electronic invoice

1. Select an invoice that has a status of **Approved**.
2. On the Action Pane, select **Functions** \> **Manual cancel**.
3. Enter the date of the cancellation.
4. In the **Cancel key name** field, enter the reason for the cancellation.
5. Select **OK** to confirm the cancellation of the electronic invoice. The status of electronic invoice is changed to **Manual cancel**.

## Manually update the status of a CFDI document that is in progress after cancellation

You can use the **Update electronic document status** periodic task to update the status a CFDI document that is **In progress** for a long time after cancellation, if the document was canceled in a PAC application.

1. Go to **Accounts receivable** \> **Invoices** \> **E-invoices** \> **Update electronic invoice status**.
2. Filter the records to find those where the status must be updated.

> [!NOTE]
> The **To status** and **To message status** fields can't be updated. You can update only CFDI documents that have a status of **In progress**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
