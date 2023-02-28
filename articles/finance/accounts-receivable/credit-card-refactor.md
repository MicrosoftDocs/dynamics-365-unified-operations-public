---
# required metadata

title: Process incomplete credit card payments
description: This article provides information about processing incomplete credit card payments.
author: sunfzam
ms.date: 02/14/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: ["13971", "intro-internal"]
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Process incomplete credit card payments

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article provides information about processing incomplete credit card payments.

Card payment is a typical payment scenario in the retail industry. In Microsoft Dynamics 365 Finance, the scenario looks like a single step. However, it's really composed of several steps:

1. Create a customer invoice for the sales order.
2. Issue a card payment (such as debit card, credit card, or gift card).
3. Post the payment in the general ledger.

In releases before Dynamics 365 Finance version 10.0.32, all these steps are done in one transaction. Card payments are external transactions that can't be rolled back in the event of errors. Therefore, any error that occurs can cause inconsistent payments.

As of version 10.0.32, the card payment process is split into several stages:

1. Create and post the customer invoice.
2. Capture or refund the credit card.
3. Post the payment journal.
4. Authorize the remaining payment amount.

The status of each stage is logged and monitored per invoice and sales order. If an error occurs in any step after the customer invoice is posted, users can review the failure reason and recover the payment process from the point where it failed.

## Prerequisites

1. In **Feature management** workspace, turn on feature that's named **Improve cards payment processing flow in customer payment**.
2. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
3. On the **Credit card** tab, on the **Setup** FastTab, set the **Cards payment status monitoring** option to **Yes**.

## View incomplete card payments

1. Go to **Accounts receivable \> Invoices \> Open customer invoices**.
2. On the **Invoice** tab, select **Incomplete cards payment** to open the **Incomplete cards payment** page.

    The **Incomplete cards payment** button is available only if the selected invoice is related to the card payment, or if no invoice was selected. If the selected invoice isn't related to the card payment, the button can't be selected.

    If no invoice was selected, the **Incomplete cards payment** page shows all incomplete cards payments.

## Resume an incomplete card payment

- On the **Incomplete cards payment** page, select a line, and then select **Resume**. The card payment process is restarted from the last failed stage.

## Terminate an incomplete card payment

- On the **Incomplete cards payment** page, select a line, and then select **Terminate**. The card payment process is terminated.

You must then follow these steps.

1. On the **Incomplete cards payment** page, select a line, and then select **View history**.

    The viewer that appears lists all the processed payment stages.

2. Select **Payment stage** to show the corresponding execution log.
