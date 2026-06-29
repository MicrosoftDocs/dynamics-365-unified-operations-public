---
title: Fiscal notes for advance payment in Brazil tax reform
description: Learn about how to create Fiscal notes for advance payment in Brazil tax reform.
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 06/22/2026
ms.custom: bap-template
---

# Fiscal notes for advance payment in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article explains how to create a fiscal document for an advance payment in Brazil tax reform, link it to a sales order, and post the invoice in Dynamics 365 Finance.

> [!IMPORTANT]
> Advance payment fiscal notes are available for **Accounts receivable only**. This functionality doesn't apply to Accounts payable.

## Create an advance payment fiscal document

Create the advance payment fiscal document (fiscal note) from **Accounts receivable** > **Fiscal notes**, not from the sales order.

To create an advance payment fiscal document, follow these steps:

1. Go to **Accounts receivable** > **Fiscal notes** > **All Fiscal notes**.
1. Select **Business Type**.
1. Select **Advance payment**.
1. In the **Total amount** field, enter a number.
1. In the **Sales Orders** field, enter or select a value.

   > [!NOTE]
   > The lookup shows only **non-posted (open) sales orders** for the selected customer. Posted sales orders aren't shown.

1. In the list, select the link in the selected row.
1. In the **Fiscal document type** field, enter or select a value.
1. In the list, select the desired row.
1. In the list, select the link in the selected row.
1. Select **OK**.

## Add lines to the fiscal document

To add item lines to the advance payment fiscal document, follow these steps:

1. Select **Add line**.
1. In the list, select the row.
1. In the **Item number** field, enter or select a value.
1. In the list, select the desired row.
1. In the list, select the link in the selected row.
1. In the **Line description** field, type a value.
1. In the **Quantity** field, enter a number.
1. In the **Net amount** field, enter a number.
1. In the **CFOP** field, enter or select a value.

   > [!NOTE]
   > CFOP is mandatory on each line. The line can't be posted without a valid CFOP code.

1. Close the page.
1. In the **CFOP** field, type a value.
1. In the **Item sales tax group** field, enter or select a value.

## Set up taxes for the fiscal document lines

To configure the sales tax group and item sales tax group on the lines, follow these steps:

1. Select the **Setup** tab.
1. In the **Item sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
1. Close the page.
1. In the **Item sales tax group** field, enter or select a value.
1. Close the page.
1. In the **Item sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, type a value.
1. In the **Sales tax group** field, type a value.
1. Select **Sales tax**.
1. Select **OK**.

## Post the advance payment fiscal document

To post the advance payment fiscal document, follow these steps:

1. Select the **Header** tab.
1. Expand the **Delivery address** section.
1. Expand the **Fiscal information** section.
1. Select the **Lines** tab.
1. Select **Post**.
1. Close the page.
1. Refresh the page.
1. Close the page.

> [!NOTE]
> After posting, the system stores the fiscal document. You can also access it from **Accounts receivable** > **Fiscal notes** > **All customer fiscal notes**. You can see draft (unposted) fiscal notes in this location too, and you can continue to edit them.

## Link the advance payment fiscal document as a fiscal reference on the sales invoice

After you post the advance payment fiscal document, manually link it as a fiscal reference when posting the sales order invoice. This link is **one-directional** - you set it on the invoice, and the advance payment fiscal note doesn't automatically show the invoice in return.

> [!IMPORTANT]
> Add the fiscal reference **at the time of posting** the sales invoice. You can't add it to a fiscal document after posting.

To link the advance payment fiscal document to the sales invoice, follow these steps:

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. In the list, select the row.
1. Select **Invoice**.
1. Select **Fiscal reference**.
1. Select **Fiscal document**.
1. Select **Customer** to add a field to the view.
1. Use the Quick Filter to find records. For example, filter on the **Field** field with a value of `*typ*`.
1. In the list, find and select the advance payment fiscal document.
1. Select the **Select** check box.
1. Select **Update**.
1. Open the **Document date** column filter.
1. Sort newest to oldest.
1. In the list, select the row.
1. Select **OK**.
1. Select **Save**.
1. Close the page.
1. Select **OK**.
1. Select **OK**.
1. Select **Cancel**.
1. Close the page.

> [!NOTE]
> When you output the NFE (NF-e) for the sales invoice, the advance payment fiscal reference appears in a **dedicated section** of the fiscal document. This section is required for correct Brazil Tax Reform reporting.

## Post the sales invoice and verify

To post the sales invoice and verify the linked advance payment, follow these steps:

1. Go to **Accounts receivable** > **Fiscal notes** > **All customer fiscal notes**.
1. In the **Item sales tax group** field, enter or select a value.
1. In the list, select the link in the selected row.
1. Select **Post**.
1. In the **Invoice date** field, enter a date.
1. Select **Save**.
1. Refresh the page.
1. Select the form caption.
1. Close the page.
1. Go to **Default dashboard**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
