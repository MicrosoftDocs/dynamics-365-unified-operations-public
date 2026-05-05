---
title: Define GSTINs and reference number sequences
description: Learn how to define Goods and Services Tax Identification Numbers and reference number sequences for legal entity, warehouse, vendor, and customer masters.
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

# Define GSTINs and reference number sequences

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

## Define GSTINs and number sequences for legal entities

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
1. On the **Addresses** FastTab, select **More options** > **Advanced**.
1. On the **Tax information** FastTab, select **Add**.
1. In the **Name or description** field, enter a value.
1. On the **GST** FastTab, in the **GSTIN/GDI/UID** field, select a value.
1. In the **Reference number sequence group** field, select a value.
1. Set the **Primary** option to **Yes**, and then select **Yes** to acknowledge the message that you receive.
1. Save the record, and then select **Close**.
1. Repeat steps 3 through 8 for all the other required addresses for the legal entity.

## Define GSTINs and number sequences for warehouses

1. Go to **Inventory management** > **Setup** > **Inventory breakdown** > **Warehouses**.
1. On the **Addresses** FastTab, select **Advanced**.
1. On the **Tax information** FastTab, select **Add**.
1. In the **Name or description** field, enter a value.
1. On the **GST** FastTab, in the **GSTIN/GDI/UID** field, select a value.
1. Set the **Primary** option to **Yes**, and then select **Yes** to acknowledge the message that you receive.
1. Save the record, and then select **Close**.


## Define GSTINs for vendors

1. Go to **Accounts payable** > **Vendors** > **All vendors**.
1. On the **Addresses** FastTab, select **More options** > **Advanced**.
1. On the **Tax information** FastTab, select **Add**.
1. In the **Name or description** field, enter a value.
1. On the **GST** FastTab, in the **GSTIN/GDI/UID** field, select a value.
1. Set the **Primary** option to **Yes**, and then select **Yes** to acknowledge the message that you receive.
1. Save the record, and then select **Close**.
1. On the **Tax information** FastTab, set the **GST composition scheme** option to **Yes** if a composition scheme is used to purchase from the dealer.

    :::image type="content" source="../media/Composite-Dealer_upd.png" alt-text="Screenshot of the composite dealer tax information settings.":::

## Define GSTINs for customers

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. On the **Addresses** FastTab, select **More options** > **Advanced**.
1. On the **Tax information** FastTab, select **Add**.
1. In the **Name or description** field, enter a value.
1. On the **GST** FastTab, in the **GSTIN/GDI/UID** field, select a value.
1. Set the **Primary** option to **Yes**, and then select **Yes** to acknowledge the message that you receive.
1. Save the record, and then select **Close**.
1. On the **Tax information** FastTab, set the **Consumer** option to **Yes** to identify the customer as a consumer.
1. For customer sales through an e-Commerce operator, enter a value in the **Merchant ID** field, and select a value in the **Default E-Commerce operator** field.
1. For sales with government companies or other agencies, in the **Customer type** field, select **Govt company or other agencies**.

    :::image type="content" source="../media/E-commerce-operator_upd.png" alt-text="Screenshot of the Tax information FastTab with e-Commerce operator settings.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
