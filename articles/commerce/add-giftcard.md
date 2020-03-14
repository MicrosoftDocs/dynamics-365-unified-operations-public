---
# required metadata

title: Giftcard module
description: This topic covers gift card module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 01/23/2020
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

This topic covers Gift card module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview

Gift cards are a common form of tender. The gift card module can be used in checkout module as a form of tender. The gift card module supports Dynamics 365 gift cards, SVS and Givex gift cards. SVS and Givex gift cards are redeemed via Adyen payment provider.


## Gift card module properties

**Show additional fields** - This property defines what fields should be displayed for gift card in addition to gift card number. For instance, some gift cards support Pin and some support Pin and Expiry date. Depending on the values chosen, the UX will show the respective values. Alternatively a user could choose "None" which only shows gift card number and no additional fields.
-	None
-	Pin
-	Expiry date
-	Pin and Expiry date

## Site settings for gift card

In the Site builder, **Site Settings > Extensions**, gift card module supports a setting called  **Supported gift card type**. This setting supports 3 values. 
1. Dynamics 365 gift card - WHen this setting is applied the gift card module will only allow redeeming of Dynamics 365 gift cards. This is supported only for signed-in users on the e-commerce site.
2. SVS and Givex gift cards - When this setting is applied, the gift card module will only allow redeeming of Givex and SVS gift cards via Adyen. This is supported for signed-in and anonymous users on the e-commerce site.
3. Dynamics 365, SVS and Givex gift card - - When this setting is applied, the gift card module will  allow redeeming Dynamics 365, and Givex, SVS gift cards via Adyen. This is supported for signed-in users only on the e-commerce site.

## Add a gift card module to a page

To add a gift card module to a checkout page and set the required properties, see [Checkout module](add-checkout-module.md).


## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)
