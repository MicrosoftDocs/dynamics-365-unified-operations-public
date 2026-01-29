---
title: Pickup information module
description: Learn about the pickup information module and how to add it to checkout pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-09021
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Pickup information module

[!include [banner](includes/banner.md)]

This article describes the pickup information module and explains how to add it to checkout pages in Microsoft Dynamics 365 Commerce.

Use the pickup information module in a checkout module to show order pickup information. Customers can view available pickup dates and time slots, and then select a suitable time to pick up their order. For example, a customer can choose to pick up an order at 3 PM on March 21 from the San Francisco store.

You must configure pickup time slots for the appropriate stores in Commerce headquarters. For more information, see [Create and update time slots for customer pickup](dev-itpro/pickup-timeslots.md).

If you create a pickup information module on a checkout page but don't define time slots for the store that the customer selects for pickup, the module shows information but the user can't select any time slots. Time slots are optional and aren't required to place an order.

If a customer selects multiple items for pickup across multiple stores, the pickup information module lets the user select a time slot for each store, if time slots are available.

> [!NOTE]
> Support for time slots and the checkout pickup information module is available in Dynamics 365 Commerce version 10.0.15 and later.

The following illustration shows an example of time slot selection through the pickup information module on a checkout page.

:::image type="content" source="./dev-itpro/media/Curbside_timeslot_eCommerce.PNG" alt-text="Screenshot of a pickup information module on a checkout page.":::

## Module properties

- **Heading** – Enter a heading for the module.

## Show time slot information after an order is placed

After an order is placed, you can view information about the selected time slot in the [order confirmation module](order-confirmation-module.md) and the [order details module](account-management.md#order-details-page). Both these modules have a **Show timeslot information** property. Before they can show the selected time slot during the order process, set this property to **True**.

## Add a checkout pickup information module to a page

For instructions about how to add a pickup information module to a checkout page and set the required properties, see [Checkout module](add-checkout-module.md).

The following illustration shows an example of an e-commerce checkout page that includes time slots for pickup line items.

:::image type="content" source="./dev-itpro/media/Curbside_timeslot_eCommerce_checkoutsummary.png" alt-text="Screenshot of an e-commerce checkout page that includes time slots for pickup line items.":::

## Additional resources

[Create and update time slots for customer pickup](dev-itpro/pickup-timeslots.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Order details module](account-management.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
