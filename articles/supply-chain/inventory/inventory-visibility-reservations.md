---
title: Inventory Visibility reservations
description: This article describes how to set up the reservation feature to create reservations, consume reservations, and/or unreserve specified inventory quantities by using Inventory Visibility.
author: yufeihuang
ms.date: 11/04/2022
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

This article describes a typical use case for soft reservations and explains how to set them up in Inventory Visibility, including how to create soft reservations, offset soft reservations upon physical consumption, and adjust or unreserve specified inventory quantities.

## Sample use case for soft reservation

Soft reservations help organizations achieve a single source of truth for available inventory, especially during the order fulfillment process. This functionality is useful for organizations where the following conditions exist:

- The organization has at least two different systems that are directly taking outbound orders.
- The organization is very strict and wants to prevent double-booking product inventory, which can happen if multiple systems are able to overbook the last piece of stock. This situation is prevented when all order systems can make instant soft reservation API calls to Inventory Visibility, which provides a single source of truth for inventory availability.

[<img src="media/inventory-visibility-soft-reservation.png" alt="Inventory Visibility soft reservation." title="Inventory Visibility soft reservation" width="720" />](media/inventory-visibility-soft-reservation.png)

The previous illustration shows how soft reservation works and highlights the following operations:

- Your initial inventory level is synchronized to Inventory Visibility from Supply Chain Management.
- Soft reservations are posted from each of your order channels/systems to Inventory Visibility. Inventory Visibility validates inventory availability and tries to make a soft reservation. If soft reservation succeeds, Inventory Visibility adds to the soft reserved quantity, deducts from the available for reservation (AFR) quantity, and respond with a soft reservation ID.
- At this time, your physical inventory quantity remains the same.
- You can then synchronize either single or aggregated soft-reserved orders (order lines) into Supply Chain Management to make hard reservations and release to warehouse or update the final inventory quantity.
- You can set the system to [offset soft reservations](inventory-visibility-reservations.md#offset-reservations-in-supply-chain-management) so that soft reservations are offset when physical inventory is updated in Supply Chain Management.

Soft reservations are normally created, consumed, and canceled by using API calls to the Inventory Visibility service.

> [!NOTE]
> You can optionally set up Supply Chain Management (and other third-party systems) to automatically offset the quantity that has been reserved by using Inventory Visibility. The offset quantity is deleted from the reservation records in Inventory Visibility.
>
> By default, the offset function is automatically turned on when you enable the soft reservation feature.

## <a name="turn-on"></a>Turn on and set up the reservation feature

To turn on the reservation feature, follow these steps.

1. Sign into Power Apps and open **Inventory Visibility**.
1. Open the **Configuration** page.
1. On the **Feature Management** tab, turn on the *OnHandReservation* feature.
1. Sign in to your Supply Chain Management environment.
1. Go to the **[Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)** workspace and enable the *Inventory Visibility integration with reservation offset* feature (requires version 10.0.22 or later).
1. Go to **Inventory Management \> Setup \> Inventory Visibility integration parameters**, open the **Reservation offset** tab and make the following settings:
    - **Enable reservation offset** – Set to *Yes* to enable this functionality.
    - **Reservation offset modifier** – Select the inventory transaction status that will offset reservations made in Inventory Visibility. This setting determines the order processing stage that triggers offsets. The stage is traced by the order's inventory transaction status. Choose one of the following values:
        - *On order* – Orders with an *On order* status will send an offset request when they're created. The offset quantity will be the quantity of the created order (line).
        - *Reserve* – Orders with a *Reserve* status will send an offset request when they're either order reserved or physically reserved. When you offset at *Reserve* status (even if you skip the reservation in Supply Chain Management and continue to another inventory status, for example release to warehouse to pick and pack) the order will send an offset request at any new inventory status that is closest to reserved picked (for example, pick, packing-slip posted, or invoiced). The request will be triggered only once. If it's been triggered at pick, it will not duplicate the offset when posting a packing slip. The offset quantity will be the same as the quantity of the inventory transaction status when the offset was triggered (in other words, *Reserved ordered/Reserve Physical* (or later status) on the corresponding order line).
1. Sign back in to the Inventory Visibility power app, go to the **Configuration** page and open the **Soft Reservation** tab. Review the default soft reservation hierarchy and add new dimensions to the hierarchy if needed.
1. In the **Set Soft Reservation Mapping** section, view the default settings. By default, the soft reserved inventory quantities will be recorded against the `softreservephysical` physical measure, data source `iv`. The calculated measure *Available for reservation* is mapped to `availabletoreserve`. If you wish to update the `availabletoreserve` calculated measure, go to the **Configuration** page and open the **Calculated Measure** tab. Then expand and modify the calculated measure.

For more information, see [Configure Inventory Visibility](inventory-visibility-configuration.md).

> [!NOTE]
> The reservation hierarchy describes the sequence of dimensions that must be specified when reservations are made. It works in the same way as the index hierarchy works for on-hand queries, but it is used independently to let users specify dimension details to make more precise reservations.

> Your soft reservation hierarchy should contain `SiteId` and `LocationId` as components, because they construct the partition configuration of Inventory Visibility.

For more information about how to configure reservations, see [Reservation configuration](inventory-visibility-configuration.md#reservation-configuration).

## Use the reservation feature in Inventory Visibility

When you call the reservation API, the system marks the reservation of the specified goods and quantities.

Here's a sample scenario and sample API query body. The company Contoso sells product D0002 (Cabinet) from their e-commerce website. A customer places a sales order via the website, asking for a small red cabinet. Contoso then decides to fulfill this order using the following dimensions

- Organization ID = usmf
- Site = 1
- Warehouse = 11
- Product = D0002
- Color = red
- Size = small

Contoso have already set up an API connection to Inventory Visibility from their own e-commerce system. When the order is received, the system instantly triggers an API call to make a soft reservation for this cabinet in Inventory Visibility.

### Create soft reservations using the reservation API

Reservations are made in the Inventory Visibility service by submitting a POST request to the service's URL, such as `/api/environment/{environmentId}/onhand/reserve`.

For a reservation, the request body must contain an organization ID, a product ID, reserved quantities, and dimensions.

When you call the reservation API, you can control the reservation validation by specifying the Boolean `ifCheckAvailForReserv` parameter in the request body. A value of `True` means that the validation is required, whereas a value of `False` means that the validation isn't required. The default value is `True`.

If you want to cancel a reservation or unreserve specified inventory quantities, set the quantity to a negative value, and set the `ifCheckAvailForReserv` parameter to `False` to skip the validation.

Here's an example of the request body referencing the sales order in the previous context.

```json
# Url

#Replace {endpoint} with your system endpoint.
 {endpoint}/api/environment/{environmentId}/onhand/reserve

# Method
Post

# Header
# replace {access_token} with the one get from security service
Api-version: "1.0"
Content-Type: "application/json"
Authorization: "Bearer {access_token}"

# Body
{
    "id": "Testrequest-0005",
    "organizationId": "usmf",
    "productId": "D0002",
    "dimensions": {
        "SiteId": "1",
        "LocationId": "11",
        "ColorId": "red",
        "SizeId": "small"
    },
    "quantityDataSource": "iv",
    "modifier": "softreservphysical",
    "quantity": 1,
    "ifCheckAvailForReserv": true
}
```

A successful soft reservation request returns a *soft reservation ID* for each reservation record. The soft reservation ID isn't a unique identifier for an individual soft reservation record, but a combination of product ID and dimension values that are associated with the soft reservation request. You can record the soft reservation ID back into the order line when you synchronize the successfully reserved orders to Supply Chain Management or another ERP system for offset.

### Offset soft reservation in Supply Chain Management

It's possible to offset a soft reserved quantity once the quantity on an order is physically deducted in Supply Chain Management or another ERP system. Inventory Visibility offers out-of-box soft reservation offset integration with Supply Chain Management.

Follow these steps to offset a soft reservation:

1. Sign in to Supply Chain Management.
1. Go to **Sales and marketing \> Sales Orders \> All Sales Orders**.
1. Select **New** on the Action Pane.
1. Recreate the external sales order and add a sales line that uses the exact same product ID, organization, site, warehouse, and dimensions values.
1. On the **Sales order lines** FastTab, select the sales line you just entered and then, from the toolbar, select **Inventory \> Reservation ID**. Then do one of the following steps:
    - Option 1: Copy the soft reservation ID from your soft reservation request response and paste it into the **Reservation ID** field.
    - Option 2: Leave the **Reservation ID** field blank but select the **Inventory service auto offset** checkbox. The system will automatically find out which product and product dimensions to offset based on the item ID and dimension values entered on the selected line.
1. Select **OK**.
1. With the same sales line still selected, physically reserve the ordered quantity by selecting **Inventory \> Reservation** on the **Sales order lines** FastTab toolbar.
1. If you have previously set the **Reservation offset modifier** to *Reserved*, the offset will be triggered when the order line has a status of *Reserve physical* or *Reserve ordered*. A batch job runs once a minute to sync offset requests from Supply Chain Management to Inventory Visibility.

> [!NOTE]
> For transaction statuses that include a specified reserve offset modifier, the transaction update will offset the corresponding reservation record when all the following conditions are met:
>
> - The reservation ID on the inventory transaction matches the reservation ID of the reservation record in Inventory Visibility.
> - The dimensions of the inventory transaction are identical to the dimensions of the reservation record in Inventory Visibility.
> - Changes in inventory transaction status trigger offsets for reservations when the inventory transaction status reflects the fact that an order process has been completed or skipped.

Offset quantities follow the inventory quantities specified on the relevant inventory transactions. An offset won't take effect if no reserved quantity remains in Inventory Visibility.

### Cancel or revert a soft reservation

If an original order line gets canceled or deleted and you need to revert the corresponding soft reservation, post a negative quantity with the exact the same information in your API query body.
