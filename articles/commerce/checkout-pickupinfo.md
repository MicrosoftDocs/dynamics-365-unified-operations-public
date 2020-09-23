---
# required metadata

title: Pickup information module
description: This topic covers Pickup information module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 09/21/2020
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
ms.search.validFrom: 2020-09021
ms.dyn365.ops.version: Release 10.0.15

---

# Checkout pickup information module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers the Pickup information modules and describes how to add it to checkout pages in Microsoft Dynamics 365 Commerce.

## Overview

Pickup information module can be used in checkout module to view the pickup information  and to choose an available time slot for an order. It allows the user to view available dates/time slots available for pickup and they can choose a suitable time slot for their order E.g. Order can be picked on 9/21/20 at 3pm from San Francisco store. 

Timeslot for respective stores need to be configured in headquarters. For more information refer to configuring [Timeslot for pickup](./dev-itpro/curbside_pickup_timeslot.md)

If a module is authored on checkout page but the store selected for pickup does not have time slots defined, the module will display information without allowing the user to select timeslots. In addition, timeslots are optional and not required to place an order.

If multiple items are selected for pickup across multiple stores, the module will allow the user to select a timeslot for each store if available.

> [!NOTE]
> Support for timeslots and Checkout pickup information module is available from Dynamics 365 Commerce 10.0.15 release.

The following image shows an example of timeslot selection using the Pickup information module displayed on a checkout page.
![Example of a Checkout pickup information module](./dev-itpro/media/Curbside_timeslot_eCommerce.PNG)

## Module properties

- **Heading** - This property allows you to configure a heading for the module.

## Add a checkout pickup information module to a page

For instructions on how to add a checkout pickup information module to a checkout page and set the required properties, see [Checkout module](add-checkout-module.md).

The following image shows an example of ecommerce checkout page with timeslots for pickup line items.
![Example of a Checkout pickup information module](./dev-itpro/media/Curbside_timeslot_eCommerce_checkoutsummary.PNG)

## Additional resources

[Cart module](add-cart-module.md)

[Cart icon module](cart-icon-module.md)

[Checkout module](add-checkout-module.md)

