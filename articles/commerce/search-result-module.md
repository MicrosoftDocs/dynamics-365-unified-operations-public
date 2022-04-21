---
# required metadata

title: Search results module
description: This topic covers search results modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 04/21/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.8

---

# Search results module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers search results modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

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

To add a search results module to a category page, follow these steps.

1. Go to **Templates**, and select **New** to create a new template.
1. In the **New template** dialog box, enter the name **Search results**, and then select **OK**.
1. In the **Body** slot, select the ellipsis (...), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Default Page** module, and then select **OK**.
1. In the **Main** slot of the **Default Page** module, select the ellipsis (...), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Container** module, and then select **OK**.
1. In the **Container** slot, select the ellipsis (...), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Breadcrumb** module, and then select **OK**.
1. In the **Breadcrumb** properties pane, enter the value **1** for **Min Occurs**.
1. In the **Container** slot, select the ellipsis (...), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Search results** module, and then select **OK**.
1. In the **Search results** properties pane, enter the value **1** for **Min Occurs**, and then set any other required properties for the search results module. By setting these properties in the template, you ensure that any customizations to a specific category page will automatically include these settings.
1. Select **Finish editing**, and then select **Publish** to publish the template.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Choose a template** dialog box, select the **Search results** template that you created, enter **Category page** for **Page name**, and then select **OK**. Because all the values are set in the template, the page is ready to be published.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Enable inventory awareness for the search results module

Customers generally expect the e-commerce website to be inventory-aware throughout the browsing experience, so that they can decide what to do if there is no inventory for a product. The search results module can be configured to incorporate inventory data and provide the following experiences:

- Show an inventory availability label together with the product.
- Hide out-of-stock products from the product list.
- Show out-of-stock products at the end of the product list.
- Filter products in search results by inventory level.

To enable these experiences, you must first enable the **Enhanced e-Commerce product discovery to be inventory-aware** feature in the **Feature management** workspace.

> [!NOTE]
> The **Enhanced e-Commerce product discovery to be inventory-aware** feature is available in Commerce version 10.0.20 release and later.

Inventory-aware product search uses product attributes to obtain inventory availability information. As a prerequisite for the feature, dedicated product attributes must be created, inventory data must be entered for them, and they must be added to the online channel. 

To create dedicated product attributes to support the inventory-aware search results module, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Products and inventory**.
1. Select and open **Populate product attributes with inventory level**.
1. In the dialog box, enter the following information:

    1. In the **Product attribute and type name** field, specify a name for the dedicated product attribute that will be created to capture inventory data.
    1. In the **Inventory availability based on** field, select the quantity type that the inventory level calculation should be based on (for example, **Available physical**). 

1. Run the job in the background. Because product inventory constantly changes in an omnichannel environment, we strongly recommend that you schedule this job as a batch process.

> [!NOTE]
> For a consistent inventory level calculation across pages and modules on your e-commerce website, be sure to select the same quantity type for both the **Inventory availability based on** setting in Commerce headquarters and the **Inventory level based on** setting in Commerce site builder. For more information about inventory settings in site builder, see [Apply inventory settings](inventory-settings.md).

To configure the product attributes for an online channel, follow these steps. 

1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.
2. Select an online channel to enable the inventory-aware search results module for.
3. Select and open an associated attribute group, and then add the newly created product attribute to it.
4. For Commerce versions before the 10.0.27 release, select **Set attribute metadata**, select the newly added product attribute, and then turn on the **Show attribute on channel**, **Retrievable**, **Can be refined**, and **Can be queried** options.
5. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**, and run the **1150 (Catalog)** job. If you schedule the **Populate product attributes with inventory level** job as a batch process, we recommend that you also schedule the 1150 job as a batch process that runs at the same frequency.

> [!NOTE]
> For products that are shown in the search results module, the inventory level is shown at the master product level instead of the individual variant level. It has only two possible values: "available" and "out of stock". The actual label for the value is retrieved from the [inventory level profile](inventory-buffers-levels.md) definition. A master product is considered out of stock only when all its variants are out of stock.

After all the preceding configuration steps are completed, the refiners on search results pages will show an inventory-based filter, and the search results module will retrieve inventory data behind the scenes. You can then configure the **Inventory settings for product list pages** setting in Commerce site builder to control how the search results module shows out-of-stock products. For more information, see [Apply inventory settings](inventory-settings.md).

## Additional resources

[Default category landing page and search results page overview](category-search-page-overview.md)

[Module library overview](starter-kit-overview.md)

[Quick view module](quick-view-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
