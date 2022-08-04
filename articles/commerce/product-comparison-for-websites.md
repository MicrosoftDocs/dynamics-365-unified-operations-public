---

# required metadata

title: Product comparison on e-commerce websites
description: This article describes a feature that allows shoppers to do product comparisons on Microsoft Dynamics 365 Commerce websites.
author: ashishmsft
ms.date: 08/03/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin, josaw
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2022-02-28
---

# Product comparison on e-commerce websites

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article describes a feature that allows shoppers to do product comparisons on Microsoft Dynamics 365 Commerce websites.

> [!NOTE]
> The product comparison feature is available starting with the Dynamics 365 Commerce version 10.0.29 release and can be used for both business-to-consumer (B2C) and business-to-business (B2B) websites.

Product comparison functionality enables shoppers to compare products across a wide range of categories to help them make the right purchase decision. On product list pages (PLPs) such as category results, search results, and product collections pages, you can add a button for product comparison that allows shoppers to add products to the comparison tray. This is done in Commerce site builder using the product comparison module, which functions similar to the [Quick view module](quick-view-module.md). When site users add products for comparison by selecting them from product tiles, a comparison tray appears at the bottom of the page that shows the total number of products the shopper is currently comparing along with short previews of the products. Site users are also able to add products from product details pages (PDPs), and can add specific product variants to compare with product masters.

When using the comparison tray, customers can add a few products to compare and then select **Compare** to be redirected to a product comparison page. The product comparison page shows customers product details for each selected product so they can compare images, prices, product dimensions (size, style, color), aggregated ratings information, and various other product attributes.

![Product comparison overview showing the compare product button, the remove from comparison button, the comparison tray panel, and the product comparision page ](./media/Product-Comparison-Overview.png)

> [!NOTE]
> - The product comparison page compares a default set of product properties as well as all attributes that are viewable on a PDP for a given product. 
> - Properties like delivery mode, on-hand inventory, and unit of measure are not viewable on a product comparison page. 
> - Customers are able to add products from different categories as long as they're from same catalog. 
> - Product comparison is currently limited to an individual catalog. In other words, shoppers aren't allowed to do cross-catalog comparisons. 

![Product comparison page](./media/Product-Comparison-Page.png)

## Product comparison module 

You can create a dedicated product comparison page by adding a product comparison module to the body of a page under the **Main slot** of the page structure. In addition to allowing customers to compare product details of different products, you can configure the product comparison module to also give customers the option to quickly complete their purchase after comparison. The product comparison module also contains an **Empty comparison** slot to add a content block module that describes the empty state, for example "Your product comparison is empty".

![Product comparison module](./media/Product-comparison-module.png)

### Add a product comparison button on product tiles in search and category results

The product comparison button lets users quickly add a product to the comparison tray when they browsing products on a list page. They can add one or more products to the comparison tray from a list page without having to go to a PDP. 

The product comparison button is supported by the product collection, search results, and PDP buy box modules.

The following example illustration from Commerce site builder shows how to place a product comparison button on a product list page.

![Product comparison button](./media/Product-comparison-button-and-preview-panel-for-search-results.png)

## Specify the maximum number of products to be displayed in the comparison tray 

You can specify the maximum number of products to be displayed in the comparison tray in site builder at **Site settings \> Extensions**. You can configure separate maximum limits for desktop and mobile/tablet views. If no maximum limit is defined, no limit will be enforced by default.

To specify the maximum number of products in the comparison tray, follow these steps.

1. In site builder, go to **Site settings \> Extensions**.
1. Scroll down to find the following settings:
    - **Products in the comparison limit - desktop devices**
    - **Products in the comparison limit - mobile and tablet devices**
1. For each of these settings, enter the maximum number of products that should be displayed for those viewports in the comparision tray. 
 
![Site settings to limit products in comparison tray](./media/Site-settings-to-limit-products-in-comparison-tray.png)


