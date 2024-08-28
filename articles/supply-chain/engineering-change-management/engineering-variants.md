---
title: Generate variants for engineering products
description: Learn how to generate variants for engineering products, including an outline on generating one or more new variants of engineering products.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 06/08/2021
ms.reviewer: kamaybac
ms.search.form:
---

# Generate variants for engineering products

[!include [banner](../includes/banner.md)]

This article describes how to generate variants for engineering products.

## Turn variant generation for engineering products on or off

The functionality described in this article requires that both the *Engineering Change Management* and *Variant generation for engineering products* features be turned on for your system. For details about how to turn these features on or off, see [Engineering change management overview](product-engineering-overview.md).

## Generate one or more new variants of an engineering product

You can create one or more new variants of a product without copying information from an existing product. This is useful when you need to create several product variants at the same time.

The following procedure provides an example of how to create several variants that include the color dimension.

1. Open the **Released products** page (for example, go to **Engineering change management \> Common \> Released products**).
1. On the Action Pane, open the **Product** tab and, from the **New** group, select **Engineering product**.
1. The **New product** dialog opens. Select the appropriate **Engineering category**.
1. If your selected engineering category includes variant dimensions, then you can set values for them now. For this example, if the category has a **Color** dimension, you can set it to *Blue*.
1. Make other settings as needed. Select **OK** to create the product.
1. The product and the blue V-1 variant are created, and the new product now opens.
1. Add a bill of materials (BOM) and route to the variant as needed.
1. On the Action Pane, open the **Product** tab and, from the **Product master** group, select **Product dimensions**.
1. The **Product dimensions** page opens. This page includes a tab for each available dimension. On each tab, add a row for each value you will support for each relevant dimension. (For this example, you might add rows on the **Color** tab for *White*, *Yellow*, and *Green*).
1. Close the page, and then select **Released product variants**. Notice that the first variant that you created (blue V-1) appears.
1. On the Action Pane, on the **Product variant** tab, select **Variants suggestions**.
1. In the **Variant suggestions** dialog box, follow one of these steps:

    - At the top of the dialog box, there is a section for each available dimension. For each dimension, select the checkbox for each value that you want to generate a variant suggestion for, and then select **Suggest** on the toolbar. Relevant suggestions are added to the **Suggested variants** section.
    - Select **Suggest all** on the toolbar to generate variant suggestions for all available combinations of dimension values. The suggestions are added to the **Suggested variants** section.

1. In the **Suggested variants** section, select the checkbox for each variant that you want to create. Then select **Create** to generate and release the selected variants to the engineering company. The following conditions apply:

    - None of the created variants will have a BOM or route.
    - The attributes for these variants will default from the engineering category and will not be copied from the previous variant.

## Generate a variant as a copy of another product variant

You can create a variant of a product based on another product variant. The bill of materials (BOM) and route from the source product variant are copied to the new variant. This may be useful for discrete manufacturing products where it can be helpful to create the BOM based on a starting BOM and keep track of the changes from the previous variant. To maintain traceability, the system records which variant was copied to create new copy.

The following procedure provides an example of how to create a new variant that includes the color dimension by creating a copy of an existing variant

1. Open the **Released products** page (for example, go to **Engineering change management \> Common \> Released products**).
1. On the Action Pane, open the **Product** tab and, from the **New** group, select **Engineering product**.
1. The **New product** dialog opens. Select the appropriate **Engineering category**.
1. If your selected engineering category includes variant dimensions, then you can set values for them now. For this example, if the category has a **Color** dimension, you can  set it to *Blue*.)
1. Make other settings as needed. Select **OK** to create the product.
1. The product and the blue V-1 variant are created, and the new product now opens.
1. Add a BOM and route to the variant as needed.
1. Add attributes to the product variant as needed.
1. Add the blue V-1 product variant to an engineering change order.
1. Set **Impact** to *New variant*.
1. Select the new color value (for example, *White*). Note that the following conditions will apply: 
    - The new variant has a BOM and route that have been copied from the previous variant.
    - The new variant has the attributes copied from the previous variant.
1. Approve the change order.
1. Process the change order. After the order is processed, the new V-1 variant will be created and released to the engineering company.
