---
title: Define HSN codes and Service Accounting Codes
description: Learn how to define Harmonized System of Nomenclature (HSN) codes and Service Accounting Codes (SACs), including a process for defining HSN codes.
author: EricWangChen
ms.author: wangchen
ms.topic: how-to
ms.date: 04/30/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak  
audience: Application User
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.search.form:
ms.dyn365.ops.version: 10.0.4
---

# Define HSN codes and Service Accounting Codes

[!include [banner](../../includes/banner.md)]

To make the India localization solution for Goods and Services Tax (GST) in Microsoft Dynamics 365 Finance available, complete the following master data setup steps:

- Define a business vertical.
- Update the state code and union territory.
- Create a Goods and Services Tax Identification Number (GSTIN) master.
- Define GSTINs for the legal entity, warehouse, vendor, or customer masters.
- Define Harmonized System of Nomenclature (HSN) codes and Service Accounting Codes (SACs).
- Create main accounts for the GST posting type.
- Create a tax settlement period.
- Attach the GSTIN to a tax registration group.

## Define HSN codes

1. Go to **Tax** > **Setup** > **Sales tax** > **India** > **HSN code**.
1. Create a record.
1. In the **Chapter** field, enter a value.
1. In the **Heading** field, enter a value.
1. In the **Subheading** field, enter a value.
1. In the **Country/region extension** field, enter a value.
1. In the **Statistical suffix** field, enter a value.
1. Save the record, and verify that the **HSN code** field is updated.
1. In the **Description** field, enter a value.
1. Select **Close**.

## Define SACs

1. Go to **Tax** > **Setup** > **Sales tax** > **India** > **Service accounting codes**.
1. Create a record.
1. In the **SAC** field, enter a value.
1. In the **Description** field, enter a value.
1. Save the record, and then select **Close**.

## Assign HSN codes and SACs to products

1. Go to **Product information management** > **Products** > **Released products**.
1. Select a product, and then select **Edit**.
1. On the **General** FastTab, if the product type is **Item**, select a value in the **HSN codes** field. If the product type is **Service**, select a value in the **Service accounting codes** field.
1. Save the record, and then select **Close**.

For the calculation of GST, you need to complete the following setup:

- Define an HSN code for the **Item** product type, or define an SAC for the **Service** product type.
- Remove the item sales tax group.

:::image type="content" source="../media/Assign-codes-to-product_upd.png" alt-text="Screenshot of assigning HSN codes and SACs to products.":::

## Assign SACs to miscellaneous charges

1. Go to **Accounts payable** > **Charges setup** > **Charges code**.
1. Select a charges code.
1. On the **Tax information** FastTab, in the **Service accounting codes** or **HSN codes** field, enter a value.
1. In the **Service category** or **ITC Category** field, enter a value.
1. Set the **Exempt** option to **Yes** to exempt these charges from the calculation of GST.
1. Save the record.

    When you select this charge code for a transaction, the system automatically enters the defined tax information and calculates GST accordingly.

1. Go to **Accounts receivable** > **Charges setup** > **Charges code**.
1. Select a charges code.
1. On the **Tax information** FastTab, in the **Service accounting codes** or **HSN codes** field, enter a value.
1. Set the **Exempt** option to **Yes** to exempt these charges from the calculation of GST.
1. Save the record.

    When you select this charge code for a transaction, the system automatically enters the defined tax information and calculates GST accordingly.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
