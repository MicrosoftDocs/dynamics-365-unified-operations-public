---
# required metadata

title: Set up bar code masks
description: This article describes how to set up bar code mask characters, bar code masks, and how to assign bar code masks to bar codes.
author: BrianShook
ms.date: 06/20/2017
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: RetailBarcodeMaskCharacter, RetailBarcodeMaskSetup
# ROBOTS:
audience: Application User, Developer, IT Pro
# ms.devlang:
ms.reviewer: josaw
# ms.tgt_pltfrm:
ms.custom: 265994
ms.assetid: 5831c74d-d2a1-4fa5-9a9a-a5aba8848381
ms.search.region: global
ms.search.industry: Retail
ms.author: brshoo
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Set up bar code masks

[!include [banner](includes/banner.md)]

This article describes how to set up bar code mask characters, bar code masks, and how to assign bar code masks to bar codes.

## Set up bar code mask characters

Bar code masks are used to create bar codes and to quickly identify bar codes that are scanned into the point of sale (POS). Masks are comprised of characters which act as placeholders that indicate the format for the bar codes that will be created. To configure a bar code mask, you need to set up bar code mask characters. Go to **Retail and Commerce** &gt; **Inventory management** &gt; **Barcodes and labels** &gt; **Mask characters**. Click **New** to create bar code mask characters. Mask characters can be created to indicate the following bar code data.

| Field            | Description |
|------------------|-------------|
| Product          | Placeholder for product ID. |
| Any number       | Used to specify a number that will be hard coded in bar codes. |
| Check digit      | Indicates that the bar code format in a bar code mask uses a check digit to confirm the validity of a bar code. |
| Size digit       | Indicates size in a bar code created for a product variant which includes size. |
| Color digit      | Indicates color in a bar code created for a product variant which includes color. |
| Style digit      | Indicates style in a bar code created for a product variant which includes a style. |
| EAN license code | Placeholder for EAN license issued for EAN license codes. |
| Price            | Indicates price for price embedded bar codes. |
| Quantity         | Indicates quantity in quantity/random weight embedded bar codes. |
| Employee         | Indicates bar code segment for employee ID number used for bar code POS login. |
| Customer         | Indicates customer ID segment. |
| Data entry       | *Not yet implemented.* |
| Discount code    | *Deprecated* as of Dynamics 365 for Retail Spring 2017 release. Previously: Indicates discount code for a bar code that's used to add a discount to a point of sale transaction. |
| Coupon code      | Indicates coupon code for a bar code used to add a discount to an order. This replaced discount code. |
| Gift card        | Indicates a gift card number when issuing or paying by gift card. |
| Loyalty card     | Adds a loyalty customer to the transaction, and can be used when paying by loyalty. |

## Define bar code masks

After bar code mask characters are specified for the necessary bar code masks, go to **Retail and Commerce** &gt; **Inventory management** &gt; **Barcodes and labels** &gt; **Barcode mask setup**. On this page, you can define bar code masks that use the previously specified characters. These bar code masks will be used when generating bar codes and will also help to identify bar codes scanned at the POS.

1. Click **New** to create a new bar code mask.
2. Enter values in the **Mask ID** and **Description** fields, and then select a bar code mask type in the **Type** field.
3. In the **General** section, select a value in the **Bar code standard** field, and then specify the bar code prefix, if one is required.
4. In the **Bar code mask segment** section, add bar code segments that will be used in the bar code to be created.

As an example, to create a bar code mask with mask ID 'Product', you'd do the following:

1. Create a new bar code mask and select type 'Product'.
2. Select a bar code standard, for example, 'Code 39'.
3. Provide a prefix to be used to easily identify the bar code. For example, '22'.
4. Add a mask segment. The 'Product' mask segment will be selected.
5. Provide a length for the product segment, for example, '10'. The length should match the length of a product ID commonly used in the store. The mask will be displayed as a preview in the **General** section under **Mask**.

> [!NOTE]
> If you are using number sequence to generate bar codes which has the bar code mask, since 10.0.32 the bar code prefix will only be inserted to the head after bar code is processed from the number sequence. As a result, you will need to make sure the length of number sequence's segments is less than or equal to the length of bar code mask's segments.
> Additionally, if you are using bar code types such as EAN13, EAN8, UPCA, UPCE which have a check digit, you will need to make sure the length of number sequence's segments is less than the length of bar code mask's segments.

## Assign bar code masks to bar codes

Bar codes masks must be assigned to bar codes before they can be used. Continuing with the previous example, to assign the bar code mask to a bar code, do the following:

1. Go to **Organization administration** &gt; **Setup** &gt; **Bar codes**. Click **New** to create a new bar code.
2. Enter values in the **Barcode** **setup** and **Setup** fields.
3. In the **General** section, in the **Bar code type** field, select 'Code 39'. In the **Mask** **ID** field, select the 'Product' mask previously created.
4. Under **Size**, enter '12'.
5. Click **Save**.

The bar code mask can now be used to create bar codes for products. The above steps are examples of how to create bar code masks for products, but they also illustrate how to create bar code masks for any of the other supported bar code types. Bar code masks, types, and lengths should be adjusted for use in your specific environment.


[!INCLUDE[footer-include](../includes/footer-banner.md)]