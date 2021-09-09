---
# required metadata

title: Delay exact price and discount calculation
description: This topic describes the delayed price calculation capability in POS and call center.
author: hhaines

ms.date: 9/9/2021
ms.topic: shajain
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.22
---

# Delay exact price calculation for improved performance
[!include [banner](includes/banner.md)]

Dynamics 365 Commerce supports creation of discounts such as Mix and match, Threshold, and Quantity discounts (aka multiline discounts) which are applied when more than one sales line of the sales order or sales quote are combined together. So, whenever a new line is added to the order, the pricing engine evaluates the entire cart to find out if any of these multiline discounts can be applied. Thus, as the sales order grows, adding a new line to the order gets slower. It is very common for B2B companies and some B2C companies to have large order sizes and thus the order taking gets more time consuming for such orders. However, for such large orders, usually it is more important to enable the user to add the items quickly rather than showing the exact price and discount for the order after each item is added to the cart. But, the user should be allowed to view the exact total whenever they want or before finalizing the order. The capability for delaying the exact price and discount calculation has been available in POS for many years, but with 10.0.22 release, we have made it available for call center as well.

**Enable delayed price and discount calculation in POS:**
1. Navigate to the functionality profile associated to the physical store and expand the "**Amount**" fast tab.
1. Enable the configuration "**Manually calculate multiple item discounts**"
1. Open the screen layout designer for the registers where this delayed calculation should be enabled
1. Add a button for "**Calculate total**" operation to the desired button grid
1. Run the **1070** and **1090** jobs

With the above setup, when the items are added to the transaction, then the multiline discounts are not calculated unless the cashier presses the "**Calculate total**" button. The system will not allow the cashier to capture payment unless the cashier presses the above button. However, once this button is pressed for a transaction, then for that transaction, the cashier does not need to press it again even if additional items have been added to the cart. This is because, after this button is pressed, the multiline discounts will always be calculated.

**Enable delayed price and discount calculation in Call center:**

1. Navigate to the Feature management workspace and enable the feature **"Prevent unintentional price calculation for commerce order"**. This is a pre-requisite for enabling the delayed price and discount calculation feature. Note: This feature is enabled by default for new deployments.
1. Navigate to the "**Commerce parameters** -> **Prices and discounts** -> **Miscellaneous**" section and enable the configuration "**Manually calculate multi-line prices and discounts**"

With this feature enabled, the exact price and discount calculation for the sales order and sales quote being created or edited in the call center would be delayed. The pricing engine will only consider the sales line that is being added or edited and will ignore the other sales lines, unless the user presses one of the three buttons i.e. **Recalculate**, **Totals** or **Complete**. This means unless one of these buttons are pressed, the net amount for an item includes the price calculation and simple discounts i.e. discount percentage or amount off on an individual item, but the Mix and match, Threshold and Quantity discounts are not applied. Whenever the users want to view the exact price and discounts, then they can press one of the buttons mentioned above. 

> [!NOTE]
> For call center orders, the system shows a warning message indicating that the user must remember to press one of the above buttons for exact price and discount calculation. For orders where the "Complete" button is displayed, there is no way for the users to miss calculating the exact price and discount as the Complete button must be pressed to complete the order capture. However, for orders where the "Complete" button is not available, there is no action that indicates the completion of the order capture, so it is the responsibility of the user to press one of the above mentioned buttons before finishing the order capture.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
