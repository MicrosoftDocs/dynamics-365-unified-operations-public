---
# required metadata

title: Gift card module
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

This topic covers gift card modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

Gift cards are a common form of tender, and the gift card module can be used in a checkout module to accept gift cards as payment. The gift card module supports Dynamics 365 gift cards, SVS, and Givex gift cards. SVS and Givex gift cards are redeemed via the Adyen payment provider.

For more information on support for external gift cards such as SVS and Givex, see [Support for external gift cards](./dev-itpro/gift-card.md)

## Module properties

-**Show additional fields** - This property defines what fields should be displayed for gift cards in addition to the gift card number, which is always displayed by default. For example, some gift cards support displaying personal identification number (PIN) and others support displaying PIN and expiration date. Alternatively, this property could be set to "None", which would only display the gift card number and no additional fields.

Supported values:
-	PIN
-	Expiration date
-	PIN and expiration date 
-	None

## Site settings for gift card modules

In Commerce site builder under **Site Settings \> Extensions**, there is a gift card module setting called **Supported gift card type**. This setting supports 3 values:
- **Dynamics 365 gift card** - When this setting is applied, the gift card module only allows the redemption of Dynamics 365 gift cards. This is setting is only supported for signed-in users on the e-Commerce site.
- **SVS and Givex gift cards** - When this setting is applied, the gift card module only allows the redemption of Givex and SVS gift cards. This setting is supported for signed-in and anonymous users on the e-Commerce site.
- **Dynamics 365, SVS, and Givex gift card** - When this setting is applied, the gift card module allows the redemption of Dynamics 365, Givex, and SVS gift cards. This setting is only supported for signed-in users on the e-Commerce site.

## Add a gift card module to a page

For instructions on how to add a gift card module to a checkout page and set the required properties, see [Checkout module](add-checkout-module.md).

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Checkout module](add-checkout-module.md)

[Support for external gift cards](./dev-itpro/gift-card.md)
