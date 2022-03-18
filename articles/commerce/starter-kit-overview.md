---
# required metadata

title: Module library overview 
description: This topic presents an overview of the Microsoft Dynamics 365 Commerce module library.
author:  anupamar-ms
ms.date: 09/15/2020
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 

ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Module library overview

[!include [banner](includes/banner.md)]

This topic presents an overview of the Microsoft Dynamics 365 Commerce module library.

The Dynamics 365 Commerce module library is a collection of modules that can be used to build an e-Commerce website. Modules have both user interface (UI) aspects and functional behavior aspects.

Themes can be applied to the modules in the module library to change their look and feel. The themes use Cascading Style Sheets (CSS). A theme for a fictitious e-Commerce site that is named "Fabrikam" is provided as part of the module library and can be used as a reference.

## Module library modules

The following types of modules are provided in the module library:

- **Container module** – A container module is a simple module that acts as a host for other modules. It controls the layout of the modules that are inside it.
- **Marketing modules** – Marketing modules include content block, text block, video player, and carousel modules. All these modules can be used to showcase content. They can be put on any page and are driven by data from the content management system (CMS).
- **Header and footer modules** – Header and footer modules appear in the header and footer of all site pages. These modules can be configured as required through properties.
- **Search modules** – Products can be discovered by using the search module in the header. Search results appear on the search results page. Products can also be discovered on category pages, which are dedicated pages for each category that is supported in the channel navigation hierarchy. In addition, refiner modules can be used to further filter results on search results and category pages.
- **Product details page modules** – Product details pages use several modules to show product information. The buy box module lets customers view products and add them to the cart. Other modules, such as the tech specs module, show the product details. The ratings and reviews module can used to view and provide reviews.
- **Buy online pick up in store module** – The buy online pick up in store module is integrated with Bing Maps. It can be used to find nearby stores where customers can pick up products that they have purchased.
- **Purchase modules** – Purchase modules include the cart module, which can be used to add items to the cart. The checkout module captures the shipping address, delivery options, and gift card, loyalty program, and credit card information, so that an order can be processed. After an order is placed, the order confirmation module can be used to show the confirmation details.
- **Account management modules** – The sign-in module lets customers sign in to an existing account, and the sign-up module lets them create a new account. After an account is created, the order history module can be used to view recent orders, and the order details module can be used to view order details.
- **Recommendations module** – Recommendations are shown by using the product placement module. This module supports algorithmic and editorial lists that can be showcased on any page.

## Additional resources

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]