---
# required metadata

title: Delay exact price and discount calculation
description: This topic describes the delayed price calculation capability in Microsoft Dynamics 365 Commerce POS and call center.
author: boycezhu
ms.date: 09/09/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: boycez
ms.search.validFrom: 2017-06-20
---

# Delay exact price calculation for improved performance
  
[!include [banner](includes/banner.md)]

This topic describes the delayed price calculation capability in Microsoft Dynamics 365 Commerce point of sale (POS) and call center.

Dynamics 365 Commerce supports the creation of multiline discounts such as mix and match, threshold, and quantity discounts that are applied when more than one sales line of a sales order or sales quote are combined together. Whenever a new line is added to an order, the Commerce pricing engine evaluates the entire cart to detect if any of these multiline discounts can be applied. A result of this is that as a sales order grows, adding a new line to the order slows order processing. 

It is very common for business-to-business (B2B) companies and some business-to-consumer (B2C) companies to have large order sizes and thus the order taking gets more time consuming for such orders. However, for such large orders usually it is more important to enable the user to add the items quickly rather than showing the exact price and discount for the order after each item is added to the cart. But, the user should be allowed to view the exact total whenever they want or before finalizing the order. The capability for delaying the exact price and discount calculation has been available in POS for many years, but with 10.0.22 release, we have made it available for call center as well.

## Enable delayed price and discount calculation for POS

To enable delayed price and discount calculation in POS, follow these steps.

1. In Commerce headquarters, go to the functionality profile associated with the physical store.
1. Select the "**Amount**" FastTab to expand it.
1. Enable the **Manually calculate multiple item discounts** configuration.
1. Open the screen layout designer for the registers where the delayed calculation should be enabled.
1. Add a button for the **Calculate total** operation to the desired button grid.
1. Run the **1070** and **1090** jobs.

With the setup above, multiline discounts are not calculated when items are added to the transaction unless the cashier selects the **Calculate total** button. The system will not allow the cashier to capture payment until the **Calculate total** button is selected. However, once the **Calculate total** button is selected for a transaction, multiline discounts will always be calculated for that transaction and the cashier will not need to select it again even if additional items are added to the cart.

## Enable delayed price and discount calculation for call center

To enable delayed price and discount calculation in call center, follow these steps.

1. In Commerce headquarters, go to **Workspaces \> Feature management**.
1. Enable the **Prevent unintentional price calculation for commerce order** feature. This is a prerequisite for enabling the delayed price and discount calculation feature. 
    > [!NOTE]
    > This feature is enabled by default for new deployments.
1. Go to **Commerce parameters \> Prices and discounts \> Miscellaneous** and enable the **Manually calculate multi-line prices and discounts** configuration.

Once the **Prevent unintentional price calculation for commerce order** feature is enabled, the exact price and discount calculation for the sales order and sales quote being created or edited in the call center will be delayed. The pricing engine will only consider the sales line that is being added or edited and will ignore other sales lines. The net amount for an item will include the price calculation and simple discounts (discount percentage or amount off on an individual item) but mix and match, threshold, and quantity discounts will not be applied. When call center users want to view the exact price including all discounts, they can select one of the three buttons: **Recalculate**, **Totals**, or **Complete**. 

> [!NOTE]
> For call center orders, the system displays a warning message indicating that the user must remember to select the **Recalculate**, **Totals**, or **Complete** button for exact price and discount calculation. For orders where the **Complete** button is displayed, there is no way for the users to miss calculating the exact price and discount because the **Complete** button must be selected to complete the order capture. For orders where the **Complete** button is not available, there is no action that indicates the completion of the order capture, so it is the responsibility of the call center user to select either the **Recalculate** or **Totals** button before completing the order capture.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
