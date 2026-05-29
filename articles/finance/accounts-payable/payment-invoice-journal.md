---
title: Apply a payment schedule to the invoice journal
description: Learn about how to add and apply a payment to the vendor invoice journal, including an overview on limitations.
author: sunfzam
ms.author: shpandey
ms.topic: how-to
ms.date: 05/26/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-08-30
ms.search.form: 
ms.dyn365.ops.version: 10.0.25
---

# Apply a payment schedule to the invoice journal

[!include [banner](../includes/preview-banner.md)]

To use a payment schedule on the **Vendor invoice journal**, you must enable the **Apply payment schedule to invoice journal** feature in Feature management.

After you enable the feature, a new **Payment schedule** field is added to the **Invoice journal** page. When you create an invoice journal line, if you maintain payment terms on the vendor and select the payment terms on the payment schedule, the **Payment schedule** field updates on the **Invoice journal** page.

You can change the payment schedule that you use, according to your business requirement. During posting of the vendor invoice journal, the system creates vendor open transactions according to the payment schedule.

- To review multiple vendor open transactions that the payment schedule generated, go to **Accounts payable \> Invoices \> Open vendor invoices**, and enter the invoice number or the vendor account.
- To review or configure the payment schedule, go to **Accounts payable \> Payment Setup \> Payment schedule**.
- To configure the payment terms and assign a payment schedule, go to **Accounts payable \> Payment setup \> Terms of payment**.
- To maintain the payment terms on a vendor, go to **Accounts payable \> All vendors**, select the vendor account, and then, on the **Payment** tab, set the **Terms of payment** field.

The payment schedule feature is also available in the **Vendor invoice register** process. If a payment schedule is selected on the invoice register journal, multiple vendor payment lines will **not** be generated when the invoice register is posted. The vendor payment lines are generated when the invoice is approved.

## Limitation

For a pending vendor invoice, if the payment schedule is on the invoice header, there's an advanced page that lets users edit the payment lines. For example, users can edit the due date and value for each payment line. Payment lines that the invoice journal generates have the value from the payment schedule.

This functionality will be available for the **Vendor invoice journal** and **Pending invoices** in a future release.

## Merge a payment schedule

Starting with Dynamics 365 Finance release 10.0.42, you can merge open transactions that you split from the same payment schedule by using the **Merge payment schedule** button.

The **Merge payment schedule for customer transactions or vendor transactions** feature in Feature management introduces this functionality. When you turn on that feature, follow these steps to merge a payment schedule:

1. Go to **All vendors** or **All customers** > **Transactions** > **Settle transactions**.
1. Select **Payment schedule**, and then select **Merge payment schedule**.
1. Mark open transactions that the payment schedule splits.
1. Select **Mark as primary payment** to select the main payment.
1. Select **Merge payment schedule** to combine all the marked transactions into one payment that has the same due date as the primary payment.
