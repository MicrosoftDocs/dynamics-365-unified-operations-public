---
title: Inventory Visibility reservations
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

# Inventory Visibility reservations

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
[!INCLUDE [cc-data-platform-banner](../../includes/cc-data-platform-banner.md)]

This topic describes how to set up the reservation feature to create a reservation, consume a reservation, and/or unreserve specified inventory quantities using Inventory Visibility.

Reservations mark a quantity of inventory to be used in the future. When you create a reservation, the system prevents other orders from reserving or consuming the reserved goods until the reservation is consumed or unreserved. Reservations are created, consumed, or cancelled using API calls to the Inventory Visibility service.

Optionally, you can set up Dynamics 365 Supply Chain Management (and other third part systems) to automatically offset the quantity reserved using Inventory Visibility. The offset quantity is deleted from the reservation records in Inventory Visibility.

When you enable the reservation feature, Dynamics 365 Supply Chain Management will automatically be prepared to offset reservations made using Inventory Visibility.

> [!NOTE]
> The offset functionality requires Supply Chain Management version 10.0.22 or later. If you want to use Inventory Visibility reservations, then we recommend that you wait until you have upgraded Supply Chain Management to version 10.0.22 or later.

## Enable the reservation feature

Use the following steps to enable the reservation Feature

1. Open **Inventory Visibility** in Power Apps.
1. Go to the **Configurations** page and open the **Feature Management** Tab. Then turn on the **OnHandReservation** feature.
1. Sign in to Dynamics 365 Supply Chain Management
1. Go to **Inventory Management \> Setup \> Inventory Visibility integration parameters**
1. Under **Reservation offset**, set **Enable reservation offset** to *Yes*.

## Use the Reservation Feature in Inventory Visibility

When you call the reservation API, the system marks the reservation of the specified goods and quantities. You must define a reservation hierarchy and post requests that match the reservation hierarchy. After that, reservations can be made by calling the reservation APIs directly.

### Configure the reservation hierarchy

The reservation hierarchy describes the sequence of dimensions to specify when making reservations. It works the same way as index hierarchy works for on-hand queries.

The reservation hierarchy can be different from the index hierarchy. This lets you implement category management where users can break down the dimensions into details to specify the needs for making more precise reservations.

To configure soft reservation hierarchy on Power Apps page, go to **Configurations \> Soft reservation mapping** and set the reservation hierarchy by adding and/or modifying dimensions and their hierarchy levels.

### Call the reservation API

Making reservations on the Inventory Visibility service is done by submitting a POST request to its URL, for example: `/api/environment/{environment-ID}/onhand/reserve`.

To make a reservation, the request body must contain an organization ID, product ID, reserved quantities, and dimensions. The request generates a reservation ID unique for each reservation record. The reservation record contains the unique combination of product ID and dimensions.

For reference, an example of the request body is as follows:

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

## Offset reservations in Dynamics 365 Supply Chain Management

For inventory transaction statuses that include a specified reserve offset modifier, the transaction update will offset the corresponding reserve record when all of following conditions are met:

- The reservation ID on the inventory transaction matches that of the Inventory Visibility service reservation record.
- The dimensions of the inventory transaction are identical to those of the Inventory visibility service reservation record.
- Changes in inventory transaction status trigger offsets for reservations when the inventory transaction status reflects that an order process has been completed or skipped.

The offset quantity follows the inventory quantity specified on inventory transactions. The offset will not take effect when no reserved quantity remains in the Inventory Visibility service.

> [!NOTE]
> The offset functionality is available from version 10.0.22

### Set up the Reserve Offset Modifier

The reserve offset modifier determines the order processing stage to trigger offsets. The stage is traced by the order's inventory transaction status. To set it up:

1. Go to **Inventory Management \> Setup \> Inventory Visibility integration parameters \> Reservation offset**.
1. Set **Reserve offset modifier** to one of the following values:
    - *On order* – For *On transaction* status, an order will send an offset request when an order is created.
    - *Reserve* – For *Reserve ordered transaction* status, an order will send an offset request when the order reserved, picked, packing-slip posted, or invoiced. The request will only be triggered once, for the first step when the mentioned process takes place.

### Set up reservation IDs

The reservation ID marks an reservation record on inventory visibility uniquely. In Dynamics 365 Supply Chain Management, users put reservations in order lines to mark the offset for the corresponding reservation record.

To set reservation IDs in Supply Chain Management:

1. Open a sales order (for example, from the **All sales orders** page).
1. On the **Sales order lines** FastTab, select an order line.
1. From the **Sales order lines** FastTab toolbar, select **Update line \> Inventory \> Inventory Visibility integration**.
1. Enter the relevant reservation IDs.
1. The inventory status change matches the offset modifier setup.
