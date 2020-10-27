---
# required metadata

title: Search result module
description: This topic covers search result module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 10/20/2020
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

# Search result module

[!include [banner](includes/banner.md)]

This topic covers search result modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

The search result module returns the products and the list of applicable refiners for the products. On e-commerce site it can be used for the following scenarios:
- Search results initiated by a user search
- Search results that show a specific set of products such as **Shop similar looks**  
- Products that belong to a category

For details refer to [Category and Search page](category-search-page-overview.md).

The following image shows an example of a search results page on the Fabrikam site for a categoy.

![Example of a search result module on the Fabrikam site](./media/SimpleCategoryLandingDressCategory.png)


## Search result module properties and slots

| Property | Values | Description |
|----------------|--------|-------------|
| Items per page | Integer  | Defines the number of items that should be displayed on each page |
| Allow back on PDP | **True** or **False** | If this property is set to **True**, breadcrumb on the PDP will show a "back to results" link when a product is navigated from this result |
| Expand Refiners | All, 1, 2, 3, 4 | Defines how many of the top N refiners will be expanded on page load. A value of 3, means the first 3 refiners on the page will be expanded. |
| Hide category heirarchy display| **True** or **False** | Should be set to True if using the Breadcrumb module to show the category heirarchy|
| Include product attributes in search results| **True** or **False** | If this property is set to **True**, attributes are retrurned for the products in the search result. These attributes can be displayed on the e-commerce site but this will be via an extension|
| Show affiliation prices| **True** or **False** | If this property is set to **True**, shows the affiliation prices for products in the result when a signed-in user is browsing the page |


> [!IMPORTANT]
> In the Dynamics 365 Commerce 10.0.16 release and later, affiliation prices can be displayed on the page using the **Show affiliation prices** configuration


## Create a Category page

To create a category page, follow these steps.

1. Go to **Templates**, and select **New** to create a new templage.
1. In the **New Template** dialog box, enter name as **Search result**
1. In the Main slot, add a **Container**
1. To the Container, add a **Breadcrumb module**, set min occurs =1
1. To the Container, add a **Search result module**, set min occurs =1.
1. On the search result module property panel, set the required properties. Doing these steps in the template will ensure any customizations to a specific category page will be automatically include these settings. 
1. Save template. Publish
1. Create a new page **Category page**. Since all the values are set in the template, the page is ready to go. 
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

 [Category and Search page](category-search-page-overview.md)

