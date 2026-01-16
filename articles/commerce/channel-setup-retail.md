---
title: Set up a retail  channel
description: Learn how to create a new retail channel in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 01/16/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-20
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Set up a retail channel

[!include [banner](includes/banner.md)]

This article describes how to create a new retail channel in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce supports multiple retail channels. These retail channels include online stores, call centers, and retail stores (also known as brick-and-mortar stores). Each retail store channel can have its own payment methods, price groups, point of sale (POS) registers, income accounts and expense accounts, and staff. You must set up all these elements before you can create a retail store channel. 

Before you create a retail channel, make sure you follow the [channel prerequisites](channels-prerequisites.md).

## Create and configure a new retail channel

To create and configure a new retail channel, follow these steps:

1. In the navigation pane, go to **Modules \> Retail and Commerce \> Channels \> Stores \> All stores**.
1. On the action pane, select **New**.
1. In the **Name** field, enter a name for the new channel.
1. In the **Store number** field, enter a unique store number. The number can be alphanumeric with a maximum of 10 characters.
1. In the **Legal entity** drop-down list, select the appropriate legal entity.
1. In the **Warehouse** drop-down list, select the appropriate warehouse.
1. In the **Store time zone** field, select the appropriate time zone.
1. In the **Sales tax group** drop-down list, select an appropriate sales tax group for the store.
1. In the **Currency** field, select the appropriate currency.
1. In the **Customer address book** field, enter a valid address book.
1. In the **Default customer** field, enter a valid default customer.
1. In the **Functionality profile** field, select a functionality profile if applicable.
1. In the **Email notification profile** field, enter a valid email notification profile.
1. On the action pane, select **Save**.

The following image shows the creation of a new retail channel.

:::image type="content" source="media/channel-setup-retail-1.png" alt-text="Screenshot of the creation of a new retail channel.":::

The following image shows an example retail channel.

:::image type="content" source="media/channel-setup-retail-2.png" alt-text="Screenshot of an example retail channel.":::

## Other settings

You can set many other optional settings in the **Statement/closing** and **Miscellaneous** sections, based on the needs of the retail store.

For information about setting up the default screen layout in the **Screen layout** section, see [Screen layouts for the point of sale (POS)](pos-screen-layouts.md). For setup information about the **Hardware stations** section, see [Configure and install Retail hardware station](dev-itpro/retail-hardware-station-configuration-installation.md).

The following image shows an example retail channel setup configuration.

:::image type="content" source="media/channel-setup-retail-3.png" alt-text="Screenshot of an example retail channel configuration.":::

## Additional channel set up

You need to set up additional items for a channel. You can find these items on the Action Pane under the **Set up** section.

Additional tasks that are required for online channel setup include setting up payment methods, cash declaration, modes of delivery, income and expense account, sections, the fulfillment group assignment, and safes.

The following image shows various other retail channel setup options on the **Set up** tab.

:::image type="content" source="media/channel-setup-retail-4.png" alt-text="Screenshot of the Set up channel options.":::

### Set up payment methods

To set up payment methods, for each payment type that the channel supports, follow these steps:

1. On the Action Pane, select the **Set Up** tab, and then select **Payment methods**.
1. On the action pane, select **New**.
1. In the navigation pane, select a payment method.
1. In the **General** section, enter an **Operation name** and configure any other settings.
1. Configure any other settings as required for the payment type.
1. On the action pane, select **Save**.

The following image shows an example of a cash payment method.

:::image type="content" source="media/channel-setup-retail-5.png" alt-text="Screenshot of an example payment methods configuration.":::

The following image shows an example of a cash payment method and the **Amount** tab configuration.

:::image type="content" source="media/payment-methods-recount.png" alt-text="Screenshot of an example payment method setup for amounts.":::

> [!NOTE]
> The Retail Server caches values for the **Amount** tab. These values don't take effect immediately after you run the Distribution Schedule jobs. To immediately apply these values for testing, you might need to restart the Cloud Scale Unit.

### Set up cash declaration

1. On the Action Pane, select the **Set Up** tab, and then select **Cash declaration**.
1. On the Action Pane, select **New**, and then create all **Coin** and **Note** denominations that apply.

The following image shows an example of a cash declaration.

:::image type="content" source="media/channel-setup-retail-6.png" alt-text="Screenshot of setting up cash declarations.":::

### Set up modes of delivery

You can see the configured modes of delivery by selecting **Modes of delivery** from the **Set up** tab on the Action Pane.  

To change or add a mode of delivery, follow these steps:

1. In the navigation pane, go to **Modules \> Inventory management \> Modes of delivery**.
1. On the Action Pane, select **New** to create a new mode of delivery, or select an existing mode.
1. In the **Retail channels** section, select **Add line** to add the channel. Adding channels by using organization nodes instead of adding each channel individually can streamline adding channels.

The following image shows an example of a mode of delivery.

:::image type="content" source="media/channel-setup-retail-7.png" alt-text="Screenshot of setting up modes of delivery.":::

### Set up income/expense account

To set up an income/expense account, follow these steps:

1. On the Action Pane, select the **Set Up** tab, and then select **Income/Expense account**.
1. On the action pane, select **New**.
1. Under **Name**, enter a name.
1. Under **Search name**, enter a search name.
1. Under **Account type**, enter the account type.
1. Enter text for **Message line 1**, **Message line 2**, **Slip text 1**, and **Slip text 2** as needed.
1. Under **Posting**, enter posting information.
1. On the action pane, select **Save**.

The following image shows an example of an income/expense account.

:::image type="content" source="media/channel-setup-retail-8.png" alt-text="Screenshot of setting up income/expense accounts.":::

### Set up sections

To set up sections, follow these steps:

1. On the Action Pane, select the **Set Up** tab, and then select **Sections**.
1. On the action pane, select **New**.
1. Under **Section number**, enter a section number.
1. Under **Description**, enter a description.
1. Under **Section size**, enter a section size.
1. Configure other settings for **General** and **Sales statistics** as needed.
1. On the action pane, select **Save**.

### Set up a fulfillment group assignment

To set up a fulfillment group assignment, follow these steps:

1. On the Action Pane, select the **Set up** tab, and then select **Fulfillment group assignment**.
1. On the action pane, select **New**.
1. In the **Fulfillment group** drop-down list, select a fulfillment group.
1. In the **Description** drop-down list, enter a description.
1. On the Action Pane, select **Save**.

The following image shows an example of a fulfillment group assignment setup.

:::image type="content" source="media/channel-setup-retail-9.png" alt-text="Screenshot of setting up fulfillment group assignments.":::

### Set up safes

To set up safes, follow these steps:

1. On the Action Pane, select the **Set Up** tab, and then select **Safes**.
1. On the action pane, select **New**.
1. Enter a name for the safe.
1. On the action pane, select **Save**.

### Ensure unique transaction IDs

The point of sale (POS) generates transaction IDs that are sequential and include the following parts:

- A fixed part, which concatenates the store ID and terminal ID. 
- A sequential part, which is a number sequence. 

Because the system generates transaction IDs in both offline and online modes, duplicate transaction IDs can occur. Eliminating duplicate transaction IDs can require a significant amount of manual data fixing. 

To prevent duplicate transaction IDs, the system introduces a new transaction ID format that uses a 13-digit number generated by calculating the time in milliseconds since 1970. This new format makes transaction IDs nonsequential and ensures that they're always unique.

The new transaction ID format is `<store ID>-<terminal ID>-<milliseconds since 1970>`. You can enable the new transaction ID format feature from the **Feature management** workspace in Commerce headquarters. 

> [!NOTE]
> - Use transaction IDs for internal system use only, so they don't need to be sequential. However, many countries/regions require receipt IDs to be sequential, so check your organization's requirements before enabling the new transaction ID format feature.
> - After you enable the new transaction ID format feature, you can't disable this feature in headquarters.
> - The new transaction ID format feature is enabled by default starting with Commerce version 10.0.41.

To enable the new transaction ID format, follow these steps:

1. In headquarters, go to **System administration \> Workspaces \> Feature management**.
1. Filter for the "retail and commerce" module.
1. Search for the **Enable new transaction id to avoid duplicate transaction ids** feature name.
1. Select the feature, and then in the right pane, select **Enable Now**.  
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Run the **1070 Channel configuration** and **1170 POS task recorder** jobs to synchronize the enabled feature to the stores.
1. After the changes are sent to the stores, close and reopen the POS terminals to use the new transaction ID format. 

### Set up store location for store selector

Store location data, including latitude and longitude, is used in store selector scenarios in both POS and e-commerce sites.

To set up the store location in Commerce headquarters, follow these steps:

1. Go to **Organization administrator \> Organizations \> Operating units**.
1. In the left navigation pane, filter the operating unit by name or the operating unit number of the channel, and then select it.
1. On the **Addresses** FastTab, select **More options \> Advanced** to access the **Manage addresses** form.
1. On the **General** tab, enter the applicable values for **Latitude** and **Longitude**.
1. On the Action Pane, select **Save**.

## Additional resources

[Channels overview](channels-overview.md)

[Channel setup prerequisites](channels-prerequisites.md)

[Set up an online channel](channel-setup-online.md)

[Set up a call center channel](channel-setup-callcenter.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
