---
# required metadata

title: Gift card module
description: This topic covers gift card modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 09/15/2020
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

# Gift card module

[!include [banner](includes/banner.md)]

This topic covers gift card modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

Gift card modules can be used in checkout modules to accept gift cards, a common form of payment used for e-Commerce transactions. The gift card module supports Dynamics 365, SVS, and Givex gift cards. SVS and Givex gift cards are redeemed via the Adyen payment provider. For more information about support for external gift cards such as SVS and Givex, see [Support for external gift cards](./dev-itpro/gift-card.md).

> [!NOTE]
> Support for redeeming SVS and Givex gift cards during checkout flow is available in the Dynamics 365 Commerce 10.0.11 release. 

There are two gift card modules available:

- **Gift card** - This module can be used on a checkout page to redeem a gift card as tender. 
- **Gift card balance check** - This module can be used on any page to check the balance on a gift card. This module is available in Commerce release 10.0.14 and later.

> [!NOTE]
> Support for the gift card balance check module is available in the Dynamics 365 Commerce 10.0.14 release.

The following image shows an example of a gift card module on a checkout page.

![Example of a gift card module](./media/ecommerce-giftcard.PNG)

## Module properties

- **Show additional fields** - This property defines what fields should be displayed for gift cards in addition to the gift card number, which is always displayed by default. For example, some gift cards support displaying a personal identification number (PIN), and others support displaying a PIN and expiration date. Alternatively, this property could be set to "None", which would only display the gift card number and no additional fields.

Supported values:
-	PIN
-	Expiration date
-	PIN and expiration date 
-	None

## Site settings for gift card modules

In Commerce site builder under **Site Settings \> Extensions**, there is a gift card module setting called **Supported gift card type**. This setting supports three values:
- **Dynamics 365 gift card** - When this setting is applied, the gift card module only allows the redemption of Dynamics 365 gift cards. This setting is only supported for signed-in users on the e-Commerce site.
- **SVS and Givex gift cards** - When this setting is applied, the gift card module only allows the redemption of Givex and SVS gift cards. This setting is supported for signed-in and anonymous users on the e-Commerce site.
- **Dynamics 365, SVS, and Givex gift cards** - When this setting is applied, the gift card module allows the redemption of Dynamics 365, Givex, and SVS gift cards. This setting is only supported for signed-in users on the e-Commerce site.

> [!IMPORTANT]
> These settings are available in the Dynamics 365 Commerce 10.0.11 release and are required only if you need support for SVS or Givex gift cards. If you are updating from an older version of Dynamics 365 Commerce, you must manually update the appsettings.json file. For instructions on updating the appsettings.json file, see [SDK and module library updates](e-commerce-extensibility/sdk-updates.md#update-the-appsettingsjson-file). 

## Add a gift card module to a page

For instructions on how to add a gift card module to a checkout page and set the required properties, see [Checkout module](add-checkout-module.md).

## Additional resources

[Cart module](add-cart-module.md)

[Cart icon module](cart-icon-module.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)

[Shipping address module](ship-address-module.md)

[Delivery options module](delivery-options-module.md)

[Order details module](order-confirmation-module.md)

[Support for external gift cards](./dev-itpro/gift-card.md)

[SDK and module library updates](e-commerce-extensibility/sdk-updates.md)
