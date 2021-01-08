---
# required metadata

title: Quick view module
description: This topic covers Quick view module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 01/08/2021
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

This topic covers Quick view module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

When browsing products in a list or a list page, the quick view module allows a user to quickly view the details of an item and add it to bag. - On a list page such as search results or category page with many items, a site user can quickly browse and add items to cart without navigating to the PDP for each item. This module can be added to Product Collection module and Search Results module. 


> [!IMPORTANT]
> The **Quick View** module is available in the Dynamics 365 Commerce 10.0.17 release.

The following image shows an example of a quick view module on a category page

![Example of a quick view module](./media/ecommerce-pdp-buybox.PNG)



## Module properties
The module properties are similar to a buy box module as it supports some of the same functions supported within a buy box.

- **Heading tag** – This property defines the heading tag for the product title. If the buy box is at the top of the page, this property should be set to **h1** to meet accessibility standards. 

- **Enable "shop similar looks" recommendations** - This property allows the buy box to show links to products that look similar to the currently viewed item. This feature is available in Commerce release 10.0.13 and later.


The following image shows an example of an "added to cart" confirmation notification on the Fabrikam site.

![Example of a notification module](./media/ecommerce-addtocart-notifications.PNG)

## Add a quick view module to a page

A quick view module can be added to the Product collection or a Search results module. To add it to product collection module, follow these steps.

1. Go to **Pages**, and select **HomePage** for Fabrikam.
1. Go to any **Product Collection** module on the homepage, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Quick View** module, and then select **OK**.
1. Set Heading tag= H2 for the Quick view module in the property panel.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.
1
## Additional resources

[Module library overview](starter-kit-overview.md)

[Buy box](add-buy-box.md)

[Product collection](add-product-collection.md)
