---
title: Delay exact price and discount calculation for improved performance
description: Learn about the delayed price calculation capability that's available in Microsoft Dynamics 365 Commerce point of sale (POS) and call center.
author: boycezhu
ms.date: 01/22/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2017-06-20
ms.custom: 
  - bap-template
---

# Delay exact price and discount calculation for improved performance

[!include [banner](includes/banner.md)]

This article explains the delayed price calculation capability that's available in Microsoft Dynamics 365 Commerce point of sale (POS) and call center.

Dynamics 365 Commerce supports the creation of multiline discounts that apply when you combine multiple sales lines of a sales order or sales quotation. These discounts include mix and match, threshold, and quantity discounts.

Whenever you add a new line to an order, the Commerce pricing engine evaluates the whole cart to determine whether it can apply any of these multiline discounts. Because of this recalculation, the addition of new lines can affect performance as a sales order grows.

However, business-to-business (B2B) companies and some business-to-consumer (B2C) companies often have large order sizes. Therefore, it can be time consuming to wait for the pricing engine to recalculate after each item is added to the cart. Moreover, for large orders, it usually isn't important that the exact price and discount show every time that an item is added to the cart. It's more important that users can add items quickly. The capability to delay exact price and discount calculation until a user requests it or an order is finalized can significantly improve performance. It can also reduce the time that is required to finish placing an order.

The capability to delay exact price and discount calculation has been available in POS. As of the Commerce version 10.0.22 release, it's also available for call center.

## Enable delayed price and discount calculation for POS

To enable delayed price and discount calculation for POS, follow these steps:

1. In Commerce headquarters, go to the functionality profile associated with the physical store.
1. On the **Amount** FastTab, enable the **Manually calculate multiple item discounts** configuration.
1. Open the screen layout designer for the registers where you want to enable the delayed calculation.
1. Add a button for the **Calculate total** operation to the desired button grid.
1. Run the **1070** and **1090** jobs.

Now, when you add items to a transaction, the system doesn't calculate multiline discounts unless the cashier selects the **Calculate total** button. After the cashier selects **Calculate total** for a transaction, the system always calculates multiline discounts for it. The cashier doesn't have to select the button again, even if the cashier adds more items to the cart. The system doesn't allow the cashier to capture payment until **Calculate total** is selected.

## Enable delayed price and discount calculation for call center

To enable delayed price and discount calculation for call center, follow these steps:

1. In Commerce headquarters, go to **Commerce parameters \> Prices and discounts**.
1. In the **Miscellaneous** section, enable the **Manually calculate multi-line prices and discounts** configuration.

When you create or edit a sales order or sales quotation in the call center, the system delays the exact price and discount calculation. The pricing engine considers only the sales line that you add or edit, and it ignores all other sales lines. The net amount for an item includes the price calculation and simple discounts (discount percentage or amount off on an individual item). However, the pricing engine doesn't apply mix and match, threshold, and quantity discounts. Call center users who want to view the exact price, including all discounts, can select one of three buttons: **Recalculate**, **Totals**, or **Complete**.

> [!NOTE]
> For call center orders, the system shows a warning message to remind the user that they must select the **Recalculate**, **Totals**, or **Complete** button for the exact price and discount calculation. For orders where the **Complete** button is available, the call center user must select **Complete** to complete the order capture. For orders where the **Complete** button isn't available, the call center user is responsible for selecting either **Recalculate** or **Totals** before they complete the order capture.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
