---
title: What's new or changed for India GST in 10.0.04 (July 2019)
description: Learn about new or changed functionality for India GST features released in Dynamics 365 Finance version 10.0.04, including outlines on new features.
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
ms.dyn365.ops.version: 10.0.04
---

# What's new or changed for India GST in 10.0.04 (July 2019)

[!include [banner](../../includes/banner.md)]

This article summarizes the new features and critical bug fixes released in Dynamics 365 Finance version 10.0.04 for India GST localization.
.

## New features

### Define GST reference number sequence group

You can define a separate GST reference number sequence group for free text invoice, stock transfer receipt, and stock transfer shipment.

 :::image type="content" source="../media/GST-reference-number-sequence-group-1-10-0-04.PNG" alt-text="Screenshot of GST reference number sequence groups configuration.":::

### Financial dimension linked to the inventory dimension site

Financial dimensions that are linked to the inventory dimension site will be automatically populated on the order line of the stock transfer receipt.

## Critical fixes

- Total transaction value in GSTR2 is incorrect for multi-line invoice journals with both debit and credit ledger lines.
- Performing Settle and post sales tax does not reach the vendor account.
- Tax is not calculated in return orders.
- The GST registration ID is not updated after the delivery address is changed in a purchase order.
- Adjustment of project transactions is not working correctly.
- Financial dimensions are not updated for the GST ledger after project invoices are posted.
- Proforma invoices consume a number from the invoice number sequence.

## Upcoming fixes in 10.0.5

- TDS isn't deducted correctly when an invoice is settled with prepayment.
- Calculated GST isn't posting to the expense account when the Service Accounting Codes (SAC) is selected with ITC category is **Others**.
- Charge allocation on the sales lines isn't in proportion to the GST regulation change.
- Tax document isn't saved in the purchase order confirmation so that the tax document can be opened after the purchase order is posted.
- IGST isn't calculating on a Special Economic Zone (SEZ) purchase.
- In a partial invoice against the purchase receipt quantity, the assessable value isn't updated and the GST isn't calculated.
- The load on inventory amount isn't posting to the fixed asset account when a fixed asset is acquired through a purchase order.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
