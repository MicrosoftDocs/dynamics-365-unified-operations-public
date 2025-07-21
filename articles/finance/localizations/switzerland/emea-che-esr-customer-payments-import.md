---
title: ESR customer payments import
description: Learn how to import customer payments in the ESR format for Switzerland in Microsoft Dynamics 365 Finance.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/21/2025
ms.reviewer: johnmichalak
ms.search.region: Switzerland
ms.search.validFrom: 2016-11-30
ms.search.form: CustPaymMode, LedgerJournalTransCustPaym
---

# ESR customer payments import

[!include [banner](../../includes/banner.md)]

This article explains how to import customer payments in the Einzahlungsschein mit Referenznummer (ESR) format for Switzerland in Microsoft Dynamics 365 Finance.

ESR is an electronic debtor service that uses payment slips to collect money. It's the standard electronic payment system created by the Swiss Post. You can receive customer payment files in the ESR format, which can include transactions and bank fees. This functionality is intended for imported customer transactions based on payment references that were originally generated in Dynamics 365 Finance and printed on the payment slip.

## Generate payment references

Payment references should be printed on the payment slip after posting. You can also verify payment references on the **Invoice journal** page for the selected sales order.

To generate payment references, follow these steps.

1. In Dynamics 365 Finance, go to the **Invoice journal** page.
1. Set the bank account settings to **ESR**, **BESR ID,** and **Routing number**.
1. On the **Account Receivables parameters** page, on the **Ledger and sales tax** FastTab, in the **Number of characters for Giro account** field, enter a number that defines how many symbols from the customer account should be included in the payment reference.
1. Check that the sales invoice number sequence is in the correct format. It shouldn't contain leading zeros or symbols other than digits.
1. On the **Invoice and delivery** FastTab, in the **On a customer invoice** field, specify the **Orange** format for the customer account.

Learn more in [Payment slip report for Europe](../europe/emea-eur-payment-slip-report-giro.md).

## Import a payment file

To import a payment file, follow these steps.

1. In Dynamics 365 Finance, go to the **Payment journal** page.
1. Select **Lines**.
1. Select **Functions** \> **Import payments**.
1. In the dialog, select the method of payment, and then browse to the location of the file to import. 

    > [!NOTE]
    >  Before you can complete this step, you must import the **ESR (CH)** configurations from Lifecycle Services (LCS) and set up the ESR method of payment. Learn more in [File formats for methods of payment](../europe/emea-select-file-formats-for-the-method-of-payments.md).

After you import the payment file, payment journal lines are created and marked for settlement with customer invoices based on the payment reference. If there are any fees specified for the bank account that are represented in the file (for example, transactions between the main account and fee account) these fees are added to the journal.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
