---
# required metadata

title: Apply unit of measure settings
description: This topic covers unit of measure settings and describes how to apply them in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 09/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Apply unit of measure settings

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers unit of measure settings and describes how to apply them in Microsoft Dynamics 365 Commerce.

A product can be sold in different units such as "each," "pair," and "dozen." In Commerce headquarters, the sell by unit of measure can be defined for a product and displayed on an e-commerce site using this setting. For example, if a retailer is selling a product both individually and in dozens, the units of measure available can be displayed along with other product information.

The following example image shows a product configured with a sell unit of measure of **ea** (each) in Commerce Headquarters.

![Example of a product configured with unit of measure in Commerce headquarters](./media/Productunit-headquarters.PNG)

> [!NOTE]
> Support for applying and displaying the unit of measure is available as of the Commerce version 10.0.19 release.

## Unit of measure settings

In Commerce, unit of measure settings are defined at **Site Settings \> Extensions \> Display unit of measure for products** in site builder.  There are 3 settings supported.

**Do not display** : When this setting is selected, the e-commerce site will not display the unit of measure of the product. This is the default behavior.
**Display in product buying experience**: With this setting, the unit of measure is displayed in the product details page, cart, checkout, order history and order details experiences.
**Display in product browsing and product buying experience** : With this setting, the unit of measure is displayed in the product buying experience as stated above and during the product browse expereince. This includes Search results and Product collection modules.

> [!IMPORTANT] 
> These settings are available in the Dynamics 365 Commerce 10.0.19 release. If you are updating from an older version of Dynamics 365 Commerce, you must manually update the appsettings.json file. For instructions on updating the appsettings.json file, see [SDK and module library updates](e-commerce-extensibility/sdk-updates.md#update-the-appsettingsjson-file).

## Modules that use unit of measure settings

Buy box, wishlist, cart, cart icon, search results container, product collection, checkout and order details modules use the unit of measure settings.

The following image shows an example of a product details page (PDP) that is showing the unit of measure  for a product
![Example of a PDP module that has unit of measure](./media/Productunit-PDP.png)

The following image shows an example of a product collection showing the unit of measure for a product

![Example of a product collection module that has unit of measure](./media/Productunit-productcollection.png)

## Additional resources

[Module library overview](starter-kit-overview.md)

[Cart module](add-cart-module.md)

[Buy box module](add-buy-box.md)

[Account management pages and modules](account-management.md)

[SDK and module library updates](e-commerce-extensibility/sdk-updates.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
