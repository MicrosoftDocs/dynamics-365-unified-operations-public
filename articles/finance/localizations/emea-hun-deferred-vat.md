---
# required metadata

title: Deferred sales tax calculations
description: This topic describes how to set up deferred sales tax calculations and VAT posting for Hungary.
author: anasyash
ms.date: 09/04/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetParameters
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 264684
ms.search.region: Hungary
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: 10.0.0

---

# Deferred sales tax calculations

[!include [banner](../includes/banner.md)]

In Hungary, value-added tax (VAT) on the continuous delivery of services, such as renting, leasing, consulting, and heating, must be recorded and reported on the due date. This functionality allows you to process the general ledger postings for VAT amounts to the deferred VAT payable and deferred VAT receivable accounts. You can also transfer amounts to regular sales tax accounts on the due date of the invoice.

Deferred tax postings work for the following document types and journals:

- Sales orders
- Free text invoices
- Purchase orders
- Invoice journals
- Invoice registers
- Invoice approval journals

When this feature is configured, the following sales tax transactions are created when the transaction is posted:

- The sales tax amount on the posting date is posted to the deferred tax account.
- The sales tax amount on the date of the VAT register is reversed from the deferred tax account.
- The sales tax amount on the date of the VAT register is posted to the default sales tax payable or sales tax receivable account.

For free text invoices and purchase orders, if the document line amounts are distributed among financial dimensions, the sale tax amounts are distributed the same as the document line amounts.

## Set up deferred VAT posting 

You can specify that VAT is posted to a deferred VAT account.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Item sales tax groups**.
2. On the **Item sales tax groups** page, select the **Deferred VAT** check box to specify that VAT is posted to a deferred VAT account.

## Set up ledger accounts for deferred VAT posting

You can designate the deferred VAT posting on ledger accounts.

1. Go to **Tax \> Setup \> Sales tax \> Ledger posting groups**.
2. On the **Ledger posting groups** page, select a ledger posting group from the list and add the following information.

- **Deferred VAT payable** - Select the deferred VAT account or tax debit account for the selected ledger posting group.
- **Deferred VAT receivable** - Select the deferred VAT account or tax credit account for the selected ledger posting group.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]