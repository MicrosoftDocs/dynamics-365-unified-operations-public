---
title: What's new or changed for India GST in 10.0.07 (January 2020)
description: Learn about new or changed functionality for India GST features released in Dynamics 365 Finance version 10.0.07, including outlines on new features.
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

# What's new or changed for India GST in 10.0.07 (January 2020)

[!include [banner](../../includes/banner.md)]

This article summarizes the new features and critical bug fixes released in Dynamics 365 Finance version 10.0.07 for India GST localization.

## New features

### Create tax component with pre-defined rules

You can create a new component with pre-defined rules that support GST behaviors including non-deductible and
reverse charge for purchases and sales. With this feature, you do not need to create a tax component, which includes adding tax measures, configuring the tax calculation formula, and configuring a tax posting profile.

You can enable the feature in **Feature management** workspace. The feature name is **Enable creating tax component with pre-defined rules**.

:::image type="content" source="../media/GST-tax-component-pre-defined-rule-1-10-0-07.png" alt-text="Screenshot of Feature management showing Enable creating tax component with pre-defined rules.":::

 With the feature enabled, there are several controls enabled in the dialog box. You can use them to control the behavior
 of the tax component. For more information, see [Create tax components](tax-engine-create-tax-component.md).

:::image type="content" source="../media/GST-Tax-component-pre-defined-2-10-0-07.PNG" alt-text="Screenshot of Tax component pane.":::

## Critical fixes

- Printing multiple copies of the **Sales invoice report** by using print management doesn't work.
- Invoice address doesn't automatically populate in the customer tax information included in the timesheet.
- Importing customer data to a free text invoice doesn't update for the Indian legal entity.
- Transactions posted through the **Tax journal** don't show in open vendor transactions for settlement.
- Sales tax settlement might have an update conflict when the **TaxsalesTaxpaymentHistory** detail is updated multiple times.
- Incorrect Withholding tax (TDS/TCS) posting in the reporting currency when the exchange rate is changed at the time of payment
  with the transaction settled for foreign vendor transactions.
- Incorrect calculation of GST for credit note.
- Lines that are imported by using the **VendorInvoiceLine** entity aren't visible on the **Pending vendor invoice** page in the India entity.
- The **Business verticals** field on the **GST registration numbers** page isn't always editable.

## Upcoming fixes in 10.0.8

- Tax amount showing in purchase order totals and purchase invoice total is posted with 100 percent reverse charges.
- TDS transactions aren't updated in the **Withholding tax transaction (TDS/TCS)** report when settled in the **Prepayment with invoice** report.
- Assessable value is updated after the charge code is removed from the Purchase order invoice line.
- When you change the selected vendor on a purchase requisition, vendor tax information isn't updated on the **Tax information** page.
- Incorrect Free on board (FOB) and Cost, insurance, and freight (CIF) calculation on exported sales orders.
- Assessable value isn't updated correctly on the **Vendor invoice** page when posted changes are incorporated in the **Excel import** file and published to Dynamics 365 Finance.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
