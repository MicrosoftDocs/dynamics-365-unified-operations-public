---
title: Inventory Visibility Reservations
description: This topic describes how to set up the reservation feature to create a reservation, consume reservation, and/or unreserve specified inventory quantities using Inventory Visibility.
author: yufeihuang
ms.date: 08/02/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21
---

# Inventory Visibility Reservations

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
[!INCLUDE [cc-data-platform-banner](../../includes/cc-data-platform-banner.md)]

This topic describes how to set up the reservation feature to create a reservation, consume reservation, and/or unreserve specified inventory quantities using Inventory Visibility.

Reservation marks quantity to be used in the future. When you create a reservation, the system prevents other orders from reserving or consuming the reserved goods until the reservation is consumed or unreserved. Reservations are created, consumed, or cancelled using API calls to the Inventory Visibility Service.

Optionally, you can set up Dynamics 365 Supply Chain Management (and other third part systems) to automatically offset the quantity reserved using Inventory Visibility. The offset quantity is deleted from the reservation records in Inventory Visibility.

When you enable the reservation feature, Dynamics 365 Supply Chain Management will automatically be prepared to offset reservations made using Inventory Visibility.

## Enable the Reservation Feature

Follow the below steps to enable the Reservation Feature

1. you need to enable `OnHandReservation` feature. Open**Inventory Visibility** PowerApps, go to "Configurations" page and open  **Feature Management Tab, turn on **OnHandReservation feature.<!-- KFM: where is this? More detail is needed. "CDS" is an outdated term. -->
1. Sign in to Dynamics 365 Supply Chain Management
1. Go to **Inventory Management \> Setup \> Inventory Visibility integration parameters**
1. Under **Reservation offset**, set **Enable reservation offset** to *Yes*. <!-- KFM: I don't see this, so I'm not sure how to clarify this instruction. --> <!-- Jiacheng: This is not yet checked in but we can review the UI for a dev environment. -->

## Use the Reservation Feature in Inventory Visibility

When you call the reservation API, the system marks the reservation of the specified goods and quantities. You must define a reservation hierarchy and post requests that match the reservation hierarchy. After that, reservations can be made by calling the reservation APIs directly.

### Configure the Reservation Hierarchy

The reservation hierarchy describes the sequence of dimensions to specify when making reservations. It works the same way as index hierarchy works for on-hand queries.

The reservation hierarchy can be different from the index hierarchy. This lets you implement category management where users can break down the dimensions into details to specify the needs for making more precise reservations.

To configure soft reservation hierarchy on Power Apps page, go to "Configurations - Soft reservation mapping" and set the reservation hierarchy by adding / modifying dimensions and their hierarchy levels. <!-- KFM: we should either provide these details here or provide a link to how to do it for index hierarchy (I don't think this is documented though). -->

### Call the Reservation API

Making reservations on the Inventory Visibility service is done by submitting a POST request to its URL, for example: `/api/environment/{environment-ID}/onhand/reserve`. <!--KFM: Original was unclear. Please confirm this revision. -->

To make a reservation, the request body must contain an organization ID, product ID, reserved quantities, and dimensions. The request generates a reservation ID unique for each reservation record. The reservation record contains the unique combination of product ID and dimensions. <!--KFM: An example of this request body might help. -->

For reference, an example of the request body is as follows: 
<!--KFM: An example of this request body might help. -->

```json
# Url
# replace {RegionShortName} and {EnvironmentId} with your value
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/onhand/reserve

# Method
Post

# Header
# replace {access_token} with the one get from security service
Api-version: "1.0"
Content-Type: "application/json"
Authorization: "Bearer {access_token}"

# Body
{
    "id": "id-bike-0001",
    "organizationId": "usmf",
    "productId": "Bike",
    "dimensions": {
        "SiteId": "1",
        "LocationId": "11",
        "ColorId": "Red",
        "SizeId": "small"
    },
    "quantityDataSource": "iv",
    "modifier": "SoftReservOrdered",
    "quantity": 1,
    "ifCheckAvailForReserv": true
}
```

## Offset Reservations in Dynamics 365 Supply Chain Management

For inventory transaction statuses that include a specified reserve offset modifier, the transaction update will offset the corresponding reserve record when all of following conditions are met:

- The reservation ID on the inventory transaction matches that of the Inventory Visibility service reservation record.
- The dimensions of the inventory transaction are identical to those of the Inventory visibility service reservation record.
- Changes in inventory transaction status triggers offsets for reservations when the inventory transaction status reflects that an order process is achieved or skipped. <!--KFM: What do you mean by "is modified"? Is this a condition or a result? -->

The offset quantity follows the inventory quantity specified on inventory transactions. The offset will not take effect when no reserved quantity remains in the Inventory Visibility service.

### Set up the Reserve Offset Modifier

The reserve offset modifier determines the order processing stage to trigger offsets. The stage is traced by the order's inventory transaction status. To set it up:
 <!--KFM: The following procedure was difficult to understand in the original. Please confirm and improve this revision. -->
1. Go to **Inventory Management \> Setup \> Inventory Visibility integration parameters \> Reservation offset**. <!--KFM: This path doesn't exist on my environment, so I could not confirm this. -->
1. Set **Reserve offset modifier** to one of the following values:
    - *On order* – For *On transaction* status, an order will send offset request upon the order creations. <!--KFM: This is unclear. Please revise. -->
    - *Reserve* – For *Reserve ordered transaction* status, an order will send an offset request at any stages in order reservation, pick, post packing slip or invoicing. The request will only be triggered once among the first step when the mentioned process takes place. <!--KFM: This is unclear. Please revise. -->

### Set up Reservation IDs

The reservation ID marks an reservation record on inventory visibility uniquely. <!--KFM: Spell out "OHMS". --> In Dynamics 365 Supply Chain Management, users put reservations in order lines to mark the offset for the corresponding reservation record.

To set reservation IDs in Supply Chain Management:

1. Open a sales order (for example, from the **All sales orders** page).
1. On the **Sales order lines** FastTab, select an order line.
1. From the **Sales order lines** FastTab toolbar, select **Update line \> Inventory \> Inventory Visibility integration**. <!--KFM: I don't see this in the UI, so I can't confirm whether it is correct. -->
1. Enter the relevant reservation IDs. 
1. The inventory status change matches the offset modifier setup as explained. <!--KFM: This is unclear. Please revise. -->
