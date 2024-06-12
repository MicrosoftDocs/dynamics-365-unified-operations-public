---
title: Check out faster with optimized payment flows
description: This article provides an overview of modernizing updates to point of sale payment flows in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 06/12/2024
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

This article provides an overview of modernizing updates to point of sale payment flows in Microsoft Dynamics 365 Commerce.

The Dynamics 365 Commerce team is modernizing the Point-of-Sale (POS) user interface, transitioning to the React UI framework that brings fluid and efficient user flows that seamlessly work across browsers and applications. The first of this transition targets some of the highest used operations- the payment flows. This change updates traditional POS payment flows, which require multiple window prompts and clicks, and repackages the process flows into a single-pane action window for efficiency. Now, actions are concentrated in a repetitive-use active area within the screen, while also offering configuration options to bypass specific screens to get straight to the action required for common scenarios. This article covers the changes available when enabling the new payments flow experience.

## Prerequisites

To set up an environment for nonrecurring payment token usage, the following elements are required:
- Set the **Enable unified payments experience in POS**  to 'Enabled' in **System administration>Workspaces>Feature management**. 

## Changes availability

In Commerce version 10.0.40, enabling the **Enabled unified payments experience in POS** feature management flag is available for use. These changes apply the modernized experience for **Credit Card**, **Cash**, and **Check** payment methods. The payment method options window also reflects updated payment method icons for all payment methods in the menu.

**Currency**, **Customer Account**, **Payment Voucher**, **Gift Card**, and **Loyalty Card** payment method updates will follow in a future release. 

> [!WARNING]
> The ability to customize the new React components will be delivered in a future feature with Commerce. The date for this availability is not yet set. This means that any customizations done specifically in the payment user flow screens will require Commerce to release React extensibility capabilities to enable any customization work to continue your customized actions within these screens.

## Pay card

The new **Pay Card** payment flow will display the transaction amount due along with input methods of "Swipe card" and "Enter manually". 
    - **Swipe card** directs the payment action to the payment terminal to receive input from the terminal directly.
    - **Enter manually** directs the payment action to the payment terminal for the shopper or sales associate to input the card number manually into the terminal (useful if a chip or magnetic stripe on the shopper's card may be failing to be readable.

The "Payment amount" screen is then presented to allow for any subamount entry if the shopper wishes to pay a different amount than the preset transaction total. 

New icons also display within the payment action pane to show the sales associate what is occurring on the terminal. The terminal presents an icon to show it's prompting the shopper to insert or swipe their card. A payment processing loader is also displayed as the terminal processes the transaction against the payment gateway. If successful, the resulting screen will be returned to show change due or return to the transaction screen for next steps if a subamount was paid. Any payment errors will also display directly in the new payments pane if encountered during processing.

## Pay cash

The **Pay Cash** flow will display the new "Pay with cash" action pane. This pane allows for direct entry of the cash amount the shopper is paying. This screen also displays quick buttons for the store's configured currency denominations. These cash denomination buttons can be used to enter the matching cash amount being used to pay by the shopper.

### Smart denominations

Commerce is introducing **Smart Denominations** with this user experience update in POS. Smart denominations present the sales associate with logical cash denominations, or paired denomination totals in the closest configured increments that a shopper is likely to pay if using cash. 

#### Configure smart denominations

To configure smart denominations, navigate to the store's **POS functionality profiles** screen in headquarters which the register you're configuring. Under the **Functions** section, switch the **Use quick pay shortcuts** item to **Yes**. 

Now, navigate to your store in headquarters (found in the **Retail and Commerce > Channels > Stores** list) and within the **Set up** action pane, click on the **Cash declaration** button. Within the **Cash declaration denominations** screen, click "Edit" to unlock edits for the settings and use the **Include in quick pay shortcuts** column checkbox to include all denominations to use for smart denomination groupings. The smart denominations logic will use the selected items to group logical totaling amounts for the transaction total, down to the granularity of denomination selected. Smaller denominations (like a 0.01 to 2.00 currency selection) will use the grouping option sections with these lower amount pairings, potentially crowding out options commonly used by shoppers in mid-range notes or coins. Depending on the average transaction totals in your store and the common currency carried by shoppers in the store's location- enabling a subset of currency lines will provide the best balanced smart denominations options during the pay cash checkout experience for the sales associate.

Once your **Include in quick pay shortcuts** denomination lines are selected, click **Save**. Go to **Retail and Commerce > Retail and Commerce IT > Distribution schedule** and using the **Run now** action button, run the **1070 (Channel configuration)** and **1090 (Registers)** jobs.

## Pay exact

Commerce is also introducing **Pay Exact** functionality that can save time at checkout by directing POS straight to the payment action result needed. In 10.0.40, **Pay Exact** can be applied to the **Pay Cash** and **Pay Card** actions. For **Pay Cash** exact, clicking a pay cash exact payment action button will complete the transaction using exact change of the transaction total (bringing the sales associate directly to the change due with no change pane). For **Pay Card** exact, the action pane will bypass the "Swipe Card" and "Enter Manually" pane and the subtotal amount entry pane- taking the transaction directly to the payment terminal for shopper payment. These actions bypass multiple entry screens, resulting in faster checkouts at the terminal.

Pay exact functionality is configured in the button grid menus for the corresponding payment action POS buttons. To set, navigate to **Retail and Commerce > Channel setup > POS setup > POS > Button grids**. Launch the button grid designer by selecting the targeted payment action button grid ID and clicking **Designer**. Once authenticated and launched, create a new button or right-click on an existing button you wish to configure to use for pay exact functionality. 

- For cash, you have the option to either set the button's Action to a "Pay cash quick" action, or set it to "Pay cash" and check the corresponding **Is pay exact** checkbox. Both these options must use the "Cash" **Payment type**. 
- For card, select the **Is pay exact** for a button with the "Pay card" **Action** and "Cards" **Payment type** set. This button will now operate with the pay exact functionality when pressed.

It's recommended to update the button's **Button text** field under the **Appearance** section of the button grid properties in order to clearly indicate to a sales associate that the button is a pay exact button for the payment method used.

Click **OK** to set the change for the button property being updated. Once finished configuring your buttons, close the button designer to apply the changes. Go to **Retail and Commerce > Retail and Commerce IT > Distribution schedule** and using the **Run now** action button, run the **1070 (Channel configuration)** and **1090 (Registers)** jobs.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
