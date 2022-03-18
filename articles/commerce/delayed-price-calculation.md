---
# required metadata

title: Delay exact price and discount calculation for improved performance
description: This topic describes the delayed price calculation capability that is available in Microsoft Dynamics 365 Commerce point of sale (POS) and call center.
author: boycezhu
ms.date: 09/09/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: boycez
ms.search.validFrom: 2017-06-20
---

# Delay exact price and discount calculation for improved performance

[!include [banner](includes/banner.md)]

This topic describes the delayed price calculation capability that is available in Microsoft Dynamics 365 Commerce point of sale (POS) and call center.

Dynamics 365 Commerce supports the creation of multiline discounts that are applied when multiple sales lines of a sales order or sales quotation are combined. These discounts include mix and match, threshold, and quantity discounts.

Whenever a new line is added to an order, the Commerce pricing engine evaluates the whole cart to determine whether any of these multiline discounts can be applied. Because of this recalculation, the addition of new lines can affect performance as a sales order grows.

However, business-to-business (B2B) companies and some business-to-consumer (B2C) companies often have large order sizes. Therefore, it can be time consuming to wait for the pricing engine to recalculate after each item is added to the cart. Moreover, for large orders, it usually isn't very important that the exact price and discount be shown every time that an item is added to the cart. It's more important that users be able to add items quickly. The capability to delay exact price and discount calculation until a user requests it or an order is finalized can significantly improve performance. It can also reduce the time that is required to finish placing an order.

The capability to delay exact price and discount calculation has long been available in POS. As of the Commerce version 10.0.22 release, it's also available for call center.

## Enable delayed price and discount calculation for POS

To enable delayed price and discount calculation for POS, follow these steps.

1. In Commerce headquarters, go to the functionality profile that is associated with the physical store.
1. On the **Amount** FastTab, enable the **Manually calculate multiple item discounts** configuration.
1. Open the screen layout designer for the registers where the delayed calculation should be enabled.
1. Add a button for the **Calculate total** operation to the desired button grid.
1. Run the **1070** and **1090** jobs.

Now, when items are added to a transaction, multiline discounts aren't calculated unless the cashier selects the **Calculate total** button. After **Calculate total** is selected for a transaction, multiline discounts will always be calculated for it. The cashier won't have to select the button again, even if additional items are added to the cart. The system won't allow the cashier to capture payment until **Calculate total** is selected.

## Enable delayed price and discount calculation for call center

To enable delayed price and discount calculation for call center, follow these steps.

1. In Commerce headquarters, go to **Workspaces \> Feature management**.
1. Enable the **Prevent unintentional price calculation for commerce order** feature. This feature is a prerequisite for the delayed price and discount calculation capability.

    > [!NOTE]
    > For new deployments, the **Prevent unintentional price calculation for commerce order** feature is enabled by default.

1. Go to **Commerce parameters \> Prices and discounts**.
1. In the **Miscellaneous** section, enable the **Manually calculate multi-line prices and discounts** configuration.

Now, when a sales order or sales quotation is created or edited in the call center, the exact price and discount calculation for it will be delayed. The pricing engine will consider only the sales line that is being added or edited, and will ignore all other sales lines. The net amount for an item includes the price calculation and simple discounts (discount percentage or amount off on an individual item). However, mix and match, threshold, and quantity discounts won't be applied. Call center users who want to view the exact price, including all discounts, can select one of three buttons: **Recalculate**, **Totals**, or **Complete**.

> [!NOTE]
> For call center orders, the system shows a warning message to remind the user that they must select the **Recalculate**, **Totals**, or **Complete** button for the exact price and discount calculation to be done. For orders where the **Complete** button is available, there is no way for the call center user to omit the exact price and discount calculation, because they must select **Complete** to complete the order capture. For orders where the **Complete** button isn't available, there is no action that indicates completion of the order capture. Therefore, the call center user is responsible for selecting either **Recalculate** or **Totals** before they complete the order capture.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
