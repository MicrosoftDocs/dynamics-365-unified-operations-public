---
# required metadata

title: ESR customer payments import | Microsoft Docs
description: This topic provides information about importing customer payments in the ESR format.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-19 17:07:48
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: CustPaymMode, LedgerJournalTransCustPaym
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 81
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 264584
ms.assetid: b03e298f-7594-4281-bd65-860bd974f2c9
ms.region: Switzerland
# ms.industry: 
ms.author: v-lenest

---

# ESR customer payments import

This topic provides information about importing customer payments in the ESR format.

ESR is an electronic debtor service that uses payment slips to collect money. It is the standard electronic payment system created by the Swiss Post. You can receive customer payment files in the ESR format, which can include transactions and bank fees. This functionality is intended for imported customer transactions based on payment references that were originally generated in Microsoft Dynamics 365 for Operations and printed on the payment slip.

## Generate payment references
Payment references should be printed on the payment slip after posting. You can also verify payment references on the **Invoice journal** page for the selected sales order. To generate payment references, the following settings must be specified.

1.  Set the bank account settings to **ESR**, **BESR ID,** and **Routing number**.
2.  Set the **Number of characters for Giro account** field on the **Account Receivables parameters** page on the **Ledger and sales tax** tab. This defines how many symbols from the customer account should be included in the payment reference.
3.  The sales invoice number sequence should be in the correct format (it should not have symbols other than digits and it should not contain leading zeros).
4.  The **Orange** format should be specified for the customer account in the **On a customer invoice** field on the **Invoice and delivery** tab.

For more information, see [Payment slip report (Giro)](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/europe/eur-payment-slip-report-giro).

## Import a payment file
1.  Go to the **Payment journal** page
2.  Click **Lines**.
3.  Click **Functions** &gt; **Import payments**.
4.  In the dialog box, select the method of payment, and then browse to the location of the file to import. **Note**: Before you can complete this step, you must have already imported the **ESR (CH)** configurations from Lifecycle Services (LCS) and set up the ESR method of payment. For more information, see [File formats for method of payments](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/europe/select-file-formats-for-the-method-of-payments).

After you import the payment file, payment journal lines are created and marked for settlement with customer invoices based on the payment reference. If there are any fees specified for the bank account that are represented in the file, such as transactions between the main account and fee account, these fees will be added to the journal.

