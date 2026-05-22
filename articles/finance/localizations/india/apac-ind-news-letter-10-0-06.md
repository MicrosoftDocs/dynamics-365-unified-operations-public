---
title: What's new or changed for  India GST in 10.0.06 (November 2019)
description: Learn about new or changed functionality for India GST features released in Dynamics 365 Finance version 10.0.06, including outlines on new features.
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
ms.dyn365.ops.version: 10.0.6
---

# What's new or changed for India GST in 10.0.06 (November 2019)

[!include [banner](../../includes/banner.md)]

This article summarizes the new features and critical bug fixes released in version 10.0.06 for India. For more information about the shipped features, see [What's new or changed in finance and operations version 10.0.6](../../../fin-ops-core/dev-itpro/get-started/whats-new-changed-10-0-6.md).

## New features

### Validate non-existent and duplicate records when importing tax setup

During the process of importing tax setup, the system validates the data correctness for master data like HSN and SAC,
as well as data duplication. Duplicate data means the lookup records result in the same tax rate, load on inventory percentage, and similar values.
Turn on this functionality in the **Feature management** workspace.

:::image type="content" source="../media/GST-tax-setup-validation-1-10-0-06.PNG" alt-text="Screenshot of Tax setup validation feature in Feature management.":::

### Tax information enabled for procurement category

Tax information is enabled for procurement categories. Add tax information on the **Tax information** FastTab on the **Procurement categories** page.

**Path : Procurement and Sourcing > Consignment > Procurement categories**

:::image type="content" source="../media/GST-tax-setup-validation-2-10-0-06.png" alt-text="Screenshot of Procurement categories page showing Tax information FastTab.":::

### Enable multi-batch processing for GSTR reports

1. Go to **Workspaces** > **Feature management**.
1. Turn on the **Multi-batch processing for GSTR reports** feature.
1. Go to **Tax** > **Sales tax reports** > **GER export to GSTR CSV** and generate a **GSTR** report.
1. Go to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**.
1. Select the comma-separated values (CSV) files that you want.
   For example, select **GER export** to **GSTR CSV__Merged**. This file is generated as a merged file.

 For more information, see [Enable multi-batch processing for GSTR reports](apac-ind-gst-multi-batch-processing-gstr-return.md).

## Critical fixes

- You can't view the transaction ID in posted tax document transactions and posted tax component transactions after you add a column.
- Accounting entry problems happen when you import purchase order invoicing, and the invoice is posted with reference to a product receipt's quantity.
- Invoicing for customers in the Indian legal entity takes a long time to process.
- Base amount isn't zero (0) for a sales order when the **Exempt** check box is selected.
- CGST and SGST are applicable for intra-state transfer orders if the GST registration number is different in two warehouses.
- TDS doesn't work for customers that have "TDS threshold" enabled.
- Reversal of the Invoice journal posted with TDS shows an incorrect total invoice amount.  
- Withholding Tax (TDS) threshold doesn't work correctly in typical TDS deduction scenarios.
- The TDS calculation in the open vendor invoice screen is incorrect.
- Incorrect calculation of GST for credit notes.

## Upcoming fixes in 10.0.7

- Printing multiple copies by using print management doesn't work for the **Sales invoice** report.  
- The imported customer free text invoice doesn't update for the India legal entity.  
- Data doesn't show in the **Tax Transaction inquiry for TDS** if the TDS settlement period character length is more than 10 characters.
- Transactions posted through the **Tax** journal don't show on the **Vendor open transaction for settlement** page.
- The system doesn't consider the threshold defined for withholding tax.
- Incorrect calculation of GST for a credit note.
- Incorrect TDS calculation on the **Open vendor invoice** page.  
- The **Business verticals** field for the GST registration number on the **Enterprise Tax Registration Numbers** page should be editable and not greyed out.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
