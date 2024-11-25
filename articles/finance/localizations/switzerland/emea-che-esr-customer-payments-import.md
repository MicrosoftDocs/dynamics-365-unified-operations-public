---
title: ESR customer payments import
description: Learn about importing customer payments in the ESR format, including an outline and step-by-step process on generating payment references.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/20/2017
ms.reviewer: johnmichalak
ms.search.region: Switzerland
ms.search.validFrom: 2016-11-30
ms.search.form: CustPaymMode, LedgerJournalTransCustPaym
ms.dyn365.ops.version: Version 1611
---

# ESR customer payments import

[!include [banner](../../includes/banner.md)]

This article provides information about importing customer payments in the ESR format.

ESR is an electronic debtor service that uses payment slips to collect money. It is the standard electronic payment system created by the Swiss Post. You can receive customer payment files in the ESR format, which can include transactions and bank fees. This functionality is intended for imported customer transactions based on payment references that were originally generated in Dynamics 365 Finance and printed on the payment slip.

## Generate payment references
Payment references should be printed on the payment slip after posting. You can also verify payment references on the **Invoice journal** page for the selected sales order. To generate payment references, the following settings must be specified.

1.  Set the bank account settings to **ESR**, **BESR ID,** and **Routing number**.
2.  Set the **Number of characters for Giro account** field on the **Account Receivables parameters** page on the **Ledger and sales tax** tab. This defines how many symbols from the customer account should be included in the payment reference.
3.  The sales invoice number sequence should be in the correct format (it should not have symbols other than digits and it should not contain leading zeros).
4.  The **Orange** format should be specified for the customer account in the **On a customer invoice** field on the **Invoice and delivery** tab.

For more information, see [Payment slip report for Europe](../europe/emea-eur-payment-slip-report-giro.md).

## Import a payment file
1. Go to the **Payment journal** page
2. Click **Lines**.
3. Click **Functions** &gt; **Import payments**.
4. In the dialog box, select the method of payment, and then browse to the location of the file to import. 
   > [!NOTE]
   >  Before you can complete this step, you must have already imported the **ESR (CH)** configurations from Lifecycle Services (LCS) and set up the ESR method of payment. For more information, see [File formats for methods of payment](../europe/emea-select-file-formats-for-the-method-of-payments.md).

After you import the payment file, payment journal lines are created and marked for settlement with customer invoices based on the payment reference. If there are any fees specified for the bank account that are represented in the file, such as transactions between the main account and fee account, these fees will be added to the journal.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
