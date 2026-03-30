---
title: Search results module
description: Learn about search results modules and how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/29/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Search results module

[!include [banner](includes/banner.md)]

This article describes search results modules and how to add them to site pages in Microsoft Dynamics 365 Commerce.

The search results module returns product search results and a list of applicable refiners for the products. Use search results modules on Dynamics 365 Commerce sites to render pages for the following scenarios:

- Search results that a user initiates by using a search
- Search results that show a specific set of products, such as "Shop similar looks"
- Lists of products that belong to a category

For more information about category and search results pages, see [Default category landing page and search results page overview](category-search-page-overview.md).

The following illustration shows an example of a search results page for a category on the Fabrikam site.

:::image type="content" source="./media/SimpleCategoryLandingDressCategory.png" alt-text="Screenshot of a search results page on the Fabrikam site.":::

## Search results module properties

The following table lists the properties of search result modules, together with their values and descriptions.

| Property | Values | Description |
|----------|--------|-------------|
| Items per page | Integer | The number of items that you want to show on each page. |
| Allow back on PDP | **True** or **False** | If you set this property to **True**, when a user selects a product on the search results page, the breadcrumb navigation on the product details page (PDP) that opens shows a "Back to results" link. |
| Expand Refiners | **All**, **1**, **2**, **3**, or **4** | The number of top refiners that you want to expand when a page loads. For example, if you set this property to **3**, the first three refiners on the page are expanded. |
| Hide category hierarchy display | **True** or **False** | If you set this property to **True**, the category hierarchy display on the page is hidden. Set this property to **True** if you're using the [breadcrumb module](add-breadcrumb.md) to show the category hierarchy.|
| Include product attributes in search results | **True** or **False** | If you set this property to **True**, attributes are returned for the products in the search results. Although you can show these attributes on a Commerce site, an extension is required.|
| Show affiliation prices | **True** or **False** | If you set this property to **True**, affiliation prices for products are shown in the search results when a signed-in user browses the page. |
| Update refiner panel | **True** or **False** | If you set this property to **True**, the refiner panel is updated when refiners are selected. In this mode, some multiple-selection refiners behave like single-selection refiners when the refiner panel is updated. |

> [!IMPORTANT]
> In the Commerce version 10.0.16 release and later, use the **Show affiliation prices** configuration to show affiliation prices on the page.
>
> In the Commerce version 10.0.20 release and later, use the **Update refiner panel** configuration to update the refiner panel during refiner selection.

## Supported modules

The search results module supports the [quick view module](quick-view-module.md), which lets users view product information and add items to the cart from the search results page.

## Add a search results module to a category page

To add a search results module to a category page in site builder, follow these steps:

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
1. In the **Search results** properties pane, enter the value **1** for **Min Occurs**, and then set any other required properties for the search results module. By setting these properties in the template, you ensure that any customizations to a specific category page automatically include these settings.
1. Select **Finish editing**, and then select **Publish** to publish the template.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Create a new page** dialog box, under **Page name**, enter **Category page**, and then select **Next**.
1. Under **Choose a template**, select the **Search results** template that you created, and then select **Next**.
1. Under **Choose a layout**, select a page layout (for example, **Flexible layout**), and then select **Next**.
1. Under **Review and finish**, review the page configuration. If you need to edit the page information, select **Back**. If the page information is correct, select **Create page**.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Inventory-aware search results module

You can configure the search results module to incorporate inventory data and provide the following experiences:

- Display inventory level labels alongside products.
- Hide out-of-stock products from the product list.
- Display out-of-stock products at the end of the product list.
- Support inventory-based product filtering.

To enable these experiences, first enable the **Enhanced e-Commerce product discovery to be inventory-aware** feature. Then, configure some prerequisite settings in Commerce headquarters. For more information, see [Inventory-aware product listing](inventory-aware-product-listing.md).

## Additional resources

[Default category landing page and search results page overview](category-search-page-overview.md)

[Module library overview](starter-kit-overview.md)

[Quick view module](quick-view-module.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
