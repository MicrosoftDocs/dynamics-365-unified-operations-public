---
title: Bank statement and payment reconciliation for the EU
description: Learn about the functionality that you can use to reconcile payment information from banks in formats that are used by European countries/regions.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Belgium, Norway, Sweden, Switzerland
ms.search.validFrom: 2016-11-30
ms.search.form: BankAccountTable, CustPaymMode, VendPaymMode
---

# Bank statement and payment reconciliation for the EU

[!include [banner](../../includes/banner.md)]

This article provides an overview of the functionality that you can use to reconcile payment information from banks in formats that European countries and regions use. You can import transactions from banks and settle these transactions against existing transactions. In Europe, you can use this functionality for the following scenarios:

- Importing bank statements
- Importing payments
- Importing return files

## Bank statements

A *bank statement* or *account statement* is a summary of financial transactions that occur over a given period on a bank account that a company holds with a financial institution. In Finance, you can import a bank statement. It's important to settle imported transactions with existing transactions and verify the opening and ending balance of the bank accounts. The following list includes the supported European formats.

- Advanced bank reconciliation European file formats. For more information, see [Advanced bank reconciliation overview](../../cash-bank-management/advanced-bank-reconciliation-overview.md).
- ISO 20022 camt.053 bank statement message file format.
- CODA bank statement file format. For more information, see [CODA bank statement](../belgium/emea-bel-coda-bank-statement-import.md).

## Customer and vendor payments import and return messages

In addition to a bank statement, banks can provide specific messages that contain information about customer and vendor payments. You can import these messages into Finance and reconcile them with customer and vendor transactions. When a company needs to receive information about incoming customer payments transactions from the bank, use the import formats. For companies that use direct debit and credit transfer, you can receive return messages to update the status of payments that you previously exported. The difference between import formats and return formats is that returns mostly update already created payment journal lines (you can create these lines when direct debit or credit transfer is initiated) instead of creating new lines. Some complex import formats can also include return scenarios. The following example shows how to implement this division.

### Import formats

- [ISO 20022 camt.054](emea-ISO20022-file-formats.md) bank notification message
- [Nets import format](../norway/emea-nor-nets-import-format.md) - Complex feature for Norwegian payment formats
- [ESR customer payments import](../switzerland/emea-che-esr-customer-payments-import.md)
- Import payment formats for Sweden - BankGirot Max and BankGirot OCR formats

### Return formats

- [ISO 20022 pain.002](emea-ISO20022-file-formats.md) payment status report
- (DNK) BetalingsserviceBasis-returformat – Return format for customer Betalingsservice export format
- [Import payment formats for Sweden](../sweden/emea-swe-payment-formats-import.md) - Bankgirot Autogiro returns
- (SWE) BankGirot return – Vendor payments return format, which corresponds to Bankgirot export format

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
