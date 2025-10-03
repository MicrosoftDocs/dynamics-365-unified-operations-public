---
title: Configure withholding taxes at invoice posting
description: Learn how to configure the withholding taxes to apply to vendor invoices.
author: Fhernandez0088
ms.date: 10/03/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure withholding taxes at invoice posting

This article describes how to configure withholdings tax that are applied when a vendor invoice is posted, using negative tax codes.
These types of withholdings are used by several LATAM Expansion reports on many countries (i.e. Colombia, Chile, Venezuela, etc.)

## Configure taxes

1. To create negative tax code go to **Tax > Indirect taxes > Sales Tax > Sales tax codes**
1. Create a new tax code and set the **Allow negative sales tax percentage** slider to **Yes**.
1. Set a negative percentage (e.g., -10%) in **Values**.
1. Assign appropriate ledger accounts in the **Ledger posting group**.

Learn more in [Set up sales tax codes](set-up-sales-tax-codes.md).

## Configure sales tax groups

1. Go to  ** Tax > Indirect taxes > Sales tax > Sales tax groups **.
1. Create a Sales tax group.
1. Add the negative taxes desired.
1. Go to  ** Tax > Indirect taxes > Sales tax > Item sales tax groups **.
1. Create a Sales tax group.
1. Add the negative taxes desired.

## Assign the tax groups to a vendor

1. Go to **Accounts payable > Vendors > All vendors**
1. Click on a vendor a account to enter the configuration form.
1. In the **Invoice and delivery** section assign the tax group in the **Sales tax group** field.

> [!NOTE]
> In Chile, a professional fees receipt may require a 10% income tax withholding at invoice registration.
