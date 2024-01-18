---

# required metadata
title: Channel and catalog selection in call center for creating B2B orders
description: Enhanced support for Commerce sales order creation through Call Center to be B2B Channel and B2B Catalog-specific B2B Order.
author: ashishmsft
ms.date: 01/17/2024
ms.topic: article
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2017-06-30

---
# Channel and catalog selection in call center for creating B2B orders 

[!include [banner](../includes/banner.md)]

This document describes the functionality that enables customer service personnel in the call center to initiate orders on behalf of B2B partners (buyers) corresponding to their specific B2B channel. Moreover, when adding order lines, they can pick items that are solely from B2B catalogs associated with the B2B channel.

## Prerequisites

- Application version is 10.0.38 or later. 
- To use this feature, enable the following feature from feature management: "Enable B2B2B setup and enhancements to B2B Commerce orders".
- Ensure that the customer hierarchy, the distributor-channel associations, and the catalog-channel associations are set up correctly in the system.
- User accessing customer service form in Call-center must be a 'Call-center' user. If not, add your user account as a 'Channel user' to a call-center channel from 'All Call Centers' form.
- Customer account (C2), for whom order is being created, must be a B2B customer, meaning that they must be associated with a B2B customer hierarchy in the system. For more information, see [Learn more about managing customer hierarchies](./b2b/partners-customer-hierarchies.md)


## Create an order

In the Customer Service form, search for a B2B customer, select the appropriate channel for the outlet user/c2 customer based on their association in the customer hierarchy. Here you can either select a B2B online channel (associated with customer) or call-center associated with the customer service agent creating the order. This channel selection controls the downstream choices available. For example, if you select a B2B online channel (associated with a customer's B2B customer hierachy) then the catalog selections available are based on the catalogs associated with the selected B2B online channel. If you were to have selected call center, then it wouldn't have the catalog selection and shall behave the same way as it was before introduction of the channel field. Other order details, such as delivery mode, delivery date, and payment method are also controlled by the selection or update to channel. 

### Add order lines

- When adding order lines, choose items exclusively from B2B catalogs associated with the selected B2B channel. The system limits the product selection based on the catalog.
- The catalog-specific prices are automatically applied when adding item lines to the cart from a particular catalog. The system honors the prices based on the combination of channel, customer, and catalog.
- Adjust the quantity of the order lines as needed. The system honors the quantity limits based on the 'Default order settings' on the product.
- Additionally, you may notice that site and warehouse on each of the order lines are also limited to Channel selection in the header. 

### Modify an order

- Modifications to the channel are only allowed if no line has been fulfilled. If an order is partially fulfilled, then no modification is allowed to update the channel.
- If no line is fulfilled, then the channel can be updated on the header, and the system must validate if the catalog on already added lines is still valid.
- If the catalog isn't valid with the newly updated channel, the system flags those lines with a warning to update the valid catalog selection.
- If the catalog on already existing order lines is valid with the newly updated channel, no action is required. The system also updates the pricing based on the updated channel information.
- On nonfulfilled lines, the site, warehouse, product information, quantity, or catalogs can be updated or removed as needed. The system validates the product information and the catalog selection accordingly and apply the appropriate prices.

## Benefits

- This functionality enhances the customization of orders according to specific B2B channels and catalogs.
- It streamlines the ordering process, ensuring accuracy and efficiency.
- It assures the correct pricing application aligned with specific B2B catalogs and B2B online channel. 
