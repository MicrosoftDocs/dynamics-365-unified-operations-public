---
title: Create a tax settlement period
description: Learn how to create a tax settlement period, part of the master data setup required to make the India localization solution for Goods and Services Tax available.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Create a tax settlement period

[!include [banner](../../includes/banner.md)]

To make the India localization solution for Goods and Services Tax (GST) in Microsoft Dynamics 365 Finance available, you must complete the following master data setup:

- Define a business vertical.
- Update the state code and union territory.
- Create a Goods and Services Tax Identification Number (GSTIN) master.
- Define GSTINs for the legal entity, warehouse, vendor, or customer masters.
- Define Harmonized System of Nomenclature (HSN) codes and Service Accounting Codes (SACs).
- Create main accounts for the GST posting type.
- Create a tax settlement period.
- Attach the GSTIN to a tax registration group.

Follow these steps to create a tax settlement period.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**, and create a vendor GST authority.

    :::image type="content" source="../media/GST-authority.png" alt-text="Screenshot of the GST authority setup page.":::

1. Go to **Tax** \> **Indirect tax** \> **Sales tax** \> **Sales tax authorities**, create a tax authority, and assign the vendor account that you created in the previous step.

    :::image type="content" source="../media/tax-authority.png" alt-text="Screenshot of the tax authority setup page.":::

1. Go to **Tax** \> **Indirect tax** \> **Sales tax** \> **Sales tax settlement periods**, and create a tax period for GST.

    :::image type="content" source="../media/tax-settlement-period.png" alt-text="Screenshot of the tax settlement period setup page.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
