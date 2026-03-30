---
title: Set up an online channel
description: Learn how to create a new online channel in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 01/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-20
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Set up an online channel

[!include [banner](includes/banner.md)]

This article describes how to create a new online channel in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce supports multiple retail channels. These retail channels include online stores, call centers, and retail stores (also known as brick-and-mortar stores). Online stores give customers the option of purchasing products from the retailer's online store in addition to its retail stores.

To create an online store in Commerce, you must first create an online channel. Before you create a new online channel, make sure that you complete the [Channel set up prerequisites](channels-prerequisites.md).

Before you can create a new site, you must create at least one online store in Commerce. For more information, see [Create an e-commerce site](create-ecommerce-site.md).

## Create and configure a new online channel

To create and configure a new online channel, follow these steps:

1. In the navigation pane, go to **Modules \> Channels \> Online Stores**.
1. On the action pane, select **New**.
1. In the **Name** field, enter a name for the new channel.
1. In the **Legal entity** drop-down, select the appropriate legal entity.
1. In the **Warehouse** drop-down, select the appropriate warehouse.
1. In the **Store time zone** field, select the appropriate time zone.
1. In the **Currency** field, select the appropriate currency.
1. In the **Default customer** field, enter a valid default customer.
1. In the **Customer address book** field, enter a valid address book.
1. In the **Functionality profile** field, select a functionality profile if applicable.
1. In the **Email notification profile** field, enter a valid email notification profile.
1. On the action pane, select **Save**.

The following image shows the creation of a new online channel.

:::image type="content" source="media/channel-setup-online-1.png" alt-text="Screenshot of the creation of a new online channel.":::

The following image shows an example online channel.

:::image type="content" source="media/channel-setup-online-2.png" alt-text="Screenshot of an example online channel.":::

> [!NOTE]
> Be cautious about changing the warehouse for a running online channel. E-commerce site carts that aren't yet checked out (unless you modify them) still fulfill from the old warehouse. This situation affects the inventory availability calculation.

## Assign the channel to a Commerce Scale Unit

Assign your new channel to a Commerce Scale Unit. For instructions, see [Configure channels to use Commerce Scale Unit](../fin-ops-core/dev-itpro/deployment/initialize-retail-channels.md#configure-channels-to-use-csu).

## Set up languages

If your e-commerce site supports multiple languages, expand the **Languages** section, and add extra languages as needed.

## Set up payment account

In the **Payment account** section, add a payment provider. For information on setting up an Adyen payment connector, see [Dynamics 365 Payment Connector for Adyen](./dev-itpro/adyen-connector.md).

## Additional channel setup

Additional tasks that are required for online channel setup include setting up payment methods, modes of delivery, and the fulfillment group assignment.

The following image shows **Modes of delivery**, **Payment methods**, and **Fulfillment group assignment** setup options on the **Set up** tab.

:::image type="content" source="media/channel-setup-online-3.png" alt-text="Screenshot of additional online channel setup actions.":::

### Set up payment methods

To set up payment methods, follow these steps for each payment type that the channel supports:

1. On the action pane, select the **Set Up** tab, and then select **Payment methods**.
1. On the action pane, select **New**.
1. In the navigation pane, select the payment method you want.
1. In the **General** section, enter an **Operation name** and configure any other settings you want.
1. Configure any other settings required for the payment type.
1. On the action pane, select **Save**.

The following image shows an example of a cash payment method.

:::image type="content" source="media/channel-setup-retail-5.png" alt-text="Screenshot of an example payment methods configuration.":::

### Set up modes of delivery

You can see the configured modes of delivery by selecting **Modes of delivery** from the **Set up** tab on the action pane.

To change or add a mode of delivery, follow these steps:

1. In the navigation pane, go to **Modules \> Inventory management \> Modes of delivery**.
1. On the action pane, select **New** to create a new mode of delivery, or select an existing mode.
1. In the **Retail channels** section, select **Add line** to add the channel. Adding channels by using organization nodes instead of adding each channel individually can streamline adding channels.

The following image shows an example of a mode of delivery.

:::image type="content" source="media/channel-setup-retail-7.png" alt-text="Screenshot of setting up modes of delivery.":::

### Set up a fulfillment group assignment

To set up a fulfillment group assignment, follow these steps:

1. On the action pane, select the **Set up** tab, and then select **Fulfillment group assignment**.
1. On the action pane, select **New**.
1. In the **Fulfillment group** drop-down list, select a fulfillment group.
1. In the **Description** drop-down list, enter a description.
1. On the action pane, select **Save**.

The following image shows an example of a fulfillment group assignment setup.

:::image type="content" source="media/channel-setup-retail-9.png" alt-text="Screenshot of setting up a fulfillment group assignment.":::

## Additional resources

[Channels overview](channels-overview.md)

[Channel setup prerequisites](channels-prerequisites.md)

[Set up a retail channel](channel-setup-retail.md)

[Set up a call center channel](channel-setup-callcenter.md)

[Dynamics 365 Payment Connector for Adyen](./dev-itpro/adyen-connector.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
