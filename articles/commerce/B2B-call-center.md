---
# required metadata

title: Channel and catalog selection enhancements in call center for creating B2B orders
description: This article describes feature functionality enhancements that enable call center workers to initiate orders on behalf of B2B partners in their B2B channels.
author: ashishmsft
ms.date: 01/17/2024
ms.topic: article
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2017-06-30

---
# Channel and catalog selection enhancements in call center for creating B2B orders 

[!include [banner](../includes/banner.md)]

This article describes feature functionality enhancements that enable call center workers to initiate orders on behalf of business to business (B2B) partners in their B2B channels. When adding order lines, call center workers can select items from the B2B catalogs associated with the B2B channel.

## Benefits

The feature functionality enhancements provide the following benefits:

- Improving the customization of orders according to specific B2B channels and catalogs.
- Streamlining the ordering process, ensuring accuracy and efficiency.
- Ensuring that correct pricing is applied to specific B2B catalogs and B2B online channels.

## Prerequisites

For the feature functionality to work, the following prerequisites must be met.

- Your site must be running Commerce version 10.0.38 or later. 
- The customer hierarchy, the distributor—channel associations, and the catalog—channel associations must be set up correctly in the system.
- Users accessing the customer service form in call center must be call center channel users. User accounts can be added as call center channel users from the **All Call Centers** form in Commerce headquarters.
- Customer accounts for which orders are created must be B2B customers, in other words they must be associated with a B2B customer hierarchy in the system. For more information, see [Learn more about managing customer hierarchies](./b2b/partners-customer-hierarchies.md)

## Enable the feature

To enable the feature in headquarters, follow these steps.

1. Go to the **Feature management** workspace (**Systems administration \> Workspaces \> Feature management**).
1. Search for the **Enable B2B2B setup and enhancements to B2B Commerce orders** feature, and then select it.
1. In the right pane, select **Enable now**.

## Create an order

To create an order in headquarters after you enable the feature, follow these steps.

1. On the **Customer service** form (**Retail and Commerce \> Customers \> Customer service**), search for a B2B customer. 
1. Select either a B2B online channel associated with the customer, or the call center channel associated with the customer service agent creating the order.

    > [!NOTE]
    > The channel selection controls the downstream choices that are available. For example, if you select a B2B online channel associated with a customer's B2B customer hierarchy, then the available catalog selections are based on the catalogs associated with the selected B2B online channel. If you select the call center channel, you won't see the same catalog selection as for a B2B online channel. 

1. Add order lines as needed. Order details such as delivery mode, delivery date, and payment method are also controlled by the selection or update to channel. 

### Order lines

- When adding order lines, select items from B2B catalogs associated with the selected B2B channel. The system limits the product selection based on the catalog.
- Catalog-specific prices are automatically applied when adding item lines to the cart from a particular catalog. The system honors the prices based on the combination of channel, customer, and catalog.
- You can adjust the quantity of the order lines as needed. The system honors the quantity limits based on the default order settings of the product.
- You may notice that the site and warehouse for each of the order lines are limited by the channel selection in the header. 

### Order modifications

- Modifications to a channel are only allowed if no line has been fulfilled. If an order is partially fulfilled, then no modification is allowed to update the channel.
- If no line is fulfilled, then the channel can be updated on the header, and the system must validate if the catalog on already added lines is still valid.
- If the catalog isn't valid with the newly updated channel, the system flags those lines with a warning to update the valid catalog selection.
- If the catalog on already existing order lines is valid with the newly updated channel, no action is required. The system also updates the pricing based on the updated channel information.
- On nonfulfilled lines, the site, the warehouse, product information, quantities, or catalogs can be updated or removed as needed. The system validates the product information and the catalog selection accordingly and applies the appropriate prices.

 
