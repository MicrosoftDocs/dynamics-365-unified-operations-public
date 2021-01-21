---
# required metadata

title: Quick view module
description: This topic covers quick view modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 01/28/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2020-01-08
ms.dyn365.ops.version: Release 10.0.17

---

# Quick view module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers quick view modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

The quick view module allows a user to quickly view a product's information when browsing products on a list page, and then add the product to the cart without having to navigate to the product details page (PDP). The purpose of the module is to allow a user to add multiple items to the cart while browsing a list page. The quick view module provides an overview of the product information necessary to make an "add to cart" decision. The quick view module also provides a link to the PDP for more additional product details and options to buy.

The quick view module is supported by the [Product collection](add-product-collection.md) and [Search results](search-result-module.md) modules.

> [!IMPORTANT]
> The quick view module is available as of the Dynamics 365 Commerce version 10.0.17 release.

The following image shows an example of a quick view module on a product list page.

![Example of a quick view module on a product list page](./media/ecommerce-quickview.PNG)

## Module properties

The quick view module properties are similar to those of a buy box module since it supports some of the same functions supported within a buy box module.

| Property | Values | Description |
|----------------|--------|-------------|
| Heading tag | **H1**, **H2**, **H3**, **H4**, **H5**, or **H6** | This property defines the heading tag for the product title. If the buy box is at the top of the page, this property should be set to **H1** to meet accessibility standards.  |
| Allow custom price | **True** or **False** | If this property is set to **True**, the buy box allows a custom price to be entered by the user.|
| Minimum price| Integer| This property is applicable only if the **Allow custom price** property is set to **True**. It sets the minimum price a user can input (for example, $1).|
| Maximum price| Integer| This property is applicable only if the **Allow custom price** property is set to **True**. It sets the maximum price a user can input (for example, $1000).|

## Commerce site builder settings

The quick view module also respects the **Site Settings \> Extensions** settings for **Add to cart** similar to Buy box. However, the **Navigate to cart page** setting is ignored since it does not align with the intent of the quick view module, which is to allow the user to browse multiple products on a list page and add them to the cart without navigating away from the list page.

## Add a quick view module to a product collection module

A quick view module can be added to the Product collection or a Search results module. 

To add a quick view module to a product collection module in site builder, follow these steps.

1. Go to **Pages**, and then select the home page for the Fabrikam site.
1. Go to any **Product Collection** module on the homepage, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Quick View** module, and then select **OK**.
1. In the **Quick View** module properties pane, select **Heading**. In the **Heading** dialog box, set the **Heading Level** to **H2**, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Buy box module](add-buy-box.md)

[Product collection module](add-product-collection.md)

[Search results module](search-result-module.md)
