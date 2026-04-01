---
title: Deferred sales tax calculations
description: Learn how to set up deferred sales tax calculations and VAT posting for Hungary, including outlines on setting up deferred VAT posting and ledger accounts.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/19/2026
ms.reviewer: johnmichalak
ms.search.region: Hungary
ms.search.validFrom: 2016-11-30
ms.search.form: AssetParameters
---

# Deferred sales tax calculations

[!include [banner](../../includes/banner.md)]

In Hungary, you must record and report value-added tax (VAT) on the continuous delivery of services, such as renting, leasing, consulting, and heating, on the due date. This functionality processes the general ledger postings for VAT amounts to the deferred VAT payable and deferred VAT receivable accounts. You can also transfer amounts to regular sales tax accounts on the due date of the invoice.

Deferred tax postings work for the following document types and journals:

- Sales orders
- Free text invoices
- Purchase orders
- Invoice journals
- Invoice registers
- Invoice approval journals

When you configure this feature, the system creates the following sales tax transactions when you post the transaction:

- The system posts the sales tax amount on the posting date to the deferred tax account.
- The system reverses the sales tax amount on the date of the VAT register from the deferred tax account.
- The system posts the sales tax amount on the date of the VAT register to the default sales tax payable or sales tax receivable account.

For free text invoices and purchase orders, if you distribute the document line amounts among financial dimensions, the system distributes the sales tax amounts the same as the document line amounts.

## Set up deferred VAT posting 

You can specify that the system posts VAT to a deferred VAT account.

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Item sales tax groups**.
2. On the **Item sales tax groups** page, select the **Deferred VAT** check box to specify that the system posts VAT to a deferred VAT account.

## Set up ledger accounts for deferred VAT posting

You can designate the deferred VAT posting on ledger accounts.

1. Go to **Tax** > **Setup** > **Sales tax** > **Ledger posting groups**.
2. On the **Ledger posting groups** page, select a ledger posting group from the list and add the following information.

- **Deferred VAT payable** - Select the deferred VAT account or tax debit account for the selected ledger posting group.
- **Deferred VAT receivable** - Select the deferred VAT account or tax credit account for the selected ledger posting group.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
