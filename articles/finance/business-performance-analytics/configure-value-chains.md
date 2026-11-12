---
title: Configure value chains in Business performance analytics
description: Learn what Value chain configuration is in Business performance analytics, how to enable and disable value chains, and which facts and dimensions are included for each value chain.
author: jinniew
ms.author: jiwo
ms.topic: how-to
ms.date: 10/20/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
---

# Configure value chains in Business performance analytics

[!INCLUDE [banner](../../includes/banner.md)]

## What this feature is

The **Value chain configuration** feature gives Business performance analytics admins a self-service way to control which value chains are enabled in their environment (for example, enabling O2C without opening a support ticket).

When you enable a value chain, its associated facts become available for Business performance analytics reporting and insights.  
When you disable a value chain, you turn off that data path.

The system retains data that it previously brought in by default (it doesn't automatically delete it).  
If cleanup is needed, you can request a manual cleanup.

The system retains data to avoid accidental data loss, preserve historical reporting continuity, and give admins explicit control over when deletion happens.

## What users see in the experience

Each value chain row or card shows:

- Business domain or module
- Last modified time
- Facts included in that value chain
- Current state (**Enabled** or **Disabled**)

This information gives admins enough context to decide what to turn on or off.

### Enable a value chain

To enable a value chain, follow these steps:

1. Open the **Data model configuration** page in Business performance analytics.
1. Find the value chain you want to enable (for example, O2C).
1. Review the listed facts and current status.
1. Turn the toggle **On**.
1. Confirm in the prompt.
1. Verify the value chain now shows as **Enabled**.

### Disable a value chain

To disable a value chain, follow these steps:

1. On the same page, locate the enabled value chain.
1. Turn the toggle **Off**.
1. Confirm in the prompt.
1. Verify the value chain now shows as **Disabled**.

#### Value chain facts and dimensions

> [!NOTE]
> Facts are listed by technical table name (with business-friendly name in parentheses).  
> Dimensions are the union of dimensions mapped in the business matrix for facts in that value chain.

#### Record to report: enabled facts and dimensions

#### Facts

- `dmo_budgetfact` (budget)
- `dmo_generalledgerfact` (general ledger)
- `dmo_generalledgertracefactless` (general ledger trace factless)

#### Dimensions

- Currency
- Date (Accounting)
- General ledger account
- Ledger dimension
- Reporting dimension

#### Procure to pay: enabled facts and dimensions

#### Facts

- `dmo_productreceiptfact` (product receipt)
- `dmo_purchaseinvoicefact` (purchase invoice)
- `dmo_purchaseinvoicematchingfact` (purchase invoice matching)
- `dmo_purchaseorderfact` (purchase order)
- `dmo_purchasepaymentfact` (purchase payment)
- `dmo_purchasepaymentmatchingfact` (purchase payment matching)
- `dmo_purchaserequisitionfact` (purchase requisition)
- `dmo_purchasesubledgerfact` (purchase sub-ledger)

### Dimensions

- Asset
- Currency
- Date (Accounting)
- Delivery method
- Delivery postal address
- Ledger dimension
- Party
- Payment postal address
- Procurement category
- Product
- Product receipt number
- Project
- Purchase invoice line number
- Purchase invoice number
- Purchase matched document number
- Purchase matching document number
- Purchase order line number
- Purchase order number
- Purchase requisition number
- Requesting party
- Selling party
- Selling party postal address
- Storage location
- Sub-ledger number

#### Order to cash: enabled facts and dimensions

#### Facts

- `dmo_bankregisterfact` (bank register)
- `dmo_bankstatementfact` (bank statement)
- `dmo_packingslipfact` (packing slip)
- `dmo_pickinglistfact` (picking list)
- `dmo_returnauthorizationfact` (return authorization)
- `dmo_salescontractbillingschedulefact` (sales contract billing schedule)
- `dmo_salesdeferralschedulefact` (sales deferral schedule)
- `dmo_salesinvoicefact` (sales invoice)
- `dmo_salesorderfact` (sales order)
- `dmo_salespaymentfact` (sales payment)
- `dmo_salespaymentmatchingfact` (sales payment matching)
- `dmo_salessubledgerfact` (sales sub-ledger)
- `dmo_serviceorderfact` (service order)

### Dimensions

- Bank account
- Buying party
- Buying party delivery address
- Buying party postal address
- Currency
- Date (Accounting)
- Delivery method
- Ledger dimension
- Packing slip line number
- Packing slip number
- Party
- Picking list line number
- Picking list number
- Product
- Project
- Return authorization number
- Sales category
- Sales invoice line number
- Sales invoice number
- Sales order line number
- Sales order number
- Sales payment matched number
- Sales payment matching number
- Sales payment number
- Service activity
- Service object
- Service order line number
- Service order number
- Storage location
- Sub-ledger number

#### Acquire-to-dispose: enabled facts and dimensions

### Facts

- `dmo_assetleaseamortizationfact` (asset lease amortization)
- `dmo_assetleasedepreciationfact` (asset lease depreciation)
- `dmo_assetleaseexpensefact` (asset lease expense)
- `dmo_assetleasefact` (asset lease)
- `dmo_assetleasepaymentfact` (asset lease payment)
- `dmo_assetsubledgerfact` (asset sub-ledger)
- `dmo_assettransactionfact` (asset transaction)
