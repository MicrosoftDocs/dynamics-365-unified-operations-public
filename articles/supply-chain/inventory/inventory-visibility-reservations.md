---
title: Inventory Visibility reservations
description: This article describes how to set up the reservation feature to create reservations, consume reservations, and/or unreserve specified inventory quantities by using Inventory Visibility.
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

This article describes a typical use case for soft reservations and explains how to set them up in Inventory Visibility, including how to create soft reservations, offset soft reservations upon physical consumption, and adjust or unreserve specified inventory quantities.

## Sample use case for soft reservation

Soft reservations help organizations achieve a single source of truth for available inventory, especially during the order fulfillment process. This functionality is useful for organizations where the following conditions exist:

- The organization has at least two different systems that are directly taking outbound orders.
- The organization is very strict and wants to prevent double-booking product inventory, which can happen if multiple systems are able to overbook the last piece of stock. This is prevented when all order systems can make instant soft reservation API calls to Inventory Visibility, which provides a single source of truth for inventory availability.

<!-- KFM: The following link isn't valid. Not sure what we are talking about here. 

Otherwise you can simply leverage the [Inventory Adjustment via onhand change posting](TBD) feature that you can first query inventory availability, and make a separate inventory adjustment call to deduct the available inventory.

-->

[<img src="media/inventory-visibility-soft-reservation.png" alt="Inventory Visibility soft reservation." title="Inventory Visibility soft reservation" width="720" />](media/inventory-visibility-soft-reservation.png)

The previous illustration shows how soft reservation works and highlights the following operations:

- Your initial inventory level is synchronized to Inventory Visibility from Supply Chain Management.
- Soft reservations are posted from each of your order channels/systems to Inventory Visibility. Inventory Visibility validates inventory availability and tries to make a soft reservation. If soft reservation succeeds, Inventory Visibility adds to the soft reserved quantity, deducts from the available for reservation (AFR) quantity, and respond with a soft reservation ID.
- At this time, your physical inventory quantity remains the same.
- You can then synchronize either single or aggregated soft-reserved orders (order lines) into Supply Chain Management to make hard reservations and release to warehouse or update the final inventory quantity.
- You can set the system to [offset soft reservations](inventory-visibility-reservations.md#offset-reservations-in-supply-chain-management) so that soft reservation are offset when physical inventory is updated in Supply Chain Management.

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
1. Sign in to Supply Chain Management environment.
1. Go to the **[Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)** workspace and enable the *Inventory Visibility integration with reservation offset* feature (requires version 10.0.22 or later).
1. Go to **Inventory Management \> Setup \> Inventory Visibility integration parameters**, open the **Reservation offset** tab and make the following settings:
    - **Enable reservation offset** – Set to *Yes* to enable this functionality.
    - **Reservation offset modifier** – Select the inventory transaction status that will offset reservations made on Inventory Visibility. This setting determines the order processing stage that triggers offsets. The stage is traced by the order's inventory transaction status. Choose one of the following values:
        - *On order* – For the *On order* status, an order will send an offset request when it's created. The offset quantity will be the quantity of the created order (line).
        - *Reserve* – For the *Reserve* status, an order will send an offset request when it's either reserve ordered or reserve physical. When you set offset at *Reserve* status, even if you skip the reservation in Dynamcis 365 SCM and continuous with the rest of inventory status, for example release to warehouse to pick and pack. The order will send offset request at any next inventory status you perform that is closest to reserved picked, for example, pick, packing-slip posted, or invoiced. The request will be triggered only once. If it's been triggered at pick, it will not duplicate the offset at packing-slip posted. The offset quantity will be the same quantity as inventory transaction status when the offset is triggerd, i.e. *Reserved ordered/Reserve Physical* (or later status) on the corresponding order line.
1. Sign back into inventory visibility power app, go to **Configuration** > **Soft Reservation**, review default soft reservation hierarchy, add new dimensions onto the hierarchy if needed
1. Go to next section **Set Soft Reservation Mapping**, view the default settings. By default the soft reserved inventory quanties will be recorded against **softreservephysical** physical measure, datasource **iv**. The calculated measure to calculated **Available For Reservation** is mapped to **availabletoreserve**. If you wish to update the **availabletoreserve** calculated measure, go to **Configuration**>**Calcualted Measure**, unfold **AVAILABLETORESERVE of IV** to modify the calculated measure.

Refer to [Inventory Visibility Configuration](inventory-visibility-configuration.md) for additional details.

>[!NOTE]
>The reservation hierarchy describes the sequence of dimensions that must be specified when reservations are made. It works in the same way that the index hierarchy works for on-hand queries. But it is used independent to let users specify dimensions details to make more precise reservations.

>Your soft reservation hierarchy should contain `SiteId` and `LocationId` as components, because they construct the partition configuration of Inventory Visibility.

For more information about how to configure reservations, see [Reservation configuration](inventory-visibility-configuration.md#reservation-configuration).

## Use the reservation feature in Inventory Visibility

When you call the reservation API, the system marks the reservation of the specified goods and quantities. 

Here is an sample scenario and sample API query body. 

Contoso sells procut D0002 (Cabinet) via their ecommerce website. A customer placed a sales order via the website, asking for a cabinet, colour red and size small. Contoso then decides to fulfill this order via 
- Organization ID = usmf
- Site = 1, Warehouse = 11
- product D0002
- Colour = red, size=small

They have already built API connection with Inventory Visibility in their own ecommerce system, the API call to do soft reservation for this order is triggerd instantly to make sure 1 quantity of this Cabinet is reserved centrally in Inventory Visibility.

### Create Soft Reservation via the reservation API

Reservations are made in the Inventory Visibility service by submitting a POST request to the service's URL, such as `/api/environment/{environmentId}/onhand/reserve`.

For a reservation, the request body must contain an organization ID, a product ID, reserved quantities, and dimensions. 

When you call the reservation API, you can control the reservation validation by specifying the Boolean `ifCheckAvailForReserv` parameter in the request body. A value of `True` means that the validation is required, whereas a value of `False` means that the validation isn't required. The default value is `True`.

If you want to cancel a reservation or unreserve specified inventory quantities, set the quantity to a negative value, and set the `ifCheckAvailForReserv` parameter to `False` to skip the validation.


Here is an example of the request body referencing the sales order in the previous context, for reference.

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
A successful soft reservation request returns a **soft eservation ID** for each reservation record. The **soft reservation ID** is not a unique identifier for indivisual soft reservation record, but a combination of product ID and dimensions values that associate with the soft reservation request. You can record the soft reservation ID back into the order line when you synchronize the successfully reserved orders into Dynamcis 365 SCM or other ERP system for offset.

### Offset soft reservation in Supply Chain Management

You may want to offset the soft reserved quantity once the quantity on the order is physically deducted in the inventory mangement/ERP system such as Dynamics 365 Supply Chain Management. Inventory Visibility add-in offers out-of-box soft reservation offset integration with Dynamics 365 SCM.

Follow the steps to offset soft reservation
1. Sign in into Dynamics 365 SCM, select org ID. Go to **Sales and marketing**> **Sales Orders** > **All Sales Orders**>**New**, recreate the external sales order into Dynamics 365 SCM with exact the same product ID, organization, site, warehouse and dimensions values. For example
    - Site = 1, Warehouse = 1, product D0002, Colour = red, size=small
1. Select the line you just entered, go to **Inventory**>**INVENTORY VISIBILITY INTEGRATION**>**Reservation Id**. You have two options, choose one that applies to you:
    - Option 1: copy the soft reservation ID from your soft reservation request response and populate into the **Reservation Id** field.
    - Option 2: leave the **Reservation Id** field blank but check the box **InventoryServiceautoOffset**, the system will automatically workout which procut under what dimensions that need offset based on the item ID + dimension values entered on this line.
1. Click **OK**.
1. Physically reserve your on order quantity by selecting the same sales line and go to **Inventory** tab > **MAINTAIN**>**Reservation**
1. If you have previously set the **Reservation offset modifier** at **Reserved**, the offset will be triggered when the order line is at **Reserve Physical** or **Reserve Ordered** status. There is a batch job that syncs the offset request together with invent sum changes from Dynamics 365 SCM to Inventory Visibility add-in every 1 minute. 

>[!NOTE]
>For the transaction statuses that include a specified reserve offset modifier, the transaction update will offset the corresponding reservation record when all the following conditions are met:
>- The reservation ID on the inventory transaction matches the reservation ID of the reservation record in the Inventory Visibility service.
>- The dimensions of the inventory transaction are identical to the dimensions of the reservation record in the Inventory Visibility service.
>- Changes in inventory transaction status trigger offsets for reservations when the inventory transaction status reflects the fact that an order process has been completed or skipped.

The offset quantity follows the inventory quantity that is specified on inventory transactions. The offset doesn't take effect if no reserved quantity remains in the Inventory Visibility service.]
### Cancel/revert soft reservation
In the case that original order line gets cancelled/deleted and you need to revert the corresponding soft reservation, you can post a negative quantity with exact the same information in your API query body.
