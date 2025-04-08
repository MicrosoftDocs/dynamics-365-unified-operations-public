---
title: Search results module
description: This article covers search results modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 05/28/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Search results module

[!include [banner](includes/banner.md)]

This article covers search results modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

The search results module returns product search results and a list of applicable refiners for the products. Search results modules on Dynamics 365 Commerce sites can be used to render pages for the following scenarios:

- Search results that are initiated by a user search
- Search results that show a specific set of products, such as "Shop similar looks"
- Lists of products that belong to a category

For more information about category and search results pages, see [Default category landing page and search results page overview](category-search-page-overview.md).

The following illustration shows an example of a search results page for a category on the Fabrikam site.

![Example of a search results page on the Fabrikam site.](./media/SimpleCategoryLandingDressCategory.png)

## Search results module properties

The following table lists the properties of search result modules, together with their values and descriptions.

| Property | Values | Description |
|----------|--------|-------------|
| Items per page | Integer | The number of items that should be shown on each page. |
| Allow back on PDP | **True** or **False** | If this property is set to **True**, when a user selects a product on the search results page, the breadcrumb navigation on the product details page (PDP) that is opened will show a "Back to results" link. |
| Expand Refiners | **All**, **1**, **2**, **3**, or **4** | The number of top refiners that should be expanded when a page is loaded. For example, if this property is set to **3**, the first three refiners on the page will be expanded. |
| Hide category hierarchy display | **True** or **False** | If this property is set to **True**, the category hierarchy display on the page will be hidden. This property should be set to **True** if you're using the [breadcrumb module](add-breadcrumb.md) to show the category hierarchy.|
| Include product attributes in search results | **True** or **False** | If this property is set to **True**, attributes will be returned for the products in the search results. Although these attributes can be shown on a Commerce site, an extension is required.|
| Show affiliation prices | **True** or **False** | If this property is set to **True**, affiliation prices for products will be shown in the search results when a signed-in user browses the page. |
| Update refiner panel | **True** or **False** | If this property is set to **True**, the refiner panel will be updated when refiners are selected. In this mode, some multiple-selection refiners will behave like single-selection refiners when the refiner panel is updated. |

> [!IMPORTANT]
> In the Commerce version 10.0.16 release and later, the **Show affiliation prices** configuration can be used to show affiliation prices on the page.
>
> In the Commerce version 10.0.20 release and later, the **Update refiner panel** configuration can be used to update the refiner panel during refiner selection.

## Supported modules

The search results module supports the [quick view module](quick-view-module.md), which lets users view product information and add items to the cart from the search results page.

## Add a search results module to a category page

To add a search results module to a category page in site builder, follow these steps.

1. Go to **Templates**, and select **New** to create a new template.
1. In the **New template** dialog box, enter the name **Search results**, and then select **OK**.
1. In the **Body** slot, select the ellipsis (...), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Default Page** module, and then select **OK**.
1. In the **Main** slot of the **Default Page** module, select the ellipsis (...), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Container** module, and then select **OK**.
1. In the **Container** slot, select the ellipsis (...), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Breadcrumb** module, and then select **OK**.
1. In the **Breadcrumb** properties pane, enter the value **1** for **Min Occurs**.
1. In the **Container** slot, select the ellipsis (...), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Search results** module, and then select **OK**.
1. In the **Search results** properties pane, enter the value **1** for **Min Occurs**, and then set any other required properties for the search results module. By setting these properties in the template, you ensure that any customizations to a specific category page will automatically include these settings.
1. Select **Finish editing**, and then select **Publish** to publish the template.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Create a new page** dialog box, under **Page name**, enter **Category page**, and then select **Next**.
1. Under **Choose a template**, select **Search results** template that you created, and then select **Next**.
1. Under **Choose a layout**, select a page layout (for example, **Flexible layout**), and then select **Next**.
1. Under **Review and finish**, review the page configuration. If you need to edit the page information, select **Back**. If the page information is correct, select **Create page**.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Inventory-aware search results module

The search results module can be configured to incorporate inventory data and provide the following experiences:

- Display inventory level labels alongside products.
- Hide out-of-stock products from the product list.
- Display out-of-stock products at the end of the product list.
- Support inventory-based product filtering.

To enable these experiences, you must first enable the **Enhanced e-Commerce product discovery to be inventory-aware** feature, and then configure some prerequisite settings in Commerce headquarters. For more information, see [Inventory-aware product listing](inventory-aware-product-listing.md).

## Additional resources

[Default category landing page and search results page overview](category-search-page-overview.md)

[Module library overview](starter-kit-overview.md)

[Quick view module](quick-view-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
