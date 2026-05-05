---
title: Create a GSTIN master
description: Learn how to create a Goods and Services Tax Identification Number (GSTIN) master, part of the master data setup required to make an India localization solution.
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

# Create a GSTIN master

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

## Define company registration numbers for the GST tax type

1. Go to **Tax** > **Setup** > **Sales Tax** > **Enterprise tax registration numbers**.
1. Create a record.
1. In the **Tax type** field, select **GST**.
1. In the **Registration number type** field, select **Company** to create state-wide company registration numbers.
1. In the **Type** field, verify that **GSTIN**, **GDI**, and **UID** appear in the list, and then select a value.
1. In the **Registration number** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Business vertical** field, select a value.

    :::image type="content" source="../media/IND-GST-GSTIN-1.png" alt-text="Screenshot of the new company registration number form.":::

1. On the **Casual registration** FastTab, select **Add**.
1. In the **From date** and **To date** fields, define the valid period for the casual registration number.
1. In the **Description** field, enter a value.
1. On the **Number sequences** FastTab, define number sequences for the **GST invoice** and **Bill of supply** references.

    - The **GST invoice** number sequence is used when customer sales that have GST transactions are posted.
    - The **Bill of supply** number sequence is used when customer sales that have non-GST transactions are posted.

:::image type="content" source="../media/IND-GST-GSTIN-2.png" alt-text="Screenshot of the company registration numbers page.":::

## Define vendor registration numbers for the GST tax type

1. In the **Registration number type** field, select **Vendors** to create state-wide vendor registration numbers.
1. Select **New** to create a record.
1. In the **Tax type** field, select **GST**.
1. In the **Registration number field**, enter a value.
1. In the **Description** field, enter a value.
1. In the **Business vertical** field, select a value.

:::image type="content" source="../media/IND-GST-GSTIN-3.png" alt-text="Screenshot of the vendor registration numbers page.":::

## Define customer registration numbers for the GST tax type

1. In the **Registration number type** field, select **Customers** to create state-wide customer registration numbers.
1. Select **New** to create a record.
1. In the **Tax type** field, select **GST**.
1. In the **Registration number field**, enter a value.
1. In the **Description** field, enter a value.
1. In the **Business vertical** field, select a value.

:::image type="content" source="../media/IND-GST-GSTIN-4.png" alt-text="Screenshot of the customer registration numbers page.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
