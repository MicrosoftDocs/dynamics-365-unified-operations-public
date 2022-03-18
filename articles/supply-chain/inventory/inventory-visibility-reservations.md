---
title: Inventory Visibility reservations
description: This topic describes how to set up the reservation feature to create reservations, consume reservations, and/or unreserve specified inventory quantities by using Inventory Visibility.
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


This topic describes how to set up the reservation feature to create reservations, consume reservations, and/or unreserve specified inventory quantities by using Inventory Visibility.

Reservations mark a quantity of inventory that will be used in the future. When you create a reservation, the system prevents other orders from reserving or consuming the reserved goods until the reservation is either consumed or unreserved. Reservations are created, consumed, and canceled by using API calls to the Inventory Visibility service.

You can optionally set up Microsoft Dynamics 365 Supply Chain Management (and other third-party systems) to automatically offset the quantity that has been reserved by using Inventory Visibility. The offset quantity is deleted from the reservation records in Inventory Visibility.

When you turn on the reservation feature, Supply Chain Management automatically becomes ready to offset reservations that are made by using Inventory Visibility.

## <a name="turn-on"></a>Turn on and set up the reservation feature

To turn on the reservation feature, follow these steps.

1. Sign into Power Apps and open **Inventory Visibility**.
1. Open the **Configuration** page.
1. On the **Feature Management** tab, turn on the *OnHandReservation* feature.
1. Sign in to Supply Chain Management.
1. Go to the **[Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)** workspace and enable the *Inventory Visibility integration with reservation offset* feature (requires version 10.0.22 or later).
1. Go to **Inventory Management \> Setup \> Inventory Visibility integration parameters**, open the **Reservation offset** tab and make the following settings:
    - **Enable reservation offset** – Set to *Yes* to enable this functionality.
    - **Reservation offset modifier** – Select the inventory transaction status that will offset reservations made on Inventory Visibility. This setting determines the order processing stage that triggers offsets. The stage is traced by the order's inventory transaction status. Choose one of the following:
        - *On order* – For the *On transaction* status, an order will send an offset request when it's created. The offset quantity will be the quantity of the created order.
        - *Reserve* – For the *Reserve ordered transaction* status, an order will send an offset request when it's reserved, picked, packing-slip posted, or invoiced. The request will be triggered only once, for the first step when the mentioned process occurs. The offset quantity will be the quantity where the inventory transaction status changed from *On order* to *Reserved ordered* (or later status) on the corresponding order line.

## Use the reservation feature in Inventory Visibility

When you call the reservation API, the system marks the reservation of the specified goods and quantities. You must define a reservation hierarchy and post requests that match that reservation hierarchy. The reservations can then be made by calling the reservation APIs directly.

### Configure the reservation hierarchy

The reservation hierarchy describes the sequence of dimensions that must be specified when reservations are made. It works in the same way that the index hierarchy works for on-hand queries.

The reservation hierarchy can differ from the index hierarchy. This independence lets you implement category management where users can break down the dimensions into details to specify the requirements for making more precise reservations.

To configure a soft reservation hierarchy in Power Apps, open the **Configuration** page, and then, on the **Soft reservation hierarchy** tab, set up the reservation hierarchy by adding and/or modifying dimensions and their hierarchy levels.

Your soft reservation hierarchy should contain `SiteId` and `LocationId` as components, because they construct the partition configuration.

For more information about how to configure reservations, see [Reservation configuration](inventory-visibility-configuration.md#reservation-configuration).

### Call the reservation API

Reservations are made in the Inventory Visibility service by submitting a POST request to the service's URL, such as `/api/environment/{environment-ID}/onhand/reserve`.

For a reservation, the request body must contain an organization ID, a product ID, reserved quantities, and dimensions. The request generates a unique reservation ID for each reservation record. The reservation record contains the unique combination of the product ID and dimensions.

When you call the reservation API, you can control the reservation validation by specifying the Boolean `ifCheckAvailForReserv` parameter in the request body. A value of `True` means that the validation is required, whereas a value of `False` means that the validation isn't required. The default value is `True`.

If you want to cancel a reservation or unreserve specified inventory quantities, set the quantity to a negative value, and set the `ifCheckAvailForReserv` parameter to `False` to skip the validation.

Here is an example of the request body, for reference.

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

## Offset reservations in Supply Chain Management

For inventory transaction statuses that include a specified reserve offset modifier, the transaction update will offset the corresponding reservation record when all the following conditions are met:

- The reservation ID on the inventory transaction matches the reservation ID of the reservation record in the Inventory Visibility service.
- The dimensions of the inventory transaction are identical to the dimensions of the reservation record in the Inventory Visibility service.
- Changes in inventory transaction status trigger offsets for reservations when the inventory transaction status reflects the fact that an order process has been completed or skipped.

The offset quantity follows the inventory quantity that is specified on inventory transactions. The offset doesn't take effect if no reserved quantity remains in the Inventory Visibility service.

### Set up the reservation offset modifier

If you haven't already done so, set up the reservation modifier as described in [Turn on and set up the reservation feature](#turn-on).

### Set up reservation IDs

The reservation ID uniquely marks a reservation record in Inventory Visibility. In Supply Chain Management, users put reservations on order lines to mark the offset for the corresponding reservation record.

To set up reservation IDs in Supply Chain Management, follow these steps.

1. Open a sales order (for example, from the **All sales orders** page).
1. On the **Sales order lines** FastTab, select an order line.
1. On the **Sales order lines** FastTab, on the toolbar, select **Update line \> Inventory \> Inventory Visibility integration**.
1. Enter the relevant reservation IDs.

The inventory status change matches the offset modifier setup.
