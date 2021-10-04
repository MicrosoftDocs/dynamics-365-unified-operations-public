---
# required metadata

title: Search results module
description: This topic covers search results modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 05/28/2021
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

## Enable inventory awareness on search results module

Customers generally expect the e-commerce site to be inventory-aware throughout the browsing experience so that they can make decisions on what to do in case of no inventory. The search results module can be enhanced to incorporate inventory data and provide the following experiences:

- Display inventory availability label along with products
- Hide out of stock products
- Display out of stock products at the end of list
	
To enable such experiences, as prerequisites, the followings need to be configured in Commerce headquarters.

First, in **Feature management** workspace, enable a feature named **Enhanced e-Commerce product discovery to be inventory-aware**, which is available in 10.0.20 release and later. 

Then, go to **Retail and Commerce** > **Retail and Commerce IT** > **Products and inventory**, click **Populate product attributes with inventory level**. In the prompt dialog, give a name to a dedicated product attribute that will be created to capture inventory availability, and select an on-hand quantity based on which you want the inventory level to be calculated.

> [!NOTE]
> For consistent inventory level calculation across product details page and product list pages in the e-commerce site, please ensure you select the same quantity for the **Inventory availability based on** setting in Commerce headquarters, and for the **Inventory level based on** setting in the Site builder. For more information about inventory settings in Site builder, see [Apply inventory settings](https://docs.microsoft.com/dynamics365/commerce/inventory-settings).

Next, run the job in the background. The job is responsible for creating a new product attribute as defined in former step, and populating that product attribute for each master product with the latest inventory level value. Considering the inventory availability for a product constantly changes as the product being sold or assortment being updated, it's strongly recommended to schedule the job as a batch processing.

> [!NOTE]
> For products displayed in search results module, the inventory level is populated at master product level rather than individual variant level, and only has two possible values - one indicates "available" and the other indicates "out of stock". The actual value text is retrieved from [inventory level profile](https://docs.microsoft.com/dynamics365/commerce/inventory-buffers-levels) definition. A master product is considered out of stock only when **all** its variants are out of stock. The inventory level of a variant is determined based on the product's inventory level profile definition. 

Finally, after the job is executed, properly configure the newly created product attribute for the e-commerce site that you want to enable inventory awareness on search results module.

1. Navigate to the **Retail and Commerce** > **Channel setup** > **Channel categories and product attributes** form, select an e-commerce site.
1. Click and open an associated attribute group, add the newly created product attribute to the group, then close the form.
1. Click **Set attribute metadata**, select the newly added product attribute, and turn on the **Show attribute on channel**, **Retrievable**, **Can be refined** and **Can be queries** toggles.

With all above configuration done, the refiners on search results page will display an inventory based filter, and the search results module will retrieve inventory data behind the scenes. You could then configure the **Inventory settings for product list pages** in Site builder to control how out-of-stock products should be displayed in search results module. For more details about that site level inventory setting, see [Apply inventory settings](https://docs.microsoft.com/dynamics365/commerce/inventory-settings).

## Additional resources

[Default category landing page and search results page overview](category-search-page-overview.md)

[Module library overview](starter-kit-overview.md)

[Quick view module](quick-view-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
