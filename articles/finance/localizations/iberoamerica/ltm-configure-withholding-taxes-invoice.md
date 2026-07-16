---
title: Configure withholding taxes at invoice posting
description: Learn how to configure the withholding taxes to apply to vendor invoices.
author: SandraYamamoto0602
ms.date: 06/16/2026
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-sandraya
---

# Configure withholding taxes at invoice posting

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](includes/does-not-apply-to.md)]

This article describes how to configure withholding taxes that apply when you post a vendor invoice that uses negative tax codes.
Several LATAM Expansion reports use these types of withholdings in many countries and regions, such as Colombia, Chile, and Venezuela.

## Configure taxes

To configure taxes, follow these steps:

1. To create a negative tax code, go to **Tax** > **Indirect taxes** > **Sales Tax** > **Sales tax codes**.
1. Create a new tax code and set the **Allow negative sales tax percentage** slider to **Yes**.
1. Set a negative percentage (for example, -10%) in the **Values** field.
1. Assign appropriate ledger accounts in the **Ledger posting group** field.

Learn more in [Set up sales tax codes](../../general-ledger/tasks/set-up-sales-tax-codes.md).

## Set up sales tax groups

To set up sales tax groups, follow these steps:

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax groups**.
1. Create a sales tax group.
1. Add the negative taxes you want.
1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Item sales tax groups**.
1. Create a sales tax group.
1. Add the negative taxes you want.

## Assign the tax groups to a vendor

To assign the tax groups to a vendor, follow these steps:

1. Go to **Accounts payable** > **Vendors** > **All vendors**.
1. Select a vendor account to open the configuration form.
1. In the **Invoice and delivery** section, enter the tax group in the **Sales tax group** field.

> [!NOTE]
> In Chile, a professional fees receipt might require a 10% income tax withholding at invoice registration.

## Specific configuration for ISLR withholdings in Venezuela

To set up the sales tax code, follow these steps:

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax code**.
1. Create a new tax code with a negative percentage. As mentioned earlier, see [Configure taxes](#configure-taxes).
1. In the LATAM section, complete the following Venezuela-specific fields:
   - **% Tax Base**: Enter the percentage to apply to the original amount for withholding calculation.
   - **Subtracting**: Enter the fixed amount that the system subtracts from the calculated withholding tax amount.
   - **Number sequence code**: Select a previously created number sequence from the **Number sequences** menu. The system uses this sequence to automatically assign the corresponding withholding certificate number.

## Specific configuration for VAT withholdings in Venezuela

To set up the sales tax code, follow these steps:

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax code**.
1. Create a new tax code with a negative percentage. As mentioned earlier, see [Configure taxes](#configure-taxes).
1. In the Calculation section, under Calculation parameters, set the origin field as percentage of sales tax.
1. In the Latam section, complete the **Number sequence code** field. Select a previously created number sequence from the **Number sequences** menu. The system uses this sequence to automatically assign the corresponding withholding certificate number.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
