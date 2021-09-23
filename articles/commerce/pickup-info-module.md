---
# required metadata

title: Pickup information module
description: This topic covers the pickup information module and describes how to add it to checkout pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 11/06/2020
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
ms.search.validFrom: 2020-09021
ms.dyn365.ops.version: Release 10.0.15

---

# Pickup information module

[!include [banner](includes/banner.md)]

This topic covers the pickup information module and describes how to add it to checkout pages in Microsoft Dynamics 365 Commerce.

The pickup information module can be used in a checkout module to show order pickup information. Customers can view available pickup dates and time slots, and then select a suitable time to pick up their order. For example, a customer can choose to pick up an order at 3 PM on March 21 from the San Francisco store.

Pickup time slots for the appropriate stores must be configured in Commerce headquarters. For more information, see [Create and update time slots for customer pickup](dev-itpro/pickup-timeslots.md).

If a pickup information module is created on a checkout page, but no time slots are defined for the store that is selected for pickup, the module will show information, but the user won't be able to select any time slots. Time slots are optional and aren't required to place an order.

If multiple items are selected for pickup across multiple stores, the pickup information module will let the user select a time slot for each store, provided that time slots are available for it.

> [!NOTE]
> Support for time slots and the checkout pickup information module is available in Dynamics 365 Commerce version 10.0.15 and later.

The following illustration shows an example of time slot selection through the pickup information module on a checkout page.

![Example of a pickup information module on a checkout page.](./dev-itpro/media/Curbside_timeslot_eCommerce.PNG)

## Module properties

- **Heading** – Enter a heading for the module.

## Show time slot information after an order is placed

After an order is placed, information about the selected time slot can be viewed in the [order confirmation module](order-confirmation-module.md) and the [order details module](account-management.md#order-details-page). Both these modules have a **Show timeslot information** property. Before they can show the selected time slot during the order process, this property must be set to **True**.

## Add a checkout pickup information module to a page

For instructions about how to add a pickup information module to a checkout page and set the required properties, see [Checkout module](add-checkout-module.md).

The following illustration shows an example of an e-Commerce checkout page that includes time slots for pickup line items.

![Example of an e-Commerce checkout page that includes time slots for pickup line items.](./dev-itpro/media/Curbside_timeslot_eCommerce_checkoutsummary.PNG)

## Additional resources

[Create and update time slots for customer pickup](dev-itpro/pickup-timeslots.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Order details module](account-management.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]