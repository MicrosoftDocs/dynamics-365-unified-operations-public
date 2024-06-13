---
title: Refund payment processing in the customer payment journal
description: Learn how to provide a refund to clients from the customer payment journal using the ISO20022 credit transfer format.
author: ankviklis
ms.author: ankviklis
ms.topic: article
ms.date: 11/08/2023
ms.reviewer: kfend
audience: Application User
ms.search.region: Global
ms.search.form: LedgerJournalTransCustPaym, LedgerJournalTransVendPaym
ms.search.validFrom: 2023-03-11
ms.assetid: 53533ee3-470e-458a-ac8b-3815aa4cb502
---

# Refund payment processing in the customer payment journal

[!include [banner](../includes/banner.md)]

This article explains how to provide a refund to clients from the customer payment journal using the ISO20022 credit transfer format. 

If a customer has a credit balance, you can refund the customer for the amount of the balance. This feature allows you to issue customer refunds and generate payment files using the ISO20022 credit transfer format in customer payments journals.

The following scenarios are supported:
- Refund or reimburse with a credit note.
- Refund a prepayment by using a payment proposal.
- Refund manually.

To configure the electronic payment format for customer refunds, follow these steps.

1. In Commerce headquarters, go to **Organization administration \> Workspaces \> Electronic reporting**.
1. Import the latest version of the **Payment model mapping for refunds to customers** configuration from the Microsoft global repository. For more information, see [Download ER configurations from the global repository of configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
1. Go to **Accounts receivable \> Payments setup \> Methods of payment**.
1. Select **New** to set up the customer’s method of payment for the ISO20022 credit transfer format.
1. In the **Payment type** field, select **Electronic Payment**.
1. On the **File formats** FastTab, under **FILE FORMATS**, set the **Generic electronic Export format** and **Export format for refunds** sliders to **Yes**. 

> [!NOTE]
> The same format configuration used for vendor payments specified at **FILE FORMATS \> Export format configuration** is also used for returning payments to customers.

For more information, see [Establish customer method of payment](tasks/establish-customer-method-payment.md).

To transfer a payment to a customer, you must provide the bank account details for the customer to whom you are providing the refunds. For more information, see [Set up a customer bank account](../localizations/europe/set-up-bank-accounts-iso20022-direct-debits.md#set-up-a-customer-bank-account).

To provide a refund to a specific customer account, in the customer payment journal, select the method of payment you created earlier, and then on the Action Pane, select **Functions \> Generate payments**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
