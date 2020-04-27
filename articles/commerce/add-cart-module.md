---
# required metadata

title: Cart module
description: This topic covers cart modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 05/25/2020
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
ms.dyn365.ops.version: Release 10.0.5

---

# Cart module

[!include [banner](includes/banner.md)]

This topic covers cart modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A cart module shows the items that have been added to the cart before the customer proceeds to checkout. The module also shows an order summary and lets the customer apply or remove promotional codes.

The cart module supports signed-in checkout and guest checkout. It also supports a **Back to shopping** link. You can configure the route for this link at **Site Settings \> Extensions \> Routes**.

The cart module renders data based on the cart ID, which is a browser cookie available throughout the site. 

The following image shows an example of a Fabrikam site cart page.

![Example of a cart module](./media/cart2.PNG)

## Cart module properties and slots

The cart module has a **Heading** property that can be set to values such as **Shopping bag** and **Items in your cart**. 

## Modules that can be used in a cart module

- **Text block** – This module supports custom messaging in the cart module. The messages are driven by the content management system (CMS). Any message can be added, such as "For issues with your order, contact 1-800-Fabrikam."
- **Store selector** – This module shows a list of nearby stores where an item is available for pickup. It lets users enter a location to find stores that are nearby. For more information on this module, see [Store selector module](store-selector.md).


## Module properties

Cart modules have the following settings that can be configured at **Site Settings \> Extensions**:

- **Maximum quantity** – This property is used to specify the maximum number of each item that can be added to the cart. For example, a retailer might decide that only 10 of each product can be sold in a single transaction.
- **Inventory check** – When the value is set to **True**, an item is added to the cart only after the buy box module makes sure that it's in stock. This inventory check is done for scenarios where the item will be shipped and for scenarios where it will be picked up in the store. If the value is set to **False**, no inventory check is done before an item is added to the cart and the order is placed. For information on how to configure inventory settings in back office, see [Calculate inventory availability for retail channels](calculated-inventory-retail-channels.md).
- **Inventory buffer** – This property is used to specify a buffer number for inventory. Inventory is maintained in real time, and when many customers place orders, it can be difficult to maintain an accurate inventory count. When an inventory check is done, if the inventory is less than the buffer amount, the product is treated as out of stock. Therefore, when sales occur quickly through several channels, and the inventory count isn't fully synced, there is less risk that an item that is out of stock will be sold.
- **Back to shopping** – This property is used to specify the route for the **Back to shopping** link. The route can be configured at the site level, allowing retailers to take the customer back to the home page or any other page on the site.

## Commerce Scale Unit interaction

The cart module retrieves product information by using Commerce Scale Unit APIs. The cart ID from the browser cookie is used to retrieve all the product information from Commerce Scale Unit.

## Add a cart module to a page

To add a cart module to a new page and set the required properties, follow these steps.

1. Go to **Page Fragments** and select **+New** to create a new fragment.
1. In the **New Page Fragment** dialog box, select the **Cart** module.
1. Under **Page Fragment Name**, enter the name **Cart fragment**, and then select **OK**.
1. Select the **Cart** slot.
1. In the properties pane on the right, select the pencil symbol, enter heading text in the box, and then select the check mark symbol.
1. In the **Cart** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Store selector** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.
1. Go to **Templates** and select **+New** to create a new template.
1. In the **New Template** dialog box, under **Template name** enter a name for the template.
1. In the outline tree, select the **Body** slot, select the ellipsis (**...**), and then select **Add Fragment**.
1. In the **Select Page Fragment** dialog box, select the **Cart fragment** fragment, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages** and select **+New** to create a new page.
1. In the **Choose a template** dialog box, select the template you created, enter a page name, and then select **OK**.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Store selector module](store-selector.md)

[Buy box module](add-buy-box.md)

[Cart icon module](cart-icon-module.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)

[Calculate inventory availability for retail channels](calculated-inventory-retail-channels.md)
