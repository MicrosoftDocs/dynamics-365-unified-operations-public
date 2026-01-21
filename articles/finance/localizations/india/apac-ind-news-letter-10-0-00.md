---
title: What's new or changed for India GST in 10.0.0 (April 2019)
description: Learn about new or changed functionality for India GST features released in Dynamics 365 Finance version 10.0.0, with an overview on new configurations.
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
ms.dyn365.ops.version: 10.0.0
---

# What's new or changed for India GST in 10.0.0 (April 2019)

[!include [banner](../../includes/banner.md)]

This article summarizes the new features and critical bug fixes released in Dynamics 365 Finance version 10.0.0 for India GST localization.

## New configuration

The Shared Asset Library in Lifecycle Services provides the following configurations for use in version 10.0.0:

- Taxable Document version.81.xml
- Taxable Document (India) version.81.138.xml
- Tax (India GST) version.81.138.246.xml

You can differentiate customer GST registration numbers from vendor GST registration numbers in tax setup.

:::image type="content" source="../media/GST-registration-rate-setup-1-10-0-00.png" alt-text="Screenshot of Registration number type drop-down list.":::

You can determine the tax rate based on invoice date for the purchase transactions, such as a purchase invoice.

:::image type="content" source="../media/GST-invoice-date-rate-setup-2-10-0-00.PNG" alt-text="Screenshot of Tax rate based on invoice date.":::

You can create a non-GST transaction, which the Goods and Services Tax return (GSTR) reflects.

:::image type="content" source="../media/GST-non-gst-transaction-3-10-0-00.png" alt-text="Screenshot of Tax information pane with Non-GST toggle.":::

## Import and export tax setup

You can import and export tax setup for **Rate**, **Reverse charge percentage**, and **Load on inventory percentage**.

:::image type="content" source="../media/GST-import-export-tax-setup-4-10-0-00.png" alt-text="Screenshot of Import/export tax setup.":::

## GTE designer enhancement

You can select multiple lookup columns and search available columns.

:::image type="content" source="../media/GST-gte-multi-select-5-10-0-00.png" alt-text="Screenshot of Available columns in GTE designer.":::

## Critical fixes

- You can't synchronize extended configurations if you change the data model in your extended tax document.
- Exclude the transactions without GST from GSTR. If there's no GST applicable for the transaction, the transaction isn't included in the GSTR,
  unless  it's exempt or non-GST.
- Block the posting with GST if there isn't a GST transaction ID.

## Upcoming fixes in 10.0.1

- Total item discount amount isn't showing in GSTR.
- Item unit of measurement should show the unit and a description.
- Total transaction value in GSTR isn't equal to the invoice amount for a transaction with the price including tax.
- No customer billing name for stock transfer in GSTR.
- No default logic for original GST transaction ID for a credit note.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
