---
title: Generate variants for engineering products
description: This topic describes how to generate variants for engineering products
author: t-benebo
ms.date: 06/08/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-06-08
ms.dyn365.ops.version: 10.0.20
---

# Generate variants for engineering products

[!include [banner](../includes/banner.md)]

This topic describes how to generate variants for engineering products.

## Generate one or more new variants of an engineering product

You can create one or more new variants of a product without copying any information from an existing product. This is useful when you need to create several product variants at the same time.

The following procure provides and example of how to create several variants that include the color dimension.

1. Open the **Released products** page (for example, by going to **Engineering change management \> Common \> Released products**).
1. On the Action Pane, open the **Product** tab and, from the **New** group, select **Engineering product**.
1. The **New product** dialog opens. Select the appropriate **Engineering category**.
1. If your selected engineering category includes variant dimensions, then you can set values for them now. (For this example, suppose the category has a **Color** dimension, which you now set to *Blue*.)
1. Make other settings as needed, and select **OK** to create the product.
1. The product and the blue V-1 variant are created, and the new product now opens.
1. Add a BOM and route to the variant as needed.
1. On the Action Pane, open the **Product** tab and, from the **Product master** group, select **Product dimensions**.
1. The **Product dimensions** page opens. This page includes a tab for each available dimension. On each tab, add a row for each value you will support for each relevant dimension. (For this example, you might add rows on the **Color** tab for *White*, *Yellow*, and *Green*).
1. Close the page and select **Released product variants**. Note that the first created variant (white V-1) appears.
1. Select **Variants suggestions**.
1. The system suggests variants with the created color values (for example, white V-1, yellow V-1, and green V-1).
1. Select the suggested variants and select **OK** to release the variants in the engineering company.
    - Note that none of the created variants will have a BOM or a route.
    - Note that the attributes for these variants are defaulted from the engineering category and not copied from the previous variant.

## Generate a variant as a copy of another product variant

You can create a variant of a product based on another product variant. The bill of materials (BOM) and route from the source product variant are copied to the new variant. This may be useful for discrete manufacturing products where it can be helpful to create the BOM based on a starting BOM and keep track of the changes from the previous variant. To maintain traceability, the system records which variant was copied to create new copy.

The following procure provides and example of how to create a new variant that includes the color dimension by creating a copy of an existing variant.

1. Create the engineering product. Choose the engineering category and the value for the relevant dimension (for example, set the color to blue) by selecting  **New \> Engineering product** on the **Products** tab on the **Released products** page in the engineering company.
1. The product and the blue V-1 variant are created.
1. Add a BOM and a route for the blue V-1 if desired.
1. Add attributes to the product variant as needed.
1. Add the blue V-1 product variant to an engineering change order.
1. Set **Impact** to *New variant*.
1. Select the new color value (for example, white).
    - Note that the new variant has a BOM and a route that have been copied from the previous variant.
    - Note that the new variant also has the attributes copied from the previous variant.
1. Approve the change order.
1. Process the change order. Once processed, the new V-1 variant will be created and released in the engineering company.
