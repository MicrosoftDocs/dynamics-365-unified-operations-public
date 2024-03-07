---
# required metadata

title: Channel and catalog selection enhancements in call center for creating B2B orders
description: This article describes channel and catalog selection enhancements in Microsoft Dynamics 365 Commerce that enable call center workers to initiate orders on behalf of B2B partners in their B2B channels.
author: ashishmsft
ms.date: 01/24/2024
ms.topic: article
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2017-06-30

---
# Channel and catalog selection enhancements in call center for creating B2B orders 

[!include [banner](../includes/banner.md)]

This article describes channel and catalog selection enhancements in Microsoft Dynamics 365 Commerce that enable call center workers to initiate orders on behalf of business-to-business (B2B) partners in their B2B channels. When call center workers add order lines, they can select items from the B2B catalogs that are associated with the B2B channel.

## Benefits

The channel and catalog selection enhancements provide the following benefits:

- Improve the customization of orders according to specific B2B channels and catalogs.
- Streamline the ordering process, and therefore ensure accuracy and efficiency.
- Ensure that correct pricing is applied to specific B2B catalogs and B2B online channels.

## Prerequisites

For the channel and catalog selection functionality to work, the following prerequisites must be met:

- Your site must be running Commerce version 10.0.38 or later.
- The customer hierarchy, the distributor—channel associations, and the catalog—channel associations must be set up correctly in the system.
- Users who access the customer service form in call center must be call center channel users. User accounts can be added as call center channel users from the **All Call Centers** page in Commerce headquarters.
- Customer accounts that orders are created for must be B2B customers. In other words, they must be associated with a B2B customer hierarchy in the system. For more information, see [Learn more about managing customer hierarchies](./b2b/partners-customer-hierarchies.md).

## Enable the feature

To enable the feature in Commerce headquarters, follow these steps.

1. Go to **Systems administration \> Workspaces \> Feature management**.
1. Search for the **Enable B2B2B setup and enhancements to B2B Commerce orders** feature, and then select it.
1. In the right pane, select **Enable now**.

## Create an order

To create an order in headquarters after you enable the feature, follow these steps.

1. Go to **Retail and Commerce \> Customers \> Customer service**, and search for a B2B customer.
1. Select a B2B online channel that's associated with the customer. Alternatively, select the call center channel that's associated with the customer service agent who is creating the order.

    > [!NOTE]
    > The channel selection controls the downstream choices that are available. For example, if you select a B2B online channel that's associated with a customer's B2B customer hierarchy, the available catalog selections are based on the catalogs that are associated with the selected B2B online channel. If you select the call center channel, different catalog selections are available.

1. Add order lines as needed. Order details such as the delivery mode, delivery date, and payment method are controlled by the selection or update to the channel.

### Order lines

- When you add order lines, select items from B2B catalogs that are associated with the selected B2B channel. The system limits the product selection, based on the catalog.
- When you add item lines to the cart from a catalog, catalog-specific prices are automatically applied. The system honors the prices, based on the combination of the channel, customer, and catalog.
- You can adjust the quantity of the order lines as needed. The system honors the quantity limits, based on the default order settings of the product.
- You might notice that the site and warehouse for each order line are limited by the channel selection on the header.

### Order modifications

- Modifications can be made to a channel only if no line is fulfilled. If an order is partially fulfilled, no modification is allowed to update the channel.
- If no line is fulfilled, the channel can be updated on the header. The system must validate whether the catalog on previously added lines is still valid.
- If the catalog isn't valid for the newly updated channel, the system flags those lines with a warning to indicate that the valid catalog selection must be updated.
- If the catalog on existing order lines is valid for the newly updated channel, no action is required. The system also updates the pricing, based on the updated channel information.
- On nonfulfilled lines, the site, the warehouse, product information, quantities, or catalogs can be updated or removed as needed. The system validates the product information and the catalog selection accordingly, and applies the appropriate prices.
