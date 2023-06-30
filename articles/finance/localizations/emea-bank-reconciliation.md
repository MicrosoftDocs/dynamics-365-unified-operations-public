---
title: Bank statement and payment reconciliation for the EU
description: This article provides an overview of the functionality that you can use to reconcile payment information from banks in formats that are used by European countries/regions.
author: AdamTrukawka
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Belgium, Norway, Sweden, Switzerland
ms.author: atrukawk
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 267994
ms.search.form: BankAccountTable, CustPaymMode, VendPaymMode
---

# Bank statement and payment reconciliation for the EU

[!include [banner](../includes/banner.md)]

This article provides an overview of the functionality that you can use to reconcile payment information from banks in formats that are used by European countries/regions. You can import transactions from banks and settle these transactions against existing transactions. In Europe, you can do this for the following scenarios:

-   Importing bank statements
-   Importing payments
-   Importing return files

## Bank statements
A *bank statement* or *account statement* is a summary of financial transactions that have occurred over a given period on a bank account held by a company with a financial institution. In Finance, you can import a bank statement. It is important to settle imported transactions with existing transactions as well as verify the opening and ending balance of the bank accounts. The following list includes the supported European formats.

-   Advanced bank reconciliation European file formats. For more information, see [Advanced bank reconciliation overview](../cash-bank-management/advanced-bank-reconciliation-overview.md).
-   ISO 20022 camt.053 bank statement message file format.
-   CODA bank statement file format. For more information, see [CODA bank statement](emea-bel-coda-bank-statement-import.md).

## Customer and vendor payments import and return messages
In addition to a bank statement, banks can provide specific messages, containing information about customer and vendor payments, which can be imported into Finance and reconciled with customer and vendor transactions. When a company needs to receive information about incoming customer payments transactions from the bank, the import formats can be used. For companies that use direct debit and credit transfer, the return messages can be received to update the status of payments that were previously exported. The difference between import formats and return formats is that returns are targeted mostly to update already created payment journal lines (they can be created when direct debit or credit transfer were initiated) instead of creating new lines. Some complex import formats can also include return scenarios. The following example shows how this division should be implemented.

### Import formats

-   [ISO 20022 camt.054](emea-ISO20022-file-formats.md) bank notification message
-   [Nets import format](emea-nor-nets-import-format.md) - Complex feature for Norwegian payment formats
-   [ESR customer payments import](emea-che-esr-customer-payments-import.md) 
-   Import payment formats for Sweden - BankGirot Max and BankGirot OCR formats

### Return formats

-   [ISO 20022 pain.002](emea-ISO20022-file-formats.md) payment status report
-   (DNK) BetalingsserviceBasis-returformat – Return format for customer Betalingsservice export format
-   [Import payment formats for Sweden](emea-swe-payment-formats-import.md) - Bankgirot Autogiro returns
-   (SWE) BankGirot return – Vendor payments return format, which corresponds to Bankgirot export format




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
