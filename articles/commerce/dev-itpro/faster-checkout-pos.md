---
title: Check out faster with optimized payment flows
description: This article provides an overview of modernizing updates to point of sale (POS) payment flows in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 05/16/2025
ms.topic: overview
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

The Dynamics 365 Commerce team is modernizing the POS user interface (UI) by transitioning to the React UI framework. The React UI framework brings fluid and efficient user flows that seamlessly work across browsers and applications. The first stage of the transition updates some of the most frequently used operations: payment flows. Traditional POS payment flows require multiple window prompts and mouse clicks. This update repackages the process flows into a single-pane action window for improved efficiency. Actions are concentrated in a repetitive-use active area on the screen. In addition, configuration options let users bypass specific screens and go directly to the actions that are required for common scenarios.

## Prerequisites

Before you can transition to the upgraded payment flow experience, the following prerequisites must be met:

- You must be running Commerce version 10.0.40 or later.
- You must enable the **Enable unified payments experience in POS** feature in the Commerce headquarters **Feature management** workspace (**System administration** \> **Workspaces** \> **Feature management**).
- The new payment experiences are enabled by default for all stores. To enable administrators to try the new payment experience only in pilot stores, starting in Commerce version 10.0.44 administrators can turn on the **Disable the unified payments experience** setting from **POS functionality profiles**. When the **Disable the unified payments experience** setting is turned on, the new payment experience is only enabled for stores that have this setting turned off. Once administrators are satisfied with the new payment experiences, they can turn off this configuration for all the stores to enable the new payment experiences for all stores.

## Feature availability

The modernized UI experience for the **Credit Card**, **Cash**, and **Check** payment methods is available starting with Commerce version 10.0.40, while the new experience for the **Currency**, **Customer Account**, **Payment Voucher**, and **Gift Card** payment methods are available starting with Commerce version 10.0.42. The **Pay by Loyalty** experience is available starting with Commerce version 10.0.44. The payment method options dialog shows updated payment method symbols for all payment methods on the menu. 

> [!NOTE]
> If you've customized the payment experiences for the **Currency**, **Customer Account**, **Payment Voucher**, and **Gift Card** payment methods and want to continue using those user experiences, you don't need to disable the feature flag. You should instead contact Microsoft support to disable the new user experiences for these individual payment methods while still benefiting from the additional functionality provided by the other payment methods.

> [!WARNING]
> The ability to customize the new React components will be delivered in a future Commerce feature. Currently, the availability date hasn't been set. For any customization that you do on the payment user flow screens, Commerce must release React extensibility capabilities. Otherwise, you can't continue to customize actions on those screens.

Apart from unifying the various payment experiences, the following sections describe some of the additional capabilities that the new payment experiences enable.

## Pay card

The new **Pay Card** payment flow shows the transaction amount that is due and the **Swipe card** and **Enter manually** input methods, as shown in the following example image.

- **Swipe card** directs the payment action to the payment terminal, so that input can be received directly from the terminal.
- **Enter manually** directs the payment action to the payment terminal, so that the customer or sales associate can manually enter the card number at the terminal. This method is useful if the chip or magnetic stripe on a customer's card is unreadable.

:::image type="content" source="../media/PayCards2.png" alt-text="Pay with card flyout showing the Swipe card and Enter manually input methods.":::

The **Payment amount** screen is then presented. This screen allows for subamount entry if the customer wants to pay a different amount than the preset transaction total. 

New symbols appear in the payment pane to show the sales associate what is occurring on the terminal, as shown in the following example image. The terminal presents a symbol to show that it's prompting the customer to insert or swipe their card. A payment processing loader is also shown while the terminal processes the transaction against the payment gateway.

:::image type="content" source="../media/newPayUX1.png" alt-text="Pay flyout showing new symbols for payment methods.":::

If the transaction is successful, the resulting screen shows the change that is due. Alternatively, if a subamount was paid, the user is returned to the transaction screen for next steps. Any payment errors that are encountered during processing are shown directly in the new payments pane.

## Pay cash

The **Pay Cash** payment flow shows the new **Pay with cash** pane. This pane allows for direct entry of the cash amount that the customer is paying. It also shows buttons for the store's configured currency denominations. These cash denomination buttons can be used to enter the matching cash amount that customers pay.

### Smart denominations

In this UI update, Commerce is introducing *smart denominations* in POS. Smart denominations present the sales associate with logical cash denominations, or paired denomination totals in the closest configured increments that a customer is likely to pay if they're using cash. 

#### Configure smart denominations

To configure smart denominations, in headquarters, go to the store's **POS functionality profiles** screen for the register that you're configuring. In the **Functions** section, set the **Use quick pay shortcuts** option to **Yes**. 

Next, in headquarters, go to your store at **Retail and Commerce** \> **Channels** \> **Stores**. In the **Set up** pane, select **Cash declaration**. On the **Cash declaration denominations** screen, select **Edit** to unlock edits for the settings. Then use the **Include in quick pay shortcuts** column checkbox to include all denominations that you want to use for smart denomination groupings. The smart denominations logic uses the selected items to group logical totaling amounts for the transaction total, including the selected denomination. Smaller denominations (such as a 0.01 to 2.00 currency selection) use the grouping option sections with these lower amount pairings and might crowd out options that customers commonly use in midrange notes or coins. Depending on the average transaction totals in your store and the currency that customers in the store's location commonly carry, enabling a subset of currency lines gives sales associates the best-balanced smart denomination options during the pay cash checkout experience.

After you finish selecting your **Include in quick pay shortcuts** denomination lines, select **Save**. Then go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**, and select **Run now** to run the **1070 (Channel configuration)** and **1090 (Registers)** jobs.

## Pay exact

Commerce is also introducing *pay exact* functionality, which can save time at checkout by directing POS straight to the required payment action result. In Commerce version 10.0.40, pay exact functionality can be applied to the **Pay Cash** and **Pay Card** actions. For **Pay Cash** pay exact functionality, selecting a pay cash exact payment action button completes the transaction by using exact change of the transaction total (the sales associate is taken directly to the change due with no change pane). For **Pay Card** pay exact functionality, the pane bypasses the **Swipe Card** and **Enter Manually** panes and the subtotal amount entry pane. Instead, the transaction is taken directly to the payment terminal for customer payment. Because these actions bypass multiple entry screens, checkout is faster at the terminal.

Pay exact functionality is configured in the button grid menus for the corresponding payment action POS buttons. To configure a button for pay exact functionality, in headquarters, go to **Retail and Commerce** \> **Channel setup** \> **POS setup** \> **POS** \> **Button grids**. To open the button grid designer, select the ID of the targeted payment action button grid, and then select **Designer**. After the button grid designer is authenticated and opened, create a new button. Alternatively, select and hold (or right-click) an existing button that you want to reconfigure for pay exact functionality. 

- For cash, you can either set the button's action to a **Pay cash quick** action, or set it to **Pay cash** and select the corresponding **Is pay exact** checkbox. In both cases, you must use the **Cash** payment type. 
- For card, select the **Is pay exact** checkbox for a button where the **Pay card** action and the **Cards** payment type are set. The button now works with the pay exact functionality when it's selected.

We recommend that you update the button's **Button text** field in the **Appearance** section of the button grid properties to clearly indicate to the sales associate that the button is a pay exact button for the payment method.

Select **OK** to set the change for the button property that you're updating. When you finish configuring your buttons, close the button designer to apply the changes. Then go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**, and select **Run now** to run the **1070 (Channel configuration)** and **1090 (Registers)** jobs.

## Pay with gift card

The **Pay with gift card** payment flow automatically triggers the balance check to show cashiers the gift card balance information on POS before using the gift card for payment. This action prevents the additional clicks that cashiers usually need to do to help customers determine their gift card balance. 

:::image type="content" source="../media/payUXGiftcard.png" alt-text="Display gift card balance before using the gift card.":::

## Pay with loyalty

The **Pay with loyalty** payment flow allows cashiers to initiate the customer search experience if a customer isn't already added to the transaction, as shown in the following example image. Alternatively, if the customer is added to the transaction, then a cashier can view the loyalty cards associated with the customer. The cashier can either select the associated loyalty cards or scan/type a different loyalty card that the customer wants to use for the payment. This payment flow helps cashiers to efficiently perform all the actions that customers usually ask for after a payment process is started.

:::image type="content" source="../media/PayLoyaltyUX.png" alt-text="Search for a customer from the Pay with loyalty program screen and view the associated loyalty cards.":::



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
