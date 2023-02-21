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

This article describes a typical use case for soft reservations and explains how to set them up in Inventory Visibility. It includes information about how to create soft reservations, offset them upon physical consumption, and adjust or unreserve specified inventory quantities.

From version 10.0.33 onwards, you can also make soft reservation from Dynamics 365 Supply Chain Management sales orders which will post soft reservation requests to Inventory Visibility and validate AvailbleForReservation qtys in IV. It is advised that **all new Inventory Visibility soft reservation customers adopt this new version**. For more details, see [Further settings if Inventory Visibility integration with soft reservation on sales order lines is enabled](#further-settings-if-inventory-visibility-integration-with-reservation-offset-is-enabled)

## Sample use case for soft reservation

Soft reservations help organizations achieve a single source of truth for available inventory, especially during the order fulfillment process. This functionality is useful for organizations where the following conditions exist:

- The organization has at least two different systems that are directly taking outbound orders.
- The organization is very strict and wants to prevent double-booking of product inventory, which can happen if multiple systems are able to overbook the last piece of stock. This situation is prevented when all order systems can make instant soft reservation API calls to Inventory Visibility, which provides a single source of truth for inventory availability.

[<img src="media/inventory-visibility-soft-reservation.png" alt="Inventory Visibility soft reservation." title="Inventory Visibility soft reservation" width="720" />](media/inventory-visibility-soft-reservation.png)

The previous illustration shows how soft reservation works and highlights the following operations:

- Your initial inventory level is synced to Inventory Visibility from Microsoft Dynamics 365 Supply Chain Management.
- Soft reservations are posted from each of your order channels or systems to Inventory Visibility. Inventory Visibility validates inventory availability and tries to make a soft reservation. If soft reservation succeeds, Inventory Visibility adds to the soft reserved quantity, deducts from the available for reservation (AFR) quantity, and respond with a soft reservation ID.
- At this time, your physical inventory quantity remains the same.
- You can then sync either single or aggregated soft-reserved orders (order lines) into Supply Chain Management to make hard reservations and release to the warehouse or update the final inventory quantity.
- You can set the system to [offset soft reservations](#offset-scm) when physical inventory is updated in Supply Chain Management.

Soft reservations are usually created, consumed, and canceled by using API calls to the Inventory Visibility service.

> [!NOTE]
> You can optionally set up Supply Chain Management (and other third-party systems) to automatically offset the quantity that has been reserved by using Inventory Visibility. The offset quantity is deleted from the reservation records in Inventory Visibility.
>
> By default, the offset function is automatically turned on when you enable the soft reservation feature.

## <a name="turn-on"></a>Turn on and set up the reservation feature

To turn on the reservation feature, follow these steps.

1. Sign in to Power Apps and open **Inventory Visibility**.
1. Open the **Configuration** page.
1. On the **Feature Management** tab, turn on the *OnHandReservation* feature.
1. Sign in to your Dynamics 365 Supply Chain Management environment.
1. Go to the **[Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)** workspace and enable **either the** 
    - *Inventory Visibility integration with reservation offset* feature (requires version 10.0.22 or later).
    - or a newer feature *Inventory Visibility integration with soft reservation on sales order lines* feature (requires 10.0.33 or later)
> [!NOTE]
> The two features are **not compatiable**, please only enable one. For new users implementing soft reservation feature with system version 10.0.33 and above, please turn on *Inventory Visibility integration with soft reservation on sales order lines* directly.
>Existing soft reservation users who are currently on *Inventory Visibility integration with reservation offset* feature, if you don't have requirement to make direct soft reservation from Dynamics 365 SCM sales orders, you can stay with current version and if you do have such requirement you may consider migrating to the new feature. 
>
### Further settings if *Inventory Visibility integration with soft reservation on sales order lines* is enabled
1.Stay in your Dynamics 365 Supply Chain Management environment
1.Go to **Inventory Management \> Setup \> Inventory Visibility integration parameters**, open the **Enable soft reservation** tab, select the soft reservation block level that is applicable to sales order lines.
    - *Block* means you can not process the sales order to hard reservation (reserve physical) or further if there is no successful soft reservation to IV for this line.
    - *Warning* will display a warning message is no soft reservation record if found but still allow you to proceed.
    - *Ignore* will not do any soft reservation check and allows you to proceed
 1. There is no need to enable and set up offset modifier as offset for soft reservation is always enabled and will be triggered when the sales line if proceeded to hard reservation status or further if hard reservation step is skipped.

### Further settings if *Inventory Visibility integration with reservation offset* is enabled
1. Go to **Inventory Management \> Setup \> Inventory Visibility integration parameters**, open the **Reservation offset** tab and make the following settings:

    - **Enable reservation offset** – Set to *Yes* to enable this functionality.
    - **Reservation offset modifier** – Select the inventory transaction status that will offset reservations that are made in Inventory Visibility. This setting determines the order processing stage that triggers offsets. The stage is traced by the order's inventory transaction status. Select one of the following values:

        - *On order* – Orders that have an *On order* status will send an offset request when they're created. The offset quantity will be the quantity of the created order (line).
        - *Reserve* – Orders that have a *Reserve* status will send an offset request when they're either order reserved or physically reserved. When you offset at the *Reserve* status, the order will send an offset request at any new inventory status that's closest to reserved picked (for example, pick, packing-slip posted, or invoiced). This behavior occurs even if you skip the reservation in Supply Chain Management and continue to another inventory status (for example, if you skip from release to warehouse to pick and pack). The request will be triggered only once. If it's been triggered at pick, it won't duplicate the offset when a packing slip is posted. The offset quantity will be the same as the quantity of the inventory transaction status when the offset was triggered (in other words, *Reserved ordered*/*Reserve Physical*, or a later status, on the corresponding order line).
## Common settings in Inventory Visibility app
1. Sign back in to the Inventory Visibility app, go to the **Configuration** page, and then, on the **Soft Reservation** tab, review the default soft reservation hierarchy. Add new dimensions to the hierarchy as required.
1. In the **Set Soft Reservation Mapping** section, view the default settings. By default, the soft-reserved inventory quantities will be recorded against the `softreservephysical` physical measure of the data source `iv`. The *Available for reservation* calculated measure is mapped to `availabletoreserve`. If you want to update the `availabletoreserve` calculated measure, go to the **Configuration** page, and then, on the **Calculated Measure** tab, expand and modify the calculated measure.

For more information, see [Configure Inventory Visibility](inventory-visibility-configuration.md).

> [!NOTE]
> The reservation hierarchy describes the sequence of dimensions that must be specified when reservations are made. It works in the same way that the index hierarchy works for on-hand queries, but it's used independently so that users can specify dimension details to make more precise reservations.
>
> Your soft reservation hierarchy should contain `SiteId` and `LocationId` as components, because they construct the partition configuration of Inventory Visibility.

For more information about how to configure reservations, see [Reservation configuration](inventory-visibility-configuration.md#reservation-configuration).

## Use the reservation feature in Inventory Visibility

When you call the reservation API, the system marks the reservation of the specified goods and quantities.

Here's an example scenario and a sample API query body. The company Contoso sells product D0002 (Cabinet) from its e-commerce website. A customer places a sales order for a small red cabinet via the website. Contoso decides to fulfill this order by using the following dimensions:

- Organization ID = usmf
- Site = 1
- Warehouse = 11
- Product = D0002
- Color = red
- Size = small

Contoso has already set up an API connection to Inventory Visibility from its own e-commerce system. When the order is received, the system instantly triggers an API call to make a soft reservation for the cabinet in Inventory Visibility.

### Create soft reservations using the reservation API

Reservations are made in the Inventory Visibility service by submitting a POST request to the service's URL, such as `/api/environment/{environmentId}/onhand/reserve`.

For a reservation, the request body must contain an organization ID, a product ID, reserved quantities, and dimensions.

When you call the reservation API, you can control the reservation validation by specifying the Boolean `ifCheckAvailForReserv` parameter in the request body. A value of `True` means that the validation is required, whereas a value of `False` means that the validation isn't required. The default value is `True`.

If you want to cancel a reservation or unreserve specified inventory quantities, set the quantity to a negative value, and set the `ifCheckAvailForReserv` parameter to `False` to skip the validation.

Here's an example of the request body that references the sales order in the previous context.

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

A successful soft reservation request returns a *soft reservation ID* for each reservation record. The soft reservation ID isn't a unique identifier for an individual soft reservation record, but a combination of the product ID and dimension values that are associated with the soft reservation request. You can record the soft reservation ID on the order line when you sync the successfully reserved orders to Supply Chain Management or another ERP system for offset.

## <a name="reserve-scm"></a>Using soft reservation and offset in Dynamics 365 Supply Chain Management

You are able to trigger soft reservation from Dynamics 365 Supply Chain Management sales order and make offset back to Inventory Visibility when the order lines are hard reserved (in the status of reserve physical, reserve ordered, picked, etc).
### Guide on *Inventory Visibility integration with soft reservation on sales order lines*
With this feature you can post soft reservation and also offset soft reservation from sales order lines in Dynamcis 365 SCM. The offset capabilities in this feature supports both sales lines that are created **internally** and **externally**.

1. Sign in into Supply Chain Management
1. Go to **Sales and marketing \> Sales Orders \> All Sales Orders**.
1. On the Action Pane, select **New**, proceed to create a new order and new sales lines. Make sure to populate product ID,site, warehouse and quantity. Specify other inventory dimension values if applicable.
1. You have two options to make soft reservation from sales orders
    - Create soft reservations on the sales order level to include all the lines in the order. To do this select **Inventory Visibility Integration \> Soft Reservation**. Choose **Reserve entire order directly** to make instant soft reservation API call to Inventory Visibility service, or **Reserve entire order by batch** to put the sales lines' reservation requests in a batch queue which is associated with a sync batch job between Dynamics 365 to Inventory Visibiloity approximately once per minute.
    - Create soft reservation on specific line. To do this, select the specific line, go to **Inventory \> Inventory Visibility Integration \> Soft reserve**. On the new pop up **Inventory service reservation details** screen, choose either reserve direct or by batch. On the details screen you will see a list of columns with quantity changes recorded
        - **Unreserved** - this column records the quantity that has not been soft reserved
        - **Soft reserve success** - this is the quantity that have been successfully soft reserved
        - **Batch reserve in progress** - this is the quantity that have been added to soft reservation batch queue
        - **Direct reserve in progress** - this is the quantity that have triggered instant soft reservation API call to inventory visibility
        - **Failed - not enough stock** - this is the quantity that has been soft reserved failed due to unavailable stock
        - **Failed - other reason** - this is the quantity that has been soft reserved due to all other reasons uncluding faled API processing/internet issue, etc.
        - **Offset quantity** - this is the total offset quantity on the line that includes both offset success and in progress quantities.
        - **Pending to offset quantity** - this is the quantity on the line that has skipped soft reservation and directly proceeded to hard reservation/further physical inventory consumptions
1. You can also revert a successful soft reservation by selecting **Resert reservation directly** or **Revert reservation by batch** from the same menu on Sales order or sales line level
1. Go back to the sales order lines. On the **Line details \> General \> Inventory Visibility Integration** you can view and edit the soft reservation block level of sales line if needed. If your company wide's default setting is block or warning, we strongly advise you not to ignore the soft reservation validation to avoid risk of oversell unless permitted in your business.
1. On the same place you can also see the Soft reservation status on the line
1. Once a soft reservation is success, soft reservation id will be automatically returned and recorded per sales line.
1. As by default the soft reservation offset trigger point is hooked at hard reservation (reserv physical/reserv ordered) or beyond status. Sales lines that have a valid soft reservation id populated and is at the right tigger status will autimcatically be added to offset batch queue
1. You can check failed to offset record in Dynamics 365 SCM **Inventory Management\>Periodic tasks\>Inventory Visibility integration**. Failed offset might be caused by incorrect soft reservation id, or internet issue, broken system connection, etc.

### Guide on *Inventory Visibility integration with reservation offset* 
You cannot trigger directly soft reservation within Dynamcis 365 SCM with this feature, this feature supports to offset sales order lines that are orginally created **externally only** of Dynamics 365 SCM and also soft reserved to IV outside of Dynamics 365. When these externally soft reserved sales lines are replicated into Dynamics 365 SCM, offsets might required from Dynamics 365 SCM to Inventory Visibility.

You can offset a soft-reserved quantity after the quantity on an order is physically deducted in Supply Chain Management or another ERP system. Inventory Visibility offers out-of-box soft reservation offset integration with Supply Chain Management.

Follow these steps to offset a soft reservation.

1. Sign in to Supply Chain Management.
1. Go to **Sales and marketing \> Sales Orders \> All Sales Orders**.
1. On the Action Pane, select **New**. Proceed to create a new order and new sales line.
1. Re-create the external sales order, and add a sales line that uses the exact same product ID, organization, site, warehouse, and dimensions values.
1. On the **Sales order lines** FastTab, select the sales line that you just entered, and then, on the toolbar, select **Inventory \> Reservation ID**.
1. Follow one of these steps:

    - Copy the soft reservation ID in your soft reservation request response, and paste it into the **Reservation ID** field.
    - Leave the **Reservation ID** field blank, but select the **Inventory service auto offset** checkbox. The system will automatically determine which product and product dimensions to offset, based on the item ID and dimension values that are entered on the selected line.

1. Select **OK**.
1. While the same sales line is still selected, physically reserve the ordered quantity by selecting **Inventory \> Reservation** on the toolbar of the **Sales order lines** FastTab.
1. If you've previously set the **Reservation offset modifier** field to *Reserved*, the offset will be triggered when the order line has a status of *Reserve physical* or *Reserve ordered*. A batch job runs once a minute to sync offset requests from Supply Chain Management to Inventory Visibility.
1. You can check failed to offset record in **Inventory Management\>Periodic tasks\>Inventory Visibility integration**. Failed offset might be caused by incorrect soft reservation id, or internet issue, broken system connection, etc.

> [!NOTE]
> For transaction statuses that include a specified reserve offset modifier, the transaction update will offset the corresponding reservation record when all the following conditions are met:
>
> - The reservation ID on the inventory transaction matches the reservation ID of the reservation record in Inventory Visibility.
> - The dimensions of the inventory transaction match the dimensions of the reservation record in Inventory Visibility.
> - Changes in inventory transaction status trigger offsets for reservations when the inventory transaction status reflects the fact that an order process has been completed or skipped.

Offset quantities follow the inventory quantities that are specified on the relevant inventory transactions. An offset will take effect only if reserved quantity remains in Inventory Visibility.

### Cancel or revert a soft reservation

If an original order line is canceled or deleted, and you must revert the corresponding soft reservation, post a negative quantity that has the exact same information in your API query body.
