---
# required metadata

title: Set up barcode masks
description: This article describes how to set up barcode mask characters and barcode masks, and how to assign barcode masks to barcodes in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 07/18/2023
ms.topic: article
ms.search.form: RetailBarcodeMaskCharacter, RetailBarcodeMaskSetup
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.custom: 265994
ms.assetid: 5831c74d-d2a1-4fa5-9a9a-a5aba8848381
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2016-02-28


---

# Set up barcode masks

[!include [banner](includes/banner.md)]

This article describes how to set up barcode mask characters and barcode masks, and how to assign barcode masks to barcodes in Microsoft Dynamics 365 Commerce.

## Set up barcode mask characters

Barcode masks are used to create barcodes and to quickly identify barcodes that are scanned into the point of sale (POS). Masks are comprised of characters which act as placeholders that indicate the format for the barcodes that will be created. To configure a barcode mask, you must set up barcode mask characters in Commerce headquarters. Go to **Retail and Commerce \> Inventory management \> Barcodes and labels \> Mask characters**, and then select **New** to create barcode mask characters. Mask characters can be created to indicate the following barcode data.

| Field            | Description |
|------------------|-------------|
| Product          | Placeholder for product ID. |
| Any number       | Used to specify a number that will be hard coded in barcodes. |
| Check digit      | Indicates that the barcode format in a barcode mask uses a check digit to confirm the validity of a barcode. |
| Size digit       | Indicates size in a barcode created for a product variant which includes size. |
| Color digit      | Indicates color in a barcode created for a product variant which includes color. |
| Style digit      | Indicates style in a barcode created for a product variant which includes a style. |
| EAN license code | Placeholder for EAN license issued for EAN license codes. |
| Price            | Indicates price for price embedded barcodes. |
| Quantity         | Indicates quantity in quantity/random weight embedded barcodes. |
| Employee         | Indicates barcode segment for employee ID number used for barcode POS login. |
| Customer         | Indicates customer ID segment. |
| Data entry       | *Not yet implemented.* |
| Discount code    | *Deprecated* as of Dynamics 365 for Retail Spring 2017 release. Previously: Indicates discount code for a barcode that's used to add a discount to a point of sale transaction. |
| Coupon code      | Indicates coupon code for a barcode used to add a discount to an order. This replaced discount code. |
| Gift card        | Indicates a gift card number when issuing or paying by gift card. |
| Loyalty card     | Adds a loyalty customer to the transaction, and can be used when paying by loyalty. |

## Define barcode masks

After barcode mask characters are specified for the necessary barcode masks, go to **Retail and Commerce** &gt; **Inventory management** &gt; **Barcodes and labels** &gt; **Barcode mask setup**. On this page, you can define barcode masks that use the previously specified characters. These barcode masks will be used when generating barcodes and will also help to identify barcodes scanned at the POS.

1. Select **New** to create a new barcode mask.
2. Enter values in the **Mask ID** and **Description** fields, and then select a barcode mask type in the **Type** field.
3. In the **General** section, select a value in the **Barcode standard** field, and then specify the barcode prefix, if one is required.
4. In the **Barcode mask segment** section, add barcode segments that will be used in the barcode to be created.

For example, to create a barcode mask with mask ID "Product", you'd do the following:

1. Create a new barcode mask and select type **Product**.
2. Select a barcode standard (for example, **Code 39**).
3. Provide a prefix to be used to easily identify the barcode (for example, "22").
4. Add a mask segment. The **Product** mask segment will be selected.
5. Provide a length for the product segment (for example, "10"). The length should match the length of a product ID commonly used in the store. The mask will be displayed as a preview in the **General** section under **Mask**.

> [!NOTE]
> - If you are using a number sequence to generate barcodes which have the barcode mask, starting with Commerce version 10.0.32 a barcode prefix is only inserted into the head after the barcode is processed from the number sequence. As a result, you must ensure that the length of the number sequence's segments is less than or equal to the length of barcode mask's segments.
> - If you are using barcode types that have a check digit (for example, "EAN13", "EAN8", "UPCA", and "UPCE"), you must ensure that the length of the number sequence's segments is less than the length of barcode mask's segments.

## Assign barcode masks to barcodes

Barcodes masks must be assigned to barcodes before they can be used. Continuing with the previous example, to assign the barcode mask to a barcode, do the following:

1. Go to **Organization administration \> Setup \> Barcodes**, and then select **New** to create a new barcode.
2. Enter values in the **Barcode** **setup** and **Setup** fields.
3. In the **General** section, in the **Barcode type** field, select **Code 39**. In the **Mask ID** field, select the product mask created previously.
4. Under **Size**, enter "12".
5. Select **Save**.

The barcode mask can now be used to create barcodes for products. The above steps are examples of how to create barcode masks for products, but they also illustrate how to create barcode masks for any of the other supported barcode types. Barcode masks, types, and lengths should be adjusted for use in your specific environment.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
