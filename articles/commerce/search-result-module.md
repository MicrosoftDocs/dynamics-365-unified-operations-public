---
# required metadata

title: Search results module
description: This topic covers search results module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 12/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
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

The search results module returns product search results and a list of applicable refiners for those products. Search results modules on Dynamics 365 Commerce sites can be used to render pages for the following scenarios.

- Search results initiated by a user search.
- Search results that show a specific set of products, such as **Shop similar looks**.
- Lists of products that belong to a category.

For more information on category and search results pages, see [Default category landing page and search results page overview](category-search-page-overview.md).

The following image shows an example of a search results page on the Fabrikam site for a category.

![Example of a search results module on the Fabrikam site](./media/SimpleCategoryLandingDressCategory.png)

## Search results module properties and slots

| Property | Values | Description |
|----------------|--------|-------------|
| Items per page | Integer  | Defines the number of items that should be displayed on each page. |
| Allow back on PDP | **True** or **False** | If this property is set to **True**, the breadcrumb on the PDP will show a "back to results" link when a product is to navigated from the search results page. |
| Expand refiners | All, 1, 2, 3, 4 | Defines how many of the top refiners will be expanded when a page loads. For example, a value of 3 would mean that the first 3 refiners on the page will be expanded. |
| Hide category hierarchy display| **True** or **False** | Hides or shows the category hierarchy display on the page. Should be set to **True** if using the [breadcrumb module](add-breadcrumb.md) to show the category hierarchy.|
| Include product attributes in search results| **True** or **False** | If this property is set to **True**, attributes are returned for the products in the search result. These attributes can be displayed on a Commerce site, but require an extension to do so.|
| Show affiliation prices| **True** or **False** | If this property is set to **True**, affiliation prices for products are shown in the results when a signed-in user is browsing the page. |

> [!IMPORTANT]
> In Dynamics 365 Commerce 10.0.16 release and later, affiliation prices can be displayed on the page using the **Show affiliation prices** configuration.

## Add a search results module to a category page

To add a search results module to a category page, follow these steps.

1. Go to **Templates**, and select **New** to create a new template.
1. In the **New template** dialog box, enter the name "Search results", and then select **OK**.
1. In the **Body** slot, select the ellipsis (...), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Default Page** module, and then select **OK**.
1. In the **Main** slot of the **Default Page** module, select the ellipsis (...), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Container** module, and then select **OK**.
1. In the **Container** slot, select the ellipsis (...), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Breadcrumb** module, and then select **OK**.
1. In the **Breadcrumb** properties pane, enter the value "1" for **Min Occurs**.
1. In the **Container** slot, select the ellipsis (...), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Search results** module, , and then select **OK**.
1. In the **Search results** properties pane, enter the value "1" for **Min Occurs**, and then set any other required search results module properties. Configuring these properties in the template ensures that any customizations to a specific category page will automatically include these settings. 
1. Select **Finish editing**, and then select **Publish** to publish the template.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Choose a template** dialog box, select the **Search results** template you created, enter "Category page" for the **Page name**, and then select **OK**. Since all the values are set in the template, the page is ready to publish. 
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

 [Default category landing page and search results page overview](category-search-page-overview.md)

