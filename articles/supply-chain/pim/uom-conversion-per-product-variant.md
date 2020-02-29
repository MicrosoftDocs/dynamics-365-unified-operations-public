---
# required metadata

title: Unit of measure conversion per product variant
description: This topic explains how unit of measure conversions can be set up on product variants.
author: johanhoffmann
manager: AnnBe
ms.date: 01/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: UnitOfMeasureConversion
ROBOTS: noindex, nofollow
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2019-04-01
ms.dyn365.ops.version: 10.0

---

# Unit of measure conversion per product variant

[!include [banner](../includes/banner.md)]

This topic explains how unit of measure conversions can be set up on product variants. It includes an example of the setup.

This feature makes it possible for companies to define different unit conversion between the variants of the same product. The following example is used in this topic. A company sells T-shirts in sizes Small, Medium, Large, and Extra-Large. The T-shirt is defined as a product, and the different sizes are defined as variants of the product. The T-shirts are packed in boxes and there can be five T-shirts in a box, except for the Extra-Large size where there is only space for four T-shirts. The company wants to track the different variants of the T-shirts in the unit **Pieces** but is selling the T-shirts in the unit **Boxes**. The conversion between the inventory unit and the sales unit is 1 Box = 5 Pieces, except for the variant Extra-Large, where the conversion is 1 Box = 4 Pieces.

### Set up a product for unit conversion per variant

Product variants can only be created for products of **Product subtype**: **Product master**. For more information, see [Create a product master](tasks/create-product-master.md).

The feature is not enabled for products that are set up for Catch Weight processes. 

When the product master with released products variants is created, unit conversions per variants can be set up. You can find the menu item for opening the unit conversion page in context of a product or a product variant on the following pages.

-   **Product details** page
-   **Released products details** page
-   **Released product variants** page

When you open the **Unit conversion** page in context of a product master or released product variant, you can select if you want to set up the unit conversion for the product or for a product variant. You do that by selecting either **Product variant** or **Product** in the **Create conversion for** field.

### Product variant

If you select **Product variant,** then you can select for which variant you want to set up the unit conversion in the **Product variant** field.

### Product

If you select **Product**, then you can set up a unit conversion for the product master. This unit conversion will apply for all product variants with no defined unit conversion.

### Example

A product master, **T-Shirt**, has four released products variants Small, Medium, Large, and X-Large. The T-shirts are packed in boxes and there can be five T-shirts in a box, except for the Extra-large size where there is only space for four T-shirts.

First, open the **Unit conversion** page from the Release product details page for **T-shirt.**

On the **Unit conversion** page, set up the unit conversion for the release product variant X-Large.

| **Field**             | **Setting**             |
|-----------------------|-------------------------|
| Create conversion for | Product variant         |
| Product variant       | T-Shirt : : X-Large : : |
| From unit             | Boxes                   |
| Factor                | 4                       |
| To Unit               | Pieces                  |

The Released product variants Small, Medium, and Large have the same unit conversion between the unit Box and Pieces, which means that you can define the unit conversion for these product variants on the product master.

| **Field**             | **Setting** |
|-----------------------|-------------|
| Create conversion for | Product     |
| Product               | T-Shirt     |
| From unit             | Boxes       |
| Factor                | 5           |
| To Unit               | Pieces      |

### Using Excel to update the unit conversions

If a product has many product variants with different unit conversions, it's a good idea to export the unit conversions from the **Unit conversion** page to an Excel spreadsheet, update the conversions, and then publish them back to Supply Chain Mangement.

The option to export to Excel and publish the edits back to Supply Chain Mangement is enabled from the **Open in Microsoft office** menu item on the Action Pane on the **Unit conversion** page.
