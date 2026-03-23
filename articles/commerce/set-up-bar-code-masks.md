---
title: Set up barcode masks
description: Learn how to set up barcode mask characters and barcode masks, and how to assign barcode masks to barcodes in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 01/29/2026
ms.topic: how-to
ms.search.form: RetailBarcodeMaskCharacter, RetailBarcodeMaskSetup
ms.reviewer: v-griffinc
ms.assetid: 5831c74d-d2a1-4fa5-9a9a-a5aba8848381
ms.search.region: Global
ms.author: ritakimani
ms.search.validFrom: 2016-02-28
ms.custom: 
  - bap-template
---

# Set up barcode masks

[!include [banner](includes/banner.md)]

This article describes how to set up barcode mask characters and barcode masks, and how to assign barcode masks to barcodes in Microsoft Dynamics 365 Commerce.

## Set up barcode mask characters

Use barcode masks to create barcodes and to quickly identify barcodes that you scan into the point of sale (POS). Masks are made up of characters that act as placeholders and show the format for the barcodes that you create. To configure a barcode mask, set up barcode mask characters in Commerce headquarters. Go to **Retail and Commerce > Inventory management > Barcodes and labels > Mask characters**, and then select **New** to create barcode mask characters. Create mask characters to indicate the following barcode data.

| Field            | Description |
|------------------|-------------|
| Product          | Placeholder for product ID. |
| Any number       | Used to specify a number that appears in barcodes. |
| Check digit      | Indicates that the barcode format in a barcode mask uses a check digit to confirm the validity of a barcode. |
| Size digit       | Indicates size in a barcode created for a product variant that includes size. |
| Color digit      | Indicates color in a barcode created for a product variant that includes color. |
| Style digit      | Indicates style in a barcode created for a product variant that includes a style. |
| EAN license code | Placeholder for EAN license issued for EAN license codes. |
| Price            | Indicates price for price embedded barcodes. |
| Quantity         | Indicates quantity in quantity/random weight embedded barcodes. |
| Employee         | Indicates barcode segment for employee ID number used for barcode POS authentication. |
| Customer         | Indicates customer ID segment. |
| Data entry       | *Not yet implemented.* |
| Discount code    | *Deprecated* as of Dynamics 365 for Retail Spring 2017 release. Previously: Indicates discount code for a barcode that's used to add a discount to a point of sale transaction. |
| Coupon code      | Indicates coupon code for a barcode used to add a discount to an order. This replaced discount code. |
| Gift card        | Indicates a gift card number when issuing or paying by gift card. |
| Loyalty card     | Adds a loyalty customer to the transaction, and can be used when paying by loyalty. |

## Define barcode masks

After you specify barcode mask characters for the necessary barcode masks, go to **Retail and Commerce > Inventory management > Barcodes and labels > Barcode mask setup**. On this page, you can define barcode masks that use the characters you specified. Use these barcode masks when you generate barcodes. They also help identify barcodes scanned at the POS.

1. Select **New** to create a new barcode mask.
1. Enter values in the **Mask ID** and **Description** fields, and then select a barcode mask type in the **Type** field.
1. In the **General** section, select a value in the **Barcode standard** field, and then specify the barcode prefix, if one is required.
1. In the **Barcode mask segment** section, add barcode segments that you want to use in the barcode.

For example, to create a barcode mask with mask ID "Product," follow these steps:

1. Create a new barcode mask and select type **Product**.
1. Select a barcode standard, such as **Code 39**.
1. Provide a prefix to easily identify the barcode, such as "22."
1. Add a mask segment. The **Product** mask segment is selected.
1. Provide a length for the product segment, such as "10." The length should match the length of a product ID commonly used in the store. The mask is displayed as a preview in the **General** section under **Mask**.

> [!NOTE]
> - If you use a number sequence to generate barcodes that have the barcode mask, starting with Commerce version 10.0.32, the system inserts a barcode prefix only after the number sequence processes the barcode. As a result, you must ensure that the length of the number sequence's segments is less than or equal to the length of barcode mask's segments.
> - If you use barcode types that have a check digit (for example, "EAN13," "EAN8," "UPCA," and "UPCE"), you must ensure that the length of the number sequence's segments is less than the length of barcode mask's segments.

## Assign barcode masks to barcodes

Assign barcode masks to barcodes before using them. In the previous example, follow these steps to assign the barcode mask to a barcode:

1. Go to **Organization administration > Setup > Barcodes**, and then select **New** to create a new barcode.
1. Enter values in the **Barcode** **setup** and **Setup** fields.
1. In the **General** section, in the **Barcode type** field, select **Code 39**. In the **Mask ID** field, select the product mask you created earlier.
1. Under **Size**, enter "12".
1. Select **Save**.

You can now use the barcode mask to create barcodes for products. These steps are examples of how to create barcode masks for products, but they also illustrate how to create barcode masks for any of the other supported barcode types. Adjust barcode masks, types, and lengths for your specific environment.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
