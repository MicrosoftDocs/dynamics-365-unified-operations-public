---
# required metadata

title: Pickup information module
description: This topic covers the pickup information module and describes how to add it to checkout pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 10/13/2020
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

# Pickup information module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers the pickup information module and describes how to add it to checkout pages in Microsoft Dynamics 365 Commerce.

## Overview

The pickup information module can be used in a checkout module to view order pickup information and to choose an available pickup timeslot for an order. It allows customers to view available pickup dates and timeslots so that they can choose a suitable time to pick up their order. For example, a customer can choose to pick up an order at 3 PM on March 21st from the San Francisco store. 

Pickup timeslots for respective stores need to be configured in Commerce headquarters. For more information, see [Timeslot for pickup](./dev-itpro/curbside_pickup_timeslot.md).

If a module is authored on a checkout page but the store selected for pickup does not have timeslots defined, the module will display information without allowing the user to select any timeslots. Timeslots are optional and not required to place an order.

If multiple items are selected for pickup across multiple stores, the pickup information module will allow the user to select a timeslot for each store (if available).

> [!NOTE]
> Support for timeslots and the checkout pickup information module is available starting with the Dynamics 365 Commerce 10.0.15 release.

The following image shows an example of timeslot selection using the pickup information module displayed on a checkout page.
![Example of a pickup information module displayed on a checkout page](./dev-itpro/media/Curbside_timeslot_eCommerce.PNG)

## Module properties

- **Heading** - This property allows you to configure a heading for the module.

## Display timeslot information after placing an order

Once an order is placed, the timeslot information that was selected can be viewed in the [Order confirmation module](order-confirmation-module.md) and [Order details module](account-management.md#order-details-page). These modules have a property called **Show timeslot information** which must be set to "true" to display the selected timeslot during the order process.

## Add a checkout pickup information module to a page

For instructions on how to add a pickup information module to a checkout page and set the required properties, see [Checkout module](add-checkout-module.md).

The following image shows an example of an e-Commerce checkout page with timeslots for pickup line items.
![Example of an e-Commerce checkout page with timeslots for pickup line items](./dev-itpro/media/Curbside_timeslot_eCommerce_checkoutsummary.PNG)

## Additional resources

[Timeslot for pickup](./dev-itpro/curbside_pickup_timeslot.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md) 

[Order details module](account-management.md)
