---
title: Tax invoice for goods delivered for free
description: Learn about tax invoices for goods that were delivered for free, including a step-by-step process for setting up the summary update parameters.
author: mrolecki
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2019-11-01
ms.search.form: 
ms.dyn365.ops.version: 10.0.8
---

# Tax invoice for goods delivered for free

[!include [banner](../../includes/banner.md)]

This article explains how to manage goods that you deliver free of charge. The **Tax invoice for goods delivered for free** feature enables you to generate invoices that include the words "Free invoice." The total of these invoices equals the tax amount only.

To generate these invoices, set up delivery reasons that you can use in the sales order.

Use these invoices in two cases, depending on who pays the taxes on the items:

- Your company pays the sales tax. The system generates a self-invoice and accounting entries for the payment.
- The customer pays the sales tax.

The delivery reason on the invoice determines which case you use.

## Prerequisites

- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, turn on the **Tax invoice for goods delivered for free** feature. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up the summary update parameters

You can set up the summary update parameters only if a delivery reason is available for both the packing slip and the invoice.

1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
1. On the **Summary update** tab, select **Summary update parameters**.
1. The **Delivery reason** summary update parameter must be selected for both packing slips and invoices. On the **Invoice** tab, in the **Available** list, select **Delivery reason**.
1. Select the right arrow button to move **Delivery reason** to the **Selected** list. Repeat this step on the **Packing slip** tab.

  :::image type="content" source="../media/emea-ita-exil-free-goods-summary-update-parameters.jpg" alt-text="Screenshot of the Summary update parameters page.":::

## Set up a Sales for free account

Follow these steps to set up the accounting account for free sales.

1. Go to **Inventory management** > **Setup** > **Posting** > **Posting**.
1. Select the **Sales for free** option.
1. Set up the main account by selecting the required relations and account codes.

  :::image type="content" source="../media/emea-ita-exil-free-goods-sales-free-account.jpg" alt-text="Screenshot of the Sales for free account setup page.":::

## Set up miscellaneous charges

You might not always need or want miscellaneous charges when you issue free sales invoices. Follow these steps to exclude miscellaneous charges when they're automatically generated.

1. Go to **Accounts receivable** > **Charges setup** > **Charges code**.
1. Create or select an existing charges code.
1. Set the **Exclude charge in free invoices** option to **Yes**.

  :::image type="content" source="../media/emea-ita-exil-free-goods-charges-codes.jpg" alt-text="Screenshot of the Charges codes page.":::

## Set up delivery reasons

1. Go to **Sales and marketing** > **Setup** > **Distribution** > **Reasons for delivery**.
1. Select the **Goods for free** check box.
1. In the **Invoice account** field, select the customer account that represents your company.
1. In the **Terms of payment** field, specify cash terms of payment.

  :::image type="content" source="../media/emea-ita-exil-free-goods-delivery-reason.jpg" alt-text="Screenshot of the Reasons for delivery page.":::

  > [!NOTE]
  > The company issues a self-invoice to account for required taxes for goods that are delivered for free. In addition to the invoice posting, the accounting entries for the payment must be generated. To make that process available, you must have a customer account that represents your company. In this case, the invoice account on a sales order is set to the company customer account by default. Therefore, the invoice that you issue is a self-invoice. When you specify cash term of payments, the payment occurs in addition to the self-invoice. Finally, the customer transaction is closed, and the amount is posted to the cash account that is specified in the **Terms of payment** field. This field is also set by default on a sales order header.
  >
  > If your customer pays the taxes, leave the **Invoice account** and **Terms of payment** fields blank.

## Posting tax invoices for goods delivered for free

When you create a sales order for goods that are delivered for free, the specified delivery reason determines whether a self-invoice is generated for your company, or whether an invoice is generated for your customer. If you use cash terms of payment, payment accounting entries are also created when you post the sales invoice.

## Printing tax invoices for goods delivered for free

The invoice printout shows the title **Free invoice**. Additionally, items are prefixed with **Free item:** if the **Goods for free** flag is active on the delivery reason that is used for the order.

:::image type="content" source="../media/emea-ita-exil-free-tax-invoice-printout.jpg" alt-text="Screenshot of the Free invoice printout.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
