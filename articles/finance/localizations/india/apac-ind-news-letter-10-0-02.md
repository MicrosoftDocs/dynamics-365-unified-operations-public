---
title: What's new or changed for India GST in 10.0.02 (May 2019)
description: Learn about new or changed functionality for India GST features released in Dynamics 365 Finance version 10.0.02, including outlines on new features.
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
---

# What's new or changed for India GST in 10.0.02 (May 2019)

[!include [banner](../../includes/banner.md)]

This article summarizes the new features and critical bug fixes released in Dynamics 365 Finance version 10.0.02 for India GST localization.

## New features

### Auto completion when editing tax formulas or conditions

Advanced editor is enabled for Global Tax Engine formulas and conditions to improve user productivity. To enable this functionality, go to **Electronic Reporting** > **Tax Configuration** > **Configurations** > **User Parameter** and set the **Enable advanced formula editor** field to **Yes**.

 :::image type="content" source="../media/GST-advance-editor-1-10-0-02.png" alt-text="Screenshot of Advanced formula editor configuration.":::

## Critical fixes

- Fixed exchange rate in sales order header used for invoice posting but not used for the **GSTR 1** report.
- Invoice date and GST tax document date are different when posting the credit note invoice.
- An incorrect financial dimension posted for GST in the stock transfer receipt.
- Unable to post free text invoices with GST information when signed in by using the **Accounts Receivable clerk** role.
- **TDS/TCS group** field is editable only for the first line on the **Pending invoice** page.  
- The tax rate isn't the same for bill of entry (BOE) and purchase invoice if the date isn't the same.
- GST doesn't calculate correctly when the **Unit price** and **Discount %/Discount amount** fields are updated at the
  purchase invoice level.
- The **UQC** field from the HSN file in the **GSTR** report doesn't show the full value because the length is ten characters.
- The **Production order** page stops responding when selecting a production order.
- The tax adjustment value isn't posted when the voucher number allocation on the posting parameter is enabled.
- GST isn't updated in tax documents when consolidated invoices with miscellaneous charges that have GST are generated and posted
  by consolidation of two or more product receipts or purchase orders.  
- The **Tax journal** doesn't update the correct tax component and amount.  
- **State place of supply** is incorrect for the **GSTR 2** report.
- IGST credit posted through a tax journal shows as recoverable on the **Tax settlement** page.
- Unable to view tax information for a timesheet in the India legal entity.
- The assessable value doesn't update on the **Project milestone** (Billing rule) page.
- The financial dimension isn't pushed to the **Site in stock transfer** page.
- Duplicate tax transactions are posted for the tax journal when the tax rate and the tax amount are equal to zero (0).
- After synchronizing a new configuration, GST tax codes with a name such as CGST1, are populated.
- While selecting tax information, it's not possible to see the **GSTIN** table in time sheets.
- The **Tax document** page fails to open from the **Stock transfer order** page.
- The **Tax** column has no value in the **Invoice journal** report in the **Accounts payable** module.

## Upcoming fixes in 10.0.3

- The subtotal amount value is incorrect on the **Adjustment** page for settle and post sales tax.
- The adjusted withholding tax origin amount doesn't appear on the **Posted withholding tax inquiry** page.
- **Project adjust transactions** doesn't work properly.
- The invoice amount appears incorrectly in the **Invoice journal** report.
- The **Tax** column doesn't update with tax value in the **Invoice journal** report.
- The delivery address doesn't autoflow on the **Tax information** page for the sales order lines.
- Tax information isn't editable on the **Sales order after delivery** page.
- The invoice number doesn't show in **Posted withholding tax inquiry**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
