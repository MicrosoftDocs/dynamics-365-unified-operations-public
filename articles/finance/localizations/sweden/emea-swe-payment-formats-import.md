---
title: Import payment formats for Sweden
description: Learn how to import payment formats for Sweden in Microsoft Dynamics 365 Finance.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/21/2025
ms.reviewer: johnmichalak
ms.search.region: Sweden
ms.search.validFrom: 2016-11-30
ms.search.form: CustPaymMode, CustVendPaymReconciliation, LedgerJournalTransCustPaym, VendPaymMode
---

# Import payment formats for Sweden

[!include [banner](../../includes/banner.md)]

This article explains how to import payment formats for Sweden in Microsoft Dynamics 365 Finance.

## Import BankGirot MAX and BankGirot OCR payment formats

BankGirot MAX and BankGirot OCR file import lets you import customer payments in BankGirot file formats. BG MAX is a file layout that collects all payments in one file. OCR is a specific kind of reference in the BG MAX file format with a payment reference. 

To import files in the BankGirot MAX and BankGirot OCR payment formats, follow these steps:

1. In Dynamics 365 Finance, go to the **Payment journal** page.
1. Select **Lines**.
1. Select **Functions** \> **Import payments**.
1. In the dialog, select the method of payment, and then browse to the location of the file to import.

   > [!NOTE]
   >  Before you can complete this step, you must have already imported the configurations from Lifecycle Services (LCS) and set up the methods of payment. For more information, see [File formats for methods of payments](../europe/emea-select-file-formats-for-the-method-of-payments.md).

After you import the payment file, payment journal lines should be created for the selected journal and marked for settlement with customer invoices.

## Bankgirot Autogiro returns

Bankgirot Autogiro returns format for the direct debit payment format of the same name. These messages can be imported as a response to direct debit messages that were previously exported. Currently, these payments are represented in Operations as payment journal lines with a **Sent** status. 

To import a file in the Bankgirot Autogiro returns format, following these steps.

1. In Dynamics 365 Finance, go to the **Payment transfers** page.
1. Select **Return file-customer**.
1. In the dialog, select corresponding method of payment, and then browse to the location of the file to import. 

   > [!NOTE]
   >  Before you can complete this step, you must have already imported the configurations from Lifecycle Services (LCS) and set up the methods of payment. Learn more in [File formats for methods of payments](../europe/emea-select-file-formats-for-the-method-of-payments.md).

After you import the return file, the payments should be updated to the status **Approved**.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
