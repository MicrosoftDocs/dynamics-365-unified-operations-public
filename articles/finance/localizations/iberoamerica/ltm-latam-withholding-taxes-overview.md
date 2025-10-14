---
title: LATAM withholding taxes overview
description: Provides information about LATAM Withholding taxes functionality.
author: Fhernandez0088
ms.date: 10/07/2025
ms.topic: overview
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# LATAM withholding taxes overview 

[!INCLUDE[banner](../../includes/banner.md)]

This article provides information about Latin American (LATAM) withholding functionality in Dynamics 365 Finance. Tax withholdings are amounts that you deduct from payments to vendors or collect from customers in compliance with local tax regulations. These amounts can apply to income tax, value-added tax (VAT), or other local taxes.

## Supported scenarios

The localization supports two main scenarios:
- Withholdings at the time of invoice registration (accrual)
- Withholdings at the time of payment

### Withholdings at the time of invoice registration (accrual)

To accrue tax withholdings when you receive a vendor invoice, use the tax calculation functionality in Finance by applying the negative tax option.

#### Example:

Taxable base: 150,000
VAT 16%: 24,000
VAT withholding base: 24,000
VAT withholding rate: 75%
Calculated VAT withholding: 18,000

Ledger accounting registration example:

|   | Debit | Credit |
| ------------- |--------|--------|
| Expense concept | 150000| |
| VAT credit      | 24000| |
| VAT withholding 75% accrual |     |18000 |
| Vendor account | 156000 |

Learn how to configure withholding taxes in [Configure withholding taxes at invoice posting](ltm-configure-withholdings-inovice.md) and how to register transactions in [Post vendor invoices with withholding taxes](ltm-post-invoice-withholdings.md).

### Withholdings at the time of payment

In some scenarios, you register tax withholdings when you pay the vendor. This scenario means you receive the vendor invoice first and then make the payment and register the withholding later. In these cases, use the LATAM tax withholding calculation functionality.

#### Example:

Taxable base: 150,000
VAT 16%: 24,000
VAT withholding base: 24,000
VAT withholding rate: 75%
Calculated VAT withholding: 18,000

Invoice ledger accounting registration example:

|   | Debit | Credit |
| ------------- |--------|--------|
| Expense concept | 150000| |
| VAT credit      | 24000| |
| Vendor account ||174000|

Payment ledger accounting registration example:

|   | Debit | Credit |
| ------------- |--------|--------|
| Vendor account | 174000| |
| VAT withholding 75% | 18000| |
| Bank transfer ||156000|

Learn how to configure LATAM withholding taxes for payments in [Configure LATAM Withholding taxes for payments](ltm-configure-LATAM-withholdings.md). For more information about how to register transactions, see [Post vendor payment transactions with LATAM Withholding taxes](ltm-post-payment-LATAM-withholdings.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
