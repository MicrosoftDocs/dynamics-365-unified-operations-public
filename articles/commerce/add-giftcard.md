---
# required metadata

title: Gift card module
description: This topic covers gift card modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 04/28/2021
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
ms.dyn365.ops.version: Release 10.0.5

---

# Gift card module

[!include [banner](includes/banner.md)]

This topic covers gift card modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

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

## Extend internal gift cards for use in e-commerce storefronts

Since internal gift cards are not optimized by default for use in e-commerce storefronts, they should only be allowed to be used as payment when they have been configured with extensions that make them more secure. The following gift card areas should be extended prior to allowing the use of internal gift cards in production.

- **Gift card number** - Internal gift cards use number sequences to generate gift card numbers. Since number sequences can easily be predicted, gift card number generation should be extended to use a random crypto-secure string for the gift card numbers being issued.
- **GetBalance** - This API is used to look up gift card balances, and is public by default. If a PIN is not required to look up gift card balances, the **GetBalance** API could be abused through the use of brute force attempts to look up gift card numbers with balances. Implementing PIN requirements for internal gift cards and API throttling can both be used to mitigate the risk of brute force attempts to predict gift card numbers.
- **PIN** - Out-of-the-box internal gift cards do not support PIN numbers by default. Internal gift cards should be extended to require PIN numbers for balance lookup. This functionality can also be used to lock gift cards after consecutive incorrect PIN entry attempts.

## Enable gift card payments for guest checkout

By default, gift card payments are not enabled for guest checkout. 

To enable gift card payments for anonymous guest checkout, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> POS Operations**.
1. Right-click the header of the grid listing POS operations, and then select **Insert columns**.
1. In the **Insert columns** dialog box, select the **AllowAnonymousAccess** check box.
1. Select **Update**.
1. For the operations **520** (Gift card balance) and **214**, set the **AllowAnonymousAccess** value to "1."
1. Select **Save**.
1. Run the **1090** scheduler job to synchronize changes to the channel database. 

## Add a gift card module to a page

For instructions on how to add a gift card module to a checkout page and set the required properties, see [Checkout module](add-checkout-module.md).

## Additional resources

[Cart module](add-cart-module.md)

[Cart icon module](cart-icon-module.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)

[Shipping address module](ship-address-module.md)

[Delivery options module](delivery-options-module.md)

[Pickup information module](pickup-info-module.md)

[Order details module](order-confirmation-module.md)

[Support for external gift cards](./dev-itpro/gift-card.md)

[SDK and module library updates](e-commerce-extensibility/sdk-updates.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
