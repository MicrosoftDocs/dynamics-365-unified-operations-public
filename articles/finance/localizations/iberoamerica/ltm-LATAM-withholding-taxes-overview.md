---
title: Latam withholding taxes overview
description: Provides information about LATAM Withholding taxes functionality.
author: Fhernandez0088
ms.date: 10/03/2025
ms.topic: overview
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Latam withholding taxes overview 

This article provides information about Latin American (LATAM) withholding functionality in Dynamics 365 Finance. Tax withholdings are amounts deducted from payments to vendors or collected from customers in compliance with local tax regulations. These can apply to income tax, value-added tax (VAT), or other local taxes.

## Supported Scenarios

The localization supports two main scenarios:
- Withholdings at the time of invoice registration (accrual)
- Withholdings at the time of payment

### Withholdings at the time of invoice registration (accrual)

If you need to accrue tax withholdings when a vendor invoice is received, you can use the tax calculation functionality in Dynamics 365 Finance by applying the negative tax option.

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
| Vendor account ||156000|

Learn more how to configure in [Configure withholding taxes at invoice posting](ltm-configure-withholdings-inovice.md) and how to register transaction in [Post vendor invoices with withholding taxes](ltm-post-withholdings-invoice.md).

### Withholdings at the time of payment

In some scenarios, tax withholdings must be registered at the time of payment to the vendor. This means the vendor invoice is received at time 1, and the payment and withholding registration occur at time 2. In these cases, you can use the LATAM tax withholding calculation functionality.

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

Learn more on how to configure in [Configure LATAM Withholding taxes for payments](ltm-configure-LATAM-withholdings.md) and how to register transaction in [Post vendor payment transactions with LATAM Withholding taxes](ltm-post-payment-LATAM-withholdings.md).
