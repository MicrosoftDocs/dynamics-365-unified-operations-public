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

The following image shows an example of a search results page on the Fabrikam site for a categoy.

![Example of a search result module on the Fabrikam site](./media/cart2.PNG)


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

## Commerce Scale Unit interaction

The cart module retrieves product information by using Commerce Scale Unit APIs. The cart ID from the browser cookie is used to retrieve all the product information from Commerce Scale Unit.

## Add a cart module to a page

To add a cart module to a new page and set the required properties, follow these steps.

1. Go to **Fragments**, and select **New** to create a new fragment.
1. In the **New fragment** dialog box, select the **Cart** module.
1. Under **Fragment name**, enter the name **Cart fragment**, and then select **OK**.
1. Select the **Cart** slot.
1. In the properties pane on the right, select the pencil symbol, enter heading text in the field, and then select the check mark symbol.
1. In the **Cart** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Store selector** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.
1. Go to **Templates**, and select **New** to create a new template.
1. In the **New Template** dialog box, under **Template name**, enter a name for the template.
1. In the outline tree, select the **Body** slot, select the ellipsis (**...**), and then select **Add fragment**.
1. In the **Select fragment** dialog box, select the **Cart fragment** fragment, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Choose a template** dialog box, select the template that you created, enter a page name, and then select **OK**.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

[Cart icon module](cart-icon-module.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)

[Shipping address module](ship-address-module.md)

[Delivery options module](delivery-options-module.md)

[Order details module](order-confirmation-module.md)

[Gift card module](add-giftcard.md)

[Calculate inventory availability for retail channels](calculated-inventory-retail-channels.md)

[Create an online functionality profile](online-functionality-profile.md)
