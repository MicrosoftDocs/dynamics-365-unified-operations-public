---
title: Payment slip report for Europe
description: Learn about payment slip reports for Europe, including an outline on setting up a creditor ID number for financial institutions in Denmark.
author: mrolecki
ms.author: mrolecki
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Belgium, Denmark, Finland, Norway, Switzerland
ms.search.validFrom: 2016-11-30
ms.search.form: OMLegalEntities, ProjFormletterParameters, CustFormletterParameters
ms.dyn365.ops.version: Version 1611
---

# Payment slip report for Europe

[!include [banner](../../includes/banner.md)]

This article provides information about payment slip reports for Europe.

The functionality for payment slip reports is available for legal entities that have their primary address in Denmark, Belgium, Norway, Switzerland, or Finland. Businesses often attach printed payment slips to invoices to provide a payment reference for posting and settlement. The payment slip can be used for project or service invoices, collection letters, interest notes, and account statements, in addition to sales invoices and free text invoices.

## Set up a creditor ID number (Denmark only)
Follow these steps to enter your company's creditor identification (ID) number. Your financial institution provides this number. It's used as a reference when customer payments are received through financial institutions.

1.  Click **Organization administration** &gt; **Setup** &gt; **Organization** &gt; **Legal entities**.
2.  On the **Bank account information** FastTab, in the **FI-Creditor ID** field, enter your unique eight-digit creditor ID number.
3.  Close the form to save your changes.

## Set up a payment slip attachment format for invoices, interest notes, collection letters, and account statements
Follow these steps to set up a format for payment slip attachments that accompany sales invoices, free text invoices, interest notes, collection letters, and account statements.

1.  Click **Accounts receivable** &gt; **Setup** &gt; **Forms** &gt; **Form setup**.
2.  On the **Invoice** tab, in the **Associated payment attachment on customer invoice** field, select the payment slip attachment format.
3.  On the **Free text invoice**, **Interest note**, **Collection letter**, and **Account statement** tabs, select a payment slip attachment format for each document type.
4.  Close the form to save your changes.

Follow these steps to set up a format for payment slip attachments that accompany project invoices.

1.  Click **Project management and accounting** &gt; **Setup** &gt; **Forms** &gt; **Form setup**.
2.  In the **Associated payment attachment** field, select the payment slip attachment format.

## Assign a payment slip attachment format to a customer account
After you set up the payment slip attachment format for sales invoices, free text invoices, interest notes, collection letters, account statements, and project invoices, you can assign specific formats for a selected customer.

1.  Click **Accounts receivable** &gt; **Common** &gt; **Customers** &gt; **All customers**.
2.  Create a new customer, or select an existing customer.
3.  On the **Invoice and delivery** FastTab, in the **On a customer invoice**, **On a free text invoice**, **On an interest note**, **On a collection letter**, **On a project invoice**, and **On an account statement** fields, select the format for payment slip attachments that will accompany documents of each type that are sent to the selected customer.
4.  Close the form to save your changes.


For more information about setting up and maintaining payment IDs, refer to [NO-00002 Customer payment based on payment ID](../norway/no-00002-customer-payment-based-payment-id.md).



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
