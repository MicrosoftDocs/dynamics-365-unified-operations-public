---
# required metadata

title: Delay exact price and discount calculation
description: This topic describes the delayed price calculation capability available in Microsoft Dynamics 365 Commerce POS and call center.
author: boycezhu
ms.date: 09/09/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: boycez
ms.search.validFrom: 2017-06-20
---

# Delay exact price and calculation for improved performance
  
[!include [banner](includes/banner.md)]

This topic describes the delayed price calculation capability available in Microsoft Dynamics 365 Commerce point of sale (POS) and call center.

Dynamics 365 Commerce supports the creation of multiline discounts such as mix and match, threshold, and quantity discounts that are applied when more than one sales line of a sales order or sales quote are combined. Whenever a new line is added to an order, the Commerce pricing engine evaluates the entire cart to detect if any of these multiline discounts can be applied. A result of this recalculation is that as a sales order grows, adding a new line to that order can impact performance. 

It is common for business-to-business (B2B) and some business-to-consumer (B2C) companies to have large order sizes, and waiting for the pricing engine to recalculate after each item is added to the cart can be time consuming. However, for such large orders it is usually more important to allow users to add items quickly rather than show the exact price and discount for the order each time an item is added to the cart. The capability to delay exact price and discount calculation until a user requests it or an order is finalized can significantly improve performance and reduce the time needed to complete the placement of an order.

The capability for delaying exact price and discount calculation has long been available in POS, and as of the Commerce version 10.0.22 release it is available for call center as well.

## Enable delayed price and discount calculation for POS

To enable delayed price and discount calculation in POS, follow these steps.

1. In Commerce headquarters, go to the functionality profile associated with the physical store.
1. Select the "**Amount**" FastTab to expand it.
1. Enable the **Manually calculate multiple item discounts** configuration.
1. Open the screen layout designer for the registers where the delayed calculation should be enabled.
1. Add a button for the **Calculate total** operation to the desired button grid.
1. Run the **1070** and **1090** jobs.

With the setup above, multiline discounts are not calculated when items are added to the transaction unless the cashier selects the **Calculate total** button. Once the **Calculate total** button is selected for a transaction, multiline discounts will always be calculated for that transaction and the cashier will not need to select it again even if additional items are added to the cart. The system will not allow the cashier to capture payment until the **Calculate total** button is selected.

## Enable delayed price and discount calculation for call center

To enable delayed price and discount calculation in call center, follow these steps.

1. In Commerce headquarters, go to **Workspaces \> Feature management**.
1. Enable the **Prevent unintentional price calculation for commerce order** feature. This is a prerequisite for enabling the delayed price and discount calculation capability. 
    > [!NOTE]
    > This feature is enabled by default for new deployments.
1. Go to **Commerce parameters \> Prices and discounts \>. 
1. In the **Miscellaneous** section, enable the **Manually calculate multi-line prices and discounts** configuration.

Once the delayed price and discount calculation capability is enabled, the exact price and discount calculation for the sales order and sales quote being created or edited in the call center will be delayed. The pricing engine will only consider the sales line that is being added or edited and will ignore other sales lines. The net amount for an item includes the price calculation and simple discounts (discount percentage or amount off on an individual item) but mix and match, threshold, and quantity discounts will not be applied. When call center users want to view the exact price including all discounts, they can select one of three buttons: **Recalculate**, **Totals**, or **Complete**. 

> [!NOTE]
> For call center orders, the system displays a warning message indicating that the user must remember to select either the **Recalculate**, **Totals**, or **Complete** button for exact price and discount calculation. For orders where the **Complete** button is displayed, there is no way for users to miss calculating the exact price and discount because the **Complete** button must be selected to complete the order capture. For orders where the **Complete** button is not available, there is no action that indicates the completion of the order capture, so it is the responsibility of the call center user to select either the **Recalculate** or **Totals** button before completing the order capture.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
