---
# required metadata

title: Add product to cart settings
description: This topic covers Add product to cart settings and describes how to apply them in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 09/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---


# Add product to cart settings

This topic covers Add product to cart settings and describes how to apply them in Microsoft Dynamics 365 Commerce.

On e-commerce, when a product is added to cart, there are different workflows that are supported. The user may be navigated to cart page. Alternatively, a notification may be shown, confirmating the add to cart action while keeping the user on the current page. To support these different workflows, we have a setting in Site builder. The Add product to cart setting is available in Site Builder under Settings/Extensions. 

There are multiple workflows supported by this setting.

 **Navigate to cart page** - When this setting is chosen, after adding an item to cart, the user will be navigated to the cart page.
 
 **Do not navigate to cart page** - With this setting, after adding an item to cart, the user will remain on the current page.
 
  **Show notification** - With this setting, users are shown a confirmation notification and can continue to browse on the product details page. 
  
  **Show notification using Notification module** - With this setting, users are shown a confirmation notification using the **Notification module**. This module should be included to the page header for this setting to work.
  
  **Show mini-cart** - With this settings, users are shown the mini-cart contents when an item is added to cart. This way a user can browse all the items in the cart and potentially proceed to checkout.

> [!IMPORTANT]
> The **Add product to cart** site settings are available in the Dynamics 365 Commerce 10.0.11 release. If you are updating from an older version of Dynamics 365 Commerce, you must manually update the appsettings.json file. For instructions on updating the appsettings.json file, see [SDK and module library updates](e-commerce-extensibility/sdk-updates.md#update-the-appsettingsjson-file). 

> [!IMPORTANT]
> The **Show mini-cart** option is available in the Dynamics 365 Commerce 10.0.20 release. If you are updating from an older version of Dynamics 365 Commerce, you must manually update the appsettings.json file. For instructions on updating the appsettings.json file, see [SDK and module library updates](e-commerce-extensibility/sdk-updates.md#update-the-appsettingsjson-file). 


The following image shows an example of an "added to cart" confirmation notification on the Fabrikam site.

![Example of a notification module](./media/ecommerce-addtocart-notifications.PNG)

The following image shows an example of an "added to cart" confirmation notification on the Adventure works site.

![Example of a notification module](./media/AW-sitesettings.PNG)

## Additional Resources

[Module library overview](starter-kit-overview.md)

[Buy Box](add-buy-box.md)

[Store selector module](store-selector.md)


[Store selector module](store-selector.md)
