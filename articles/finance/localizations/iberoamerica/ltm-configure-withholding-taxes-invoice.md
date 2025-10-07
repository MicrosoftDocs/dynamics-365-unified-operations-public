---
title: Configure withholding taxes at invoice posting
description: Learn how to configure the withholding taxes to apply to vendor invoices.
author: Fhernandez0088
ms.date: 10/07/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure withholding taxes at invoice posting

This article describes how to configure withholding taxes that apply when you post a vendor invoice, using negative tax codes.
Several LATAM Expansion reports use these types of withholding taxes for many countries/regions, such as Colombia, Chile, and Venezuela.

## Configure taxes

1. To create a negative tax code, go to **Tax > Indirect taxes > Sales Tax > Sales tax codes**.
1. Create a new tax code and set the **Allow negative sales tax percentage** slider to **Yes**.
1. Set a negative percentage (for example, -10%) in **Values**.
1. Assign appropriate ledger accounts in the **Ledger posting group**.

Learn more in [Set up sales tax codes](set-up-sales-tax-codes.md).

## Set up sales tax groups

1. Go to **Tax > Indirect taxes > Sales tax > Sales tax groups**.
1. Create a Sales tax group.
1. Add the negative taxes you want.
1. Go to **Tax > Indirect taxes > Sales tax > Item sales tax groups**.
1. Create a Sales tax group.
1. Add the negative taxes you want.

## Assign the tax groups to a vendor

1. Go to **Accounts payable > Vendors > All vendors**.
1. Select a vendor account to open the configuration form.
1. In the **Invoice and delivery** section, enter the tax group in the **Sales tax group** field.

> [!NOTE]
> In Chile, a professional fees receipt might require a 10% income tax withholding at invoice registration.
