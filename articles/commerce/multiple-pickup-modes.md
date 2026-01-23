---
title: Enable multiple pickup delivery modes for customer orders
description: Learn about functionality that lets you create customer orders for pickup at a store in Microsoft Dynamics 365 Commerce.
author: hhainesms
ms.date: 01/23/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2019-06-30
---

# Enable multiple pickup delivery modes for customer orders

[!include [banner](includes/banner.md)]

This article explains functionality that lets you create customer orders for pickup at a store in Microsoft Dynamics 365 Commerce.

In Microsoft Dynamics 365 Commerce, organizations can define multiple modes of delivery that shoppers or sales associates can choose from when they create an order that the customer picks up at a store. In this way, organizations can provide multiple pickup options to their shoppers. For example, many retailers now offer shoppers the choice of in-store pickup or curbside pickup for their orders. Commerce supports the configuration of these different pickup delivery modes. Users can take advantage of them when they create customer orders in any supported Commerce channel (e-commerce, call center, or store).

## Enable and configure pickup delivery modes

Make sure the **Support for multiple pickup delivery modes** feature in the **Feature management** workspace in Commerce headquarters is enabled.

If you previously defined a pickup delivery mode on the **Commerce parameters** page, that mode appears in the current configuration for pickup delivery modes.

:::image type="content" source="media/multiplepickupparameter.png" alt-text="Screenshot of pickup delivery modes on the Commerce parameters page.":::

You can define multiple pickup delivery modes on the **Pickup mode of delivery** grid at **Commerce parameters** > **Customer orders** tab > **Modes of delivery** FastTab.  

The **Carry Out mode of delivery** and **Electronic mode of delivery** fields, and the **Show only carrier mode options for ship orders** option, are relocated to this FastTab.

Before you configure additional pickup delivery modes, define the modes of delivery. On the **Modes of delivery** page in Commerce headquarters, add the modes of delivery that you consider pickup delivery modes. Make sure that all configuration is complete. For example, if you're offering curbside pickup as a delivery option for your online shoppers at certain stores, you need to create a new delivery mode for this purpose. You can create this delivery mode using "curbside pickup" as the description. You'll then want to ensure that the "curbside pickup" mode of delivery is mapped to all of the Commerce channels that can offer it, including online stores that might offer this option and the individual store channels that offer this method of fulfillment. You must also link modes of delivery to the products. In this example, if there are certain products that can't be fulfilled using "curbside pickup," make sure that those items are excluded. When you finish adding any new modes of delivery, run the **Process delivery modes** job to create the relationships between the mode of delivery, channels, and items. When the job is completed, open the **Distribution schedule** page in Commerce headquarters, and run the **1120** distribution job to ensure that the relevant Commerce channel databases are updated with your new delivery mode configuration.

:::image type="content" source="media/pickupmodes.png" alt-text="Screenshot of a mode of delivery configuration for curbside pickup.":::

After you define the additional pickup delivery modes, add them to the **Pickup mode of delivery** grid on the **Commerce parameters** page. Then run the appropriate distribution jobs to update the relevant Commerce channel databases with the configuration change.

> [!NOTE]
> Apart from the existing pickup delivery mode that the system copies to the **Pickup mode of delivery** grid when you turn on the **Support for multiple pickup delivery modes** feature, for every additional pickup delivery mode configuration that you create, configure new modes of delivery. When you add modes of delivery to the **Pickup mode of delivery** grid, Commerce validates whether any active open sales lines already use them. If any open sales lines are found, you receive an error message. Modes of delivery aren't considered pickup delivery modes until all open sales lines that use them are closed (either invoiced or canceled).


### E-commerce site configurations

When you turn on the **Support for multiple pickup delivery modes** feature, the following modules on e-commerce pages show the new pickup delivery modes as configured:

- Buy box
- Store selector
- Cart
- Pickup information
- Order confirmation
- Order details

You don't need to take any extra steps on e-commerce pages to make the pickup delivery modes available.

## Work with multiple pickup delivery modes

When multiple pickup delivery modes are available for a channel, customers get an enhanced experience when they shop for products that they want to pick up. 

- In e-commerce channels, shoppers can select any valid pickup delivery mode that's available. For example, a retailer defines two pickup delivery modes (in-store pickup and curbside pickup). Both modes are configured in the **Pickup mode of delivery** grid, and both are valid for the order fulfillment channel and the product that a shopper is currently purchasing. In this case, the shopper can select their preferred pickup delivery mode. The selected pickup delivery mode then becomes the mode of delivery that is linked to the sales order line when the order is created in Commerce headquarters.

    :::image type="content" source="media/pickupecommerce.png" alt-text="Screenshot of selecting a pickup option in e-commerce.":::

- In store channels, if a customer order for pickup is created through the point of sale (POS) application, the sales associate is prompted to choose among the available pickup delivery modes, if any are configured. If only one valid pickup delivery mode is available for the channel and item, the sales associate isn't prompted to select it. Instead, the available pickup delivery mode is automatically applied to the order lines.

    :::image type="content" source="media/pickuppos.png" alt-text="Screenshot of selecting a pickup option in the POS application.":::

- In call center channels, when users create pickup orders, they can manually select any defined pickup delivery mode that is linked to the call center channel. The system then validates that the selected pickup delivery mode can be used when the item that's being linked to it's ordered. When a pickup delivery mode is selected in call center channels, the sales order lines must be linked to a valid store warehouse. If a nonstore warehouse is defined on a call center sales line, a pickup delivery mode can't be set on that sales line.
- Sales associates can use the **Order recall** or **Order fulfillment** operation in the POS application to retrieve a list of orders or order lines for pickup. If a sales associate uses a predefined search filter to show all orders that are picked up at the current store, the queries are modified to ensure that the search results include all eligible orders that use any pickup delivery mode. POS users can also use existing filters to narrow down the list of orders to a specific pickup delivery mode. For example, they can show only orders for curbside pickup.

    :::image type="content" source="media/pickuprecallorder.png" alt-text="Screenshot of filter for pickup delivery modes applied to a list of recall orders.":::

## Considerations for distributed order management

The [distributed order management (DOM)](./dom.md) features in Commerce ignore any sales lines that are marked for store pickup. These features are updated to ensure that sales lines that are linked to configured pickup delivery modes bypass the DOM logic and aren't reallocated to a new fulfillment warehouse.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
