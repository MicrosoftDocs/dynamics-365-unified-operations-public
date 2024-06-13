---
title: Check out faster with optimized payment flows
description: This article provides an overview of modernizing updates to point of sale payment flows in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 06/13/2024
ms.topic: overview
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: v-chrgriffin
ms.search.validFrom: 2024-06-07
ms.custom: 
  - bap-template
---

# Check out faster with optimized payment flows

[!include [banner](../includes/banner.md)]

This article provides an overview of modernizing updates to point of sale (POS) payment flows in Microsoft Dynamics 365 Commerce.

The Dynamics 365 Commerce team is modernizing the POS user interface (UI) by transitioning to the React UI framework, which brings fluid and efficient user flows that seamlessly work across browsers and applications. The first stage of this transition updates some of the most frequently used operations, payment flows. This change updates traditional POS payment flows, which require multiple window prompts and clicks, and repackages the process flows into a single-pane action window for efficiency. Actions are concentrated in a repetitive-use active area within the screen, while also offering configuration options to bypass specific screens to directly get to the actions required for common scenarios.

## Prerequisites

To transition to the upgraded payments flow experience, the following prerequisites must be met:
- You must be running Commerce version 10.0.40.
- You must enable the **Enable unified payments experience in POS** feature in the Commerce headquarters **Feature management** workspace (**System administration \> Workspaces \> Feature management**). 

## Feature availability

The **Enabled unified payments experience in POS** feature management flag is available for use in Commerce version 10.0.40. These changes apply the modernized UI experience for the **Credit Card**, **Cash**, and **Check** payment methods. The payment method options window also reflects updated payment method symbols for all payment methods in the menu.

Updates for the **Currency**, **Customer Account**, **Payment Voucher**, **Gift Card**, and **Loyalty Card** payment methods will be rolled out in a future release. 

> [!WARNING]
> The ability to customize the new React components will be delivered in a future Commerce feature. Currently, the availability date hasn't been set. Any customizations done to the payment user flow screens will require Commerce to release React extensibility capabilities to enable you to continue customizing actions within these screens.

## Pay card

The new **Pay Card** payment flow displays the transaction amount due, along with **Swipe card** and **Enter manually** input methods. 
    - **Swipe card** directs the payment action to the payment terminal to receive input directly from the terminal.
    - **Enter manually** directs the payment action to the payment terminal for the customer or sales associate to input the card number manually into the terminal, which is useful if a chip or magnetic stripe on a customer's card is unreadable.

The **Payment amount** screen is then presented to allow for any subamount entry if the customer wishes to pay a different amount than the preset transaction total. 

New symbols also display within the payment pane to show the sales associate what is occurring on the terminal. The terminal presents a symbol to show that it's prompting the customer to insert or swipe their card. A payment processing loader is also displayed as the terminal processes the transaction against the payment gateway. If the transaction is successful, the resulting screen shows the change due, or the user is returned to the transaction screen for next steps if a subamount was paid. Any payment errors encountered during processing are also displayed directly in the new payments pane.

## Pay cash

The **Pay Cash** flow displays the new **Pay with cash** pane. This pane allows for direct entry of the cash amount the customer is paying, and also displays buttons for the store's configured currency denominations. These cash denomination buttons can be used to enter the matching cash amount that customers pay.

### Smart denominations

Commerce is introducing *smart denominations* in POS with this UI update. Smart denominations present the sales associate with logical cash denominations, or paired denomination totals in the closest configured increments that a customer is likely to pay if using cash. 

#### Configure smart denominations

To configure smart denominations, navigate to the store's **POS functionality profiles** screen in headquarters for the register you're configuring. In the **Functions** section, set the **Use quick pay shortcuts** option to **Yes**. 

Next, go to your store in headquarters at **Retail and Commerce \> Channels \> Stores** and within the **Set up** pane, select **Cash declaration**. On the **Cash declaration denominations** screen, select **Edit** to unlock edits for the settings and use the **Include in quick pay shortcuts** column checkbox to include all denominations to use for smart denomination groupings. The smart denominations logic uses the selected items to group logical totaling amounts for the transaction total, including the denomination selected. Smaller denominations (like a 0.01 to 2.00 currency selection) use the grouping option sections with these lower amount pairings, potentially crowding out options commonly used by customers in midrange notes or coins. Depending on the average transaction totals in your store and the common currency carried by customers in the store's location, enabling a subset of currency lines provides the sales associate with the best balanced smart denominations options during the pay cash checkout experience.

After your **Include in quick pay shortcuts** denomination lines are selected, select **Save**. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule** and select **Run now** to run the **1070 (Channel configuration)** and **1090 (Registers)** jobs.

## Pay exact

Commerce is also introducing *pay exact* functionality, which can save time at checkout by directing POS straight to the payment action result needed. In Commerce version 10.0.40, **Pay Exact** can be applied to the **Pay Cash** and **Pay Card** actions. For **Pay Cash** pay exact functionality, selecting a pay cash exact payment action button completes the transaction using exact change of the transaction total (bringing the sales associate directly to the change due with no change pane). For **Pay Card** pay exact functionality, the pane bypasses the **Swipe Card** and **Enter Manually** pane and the subtotal amount entry pane, taking the transaction directly to the payment terminal for customer payment. These actions bypass multiple entry screens, resulting in faster checkouts at the terminal.

Pay exact functionality is configured in the button grid menus for the corresponding payment action POS buttons. To configure a button for pay exact functionality, in headquarters go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Button grids**. To launch the button grid designer, select the targeted payment action button grid ID, and then select **Designer**. Once the button grid designer is authenticated and launched, create a new button, or right-click on an existing button you want to reconfigure to use for pay exact functionality. 

- For cash, you can either set the button's action to a **Pay cash quick** action, or set it to **Pay cash** and select the corresponding **Is pay exact** checkbox. For both these options, you must use the **Cash** payment type. 
- For card, select the **Is pay exact** for a button with the **Pay card** action and the **Cards** payment type set. This button now operates with the pay exact functionality when pressed.

Microsoft recommends that you update the button's **Button text** field in the **Appearance** section of the button grid properties to clearly indicate to a sales associate that the button is a pay exact button for the payment method used.

Select **OK** to set the change for the button property being updated. When done configuring your buttons, close the button designer to apply the changes. Then go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule** and select **Run now** to run the **1070 (Channel configuration)** and **1090 (Registers)** jobs.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
