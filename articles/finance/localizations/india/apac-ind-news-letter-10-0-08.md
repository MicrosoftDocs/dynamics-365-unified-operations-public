---
title: What's new or changed for India GST in 10.0.08 (February 2020)
description: Learn about new or changed functionality for India GST features released in Dynamics 365 Finance version 10.0.08, including outlines on new features.
author: prabhatb
ms.author: johnmichalak
ms.topic: whats-new
ms.custom:
  - bap-template
  - evergreen
ms.date: 01/21/2026
ms.update-cycle: 1095-days
ms.reviewer: johnmichalak
ms.search.region: India
ms.dyn365.ops.version: 10.0.8
---

# What's new or changed for India GST in 10.0.08 (February 2020)

[!include [banner](../../includes/banner.md)]

This article summarizes the new features and critical bug fixes released in Dynamics 365 Finance version 10.0.08 for India GST localization.

## New features

### Change the tax rate type on a purchase invoice

In India, the invoice received from the supplier can have different tax rates from the purchase order. The tax rate type functionality supports this difference.

You can enable the feature in the **Feature management** workspace. The name of the feature is **(India) Enable changing tax rate type in purchase invoice**.

:::image type="content" source="../media/GST-changing-tax-rate-type-1-10-0-08.png" alt-text="Screenshot of Feature management showing India Enable changing tax rate type in purchase invoice.":::

When you enable the feature, you can update the tax rate type in the tax information for a purchase invoice. You can apply a different tax rate if needed.

:::image type="content" source="../media/GST-tax-rate-type-tax-information-2-10-0-08.png" alt-text="Screenshot of Tax rate type information.":::

### Data consistency check

You can verify and fix a data inconsistency issue regarding GTE. To do this, go to **System administration** > **Periodic tasks** > **Database** > **Consistency check**. Run this consistency check in your environment.

:::image type="content" source="../media/GST-tax-rate-type-tax-information-3-10-0-08.PNG" alt-text="Screenshot of Consistency check dialog page.":::

### GST number sequence issue

A posting failure can occur due to missing or incorrect setup of the GST number sequence. To resolve the issue and set up the GST number sequence correctly, complete the procedures in the [Define GSTINs and reference number sequences](apac-ind-GST-define-gstin-numbers-number-sequences.md) and [Set up GST reference number groups](apac-ind-gst-reference-groups.md) topics.

## Critical fixes

- After you define the tax information on a purchase order, the tax account lines on the **View distribution** page aren't visible.
- TDS transaction isn't updated in **Withholding tax transaction** reports when the invoice is settled with prepayment.
- Tax amount showing in purchase order totals and purchase invoice totals is posted with 100 percent reverse charges.
- Assessable value is updated after the charge code is removed from the purchase order invoice line.
- When you change the selected vendor on a purchase requisition, vendor tax information isn't updated on the **Tax information** page.
- Incorrect Free on board (FOB) and Cost, insurance, and freight (CIF) calculation on exported sales orders.
- Assessable value isn't updated correctly on the **Vendor invoice** page when posted changes are incorporated in the Excel import file and published into Dynamics 365 Finance.

## Upcoming fixes in 10.0.9

- Free text invoice print isn't working for non-GST invoices.
- Tax isn't calculated when data is imported through the data entity file.
- When an Indian company generates a free text invoice, an error occurs.
- The system generates a sales order invoice instead of a  GST tax invoice when the tax value becomes zero (0).
- The value in the GSTR-2 column, **Is Reverse charge applicable** is updating incorrectly.
- The **Tax code** lookup filter option is unavailable in the tax configuration.
- The GTE set off hierarchy version isn't the latest version.
- There's an issue with the journal voucher description transaction for GST transactions.
- Per government notification, there's a change in the hierarchy of the tax settlement components.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
