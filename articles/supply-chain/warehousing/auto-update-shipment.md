---
# required metadata

title: Shipment auto-updates
description: This topic provides an overview of functionality providing auto-updates for shipments.
author: josaw1
manager: AnnBe
ms.date: 08/13/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2019-08-31
ms.dyn365.ops.version: 10.0.5

---

# Shipment auto-updates

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

Auto-update shipment functionality automatically updates quantities--increases
as well as decreases--on a load line associated with a shipment after it’s been
released to a warehouse. This functionality is enabled for as long as the load line on the
shipment or load has not been processed on a wave. The functionaltity
will allow any order updates to automatically flow through to the warehouse
without manual intervention for as long as warehouse work hasn’t been created.

Without the auto-update functionality, only quantity decreases will automatically flow, as
long as warehouse work hasn’t been created. Users have to manually update or delete lines and then re-release
lines if order quantities increase or new order lines are added. With the auto-update functionality, the business can
seamlessly provide updates to the warehouse without having to worry about order
line updates not being reflected on related shipments and loads. 

The auto-update shipment functionality applies to sales order lines and transfer order lines and is enabled for a specific warehouse. This allows a company to
apply different auto update shipment policies across warehouses, when required.
By default, the auto update shipment policy applied for all warehouses that use
warehouse management process is for quantity decrease. With this policy
setting, only quantity decreases automatically flow through to a shipment and
load as long as warehouse work hasn’t been created. This is similar to
legacy behavior without the functionality.

## Key elements in functionality

The auto-update shipment functionality relies foremost on the shipment status
to determine whether a change to the quantity on a load line should occur when a
change is made on a sales and transfer order line. It also relies foremost on shipment status to determine when to add a new load
line automatically to an existing load. When the shipment status is waved or
higher, no automatic update takes places.

Wave status is also considered for auto-updates. When the wave
related to the load line has a status of held, executing, released, picked, or shipped, and the user attempts to reduce the quantity on a load line (via a
quantity decrease on the sales or transfer order line), the user will receive
the following error message: “Reservations cannot be removed because there is work created which
relies on the reservations.” Similarly, if attempting to increase
the load line quantity with the above wave statuses indirectly by decreasing quantity on the
sales or transfer order line, the load line will not automatically be increased. In this scenario, the load line must be updated manually.

## Scenarios
The following four scenarios are supported by auto-update shipment functionality: add a new order line,
increase the line quantity, decrease the order line quantity, and remove an order line.

- **Add a new order line:** When the **Auto update shipment** parameter, located on the **Warehouse** FastTab on the **Warehouse management > Setup > Warehouse > Warehouses** page, is set to
**Always**, a shipment exists for the order, and a new order line is added to
a sales or transfer order while a load has already been created for the sales
order, the existing load will not be updated. A new load line with no
reference to the existing load will be created and associated with the existing
shipment. The new line will be added to the load and released. 

- **Increase order line quantity:** When the parameter **Auto update shipment**
is set to **Always**, a shipment exists for the order, and the quantity on an
existing sales or transfer order line is increased while a load has already
been created for the sales order, the load line will be increased by the same
quantity as the order line. If the load was released but no
work was created, the load line will be increased by the same quantity as the order
line.

- **Decrease order line quantity:** When the parameter **Auto update shipment**
is set to **Always** or **On quantity decrease**, a shipment exists for the order,
and the quantity on an existing sales or transfer order line is decreased
while a load has already been created for the sales order, the
associated load line quantity will be updated to match, unless the load line is
already equal to or lower than the new order line quantity. In that case, the
load line will not be affected. If the load has been released but no
work was created, the associated load line quantity will be updated to
match, unless the load line is already equal to or lower than the new order line
quantity. In that case, the load line will not be affected.

- **Remove order line:** When the parameter **Auto update shipment** is set to
**Always** or **On quantity decrease**, and the user attempts to remove an order
line for which a load line exists, then an error message is shown.

## Demo

For this demo, you need to have demo data installed, and use demo data company USMF.

### Enable shipment auto-updates

To enable shipment auto-updates, do the following.

1. Go to **Warehouse management > Setup > Warehouse > Warehouses**. 
1. Select "Warehouse 24". 
1. Expand the **Warehouse** FastTab. Change the **Auto update shipment** parameter from **On quantity decrease** to **Always**.

Once you change the policy to "always", any
increase or decrease to the sales and transfer order line quantities
(including adding new lines) will be reflected on shipments and loads for the
specific warehouse given the before mentioned update constraints.

### Change wave template to not automatically process

To configure the wave template so it doesn't automatically process, do the following.

1. Go to **Warehouse management > Setup > Waves > Wave templates**. 
1. Select the wave template "24 Shipping default". 
1. Click **Edit**.
1. In the **General** FastTab, set the **Automate wave creation** parameter to **Yes** and make sure all other parameters are set to **No**. 

It's important that there's no work that's automatically created and released as part of the wave creation process. Once work is created relative to the load line created for the sales order line, the load line will no
longer be updated automatically from a sales order line quantity change.

### Create a sales order

To create a sales order, do the following.

1. Go to **Sales and marketing > Sales orders > All sales orders**. 
1. Select customer "US-003". 
1. Create a line for item number "A0001".
1. Enter a quantity of "10". (Make sure you are using warehouse "24".)
1. Click **Save**.
1. Click **Warehouse**, and under **Actions**, click **Release to warehouse**. A shipment and a wave will be created.

Because the wave template was modified in the steps above, no load or work will be created. The shipment status will be "open", and the wave status will be "created".

### Decrease quantity on a sales order line

To decrease the quantity on a sales order line, do the following.

1. Go to **Sales and marketing > Sales orders > All sales orders**. 
1. Select the sales order that you just released to the warehouse. 
1. Select the sales order line. In the **Quantity** field, change the value from "10" to "8". 
1. From the sales order line, go to **Warehouse > Shipment details**. 
1. On the **Shipment details** page, on the **Load lines** FastTab, the quantity reflects the change on the sales order line.



### Increase quantity on a sales order line

To increase the quantity on a sales order line, do the following.

1. Go to **Sales and marketing > Sales orders > All sales orders**.
1. Select the sales order that you just released to the warehouse.
1. Change the line quantity from "8" to "12". 
1. Click **Save**.
1. Go back to **Sales and marketing > Sales orders > All sales orders** and select the sales order. Click **Warehouse** and under **Related information** click **Shipment details**. 
1. On the **Shipment details** page, the quantity on the **Load lines** FastTab reflects the change on the sales order line.

Even though the load line quantity is increased from "8" to "12", only 8 items will remain reserved unless automatic reservation is enabled. If the wave is processed at this point, work will only be created for the reserved quantity.

> [!NOTE]
> When an order line is decreased, the load line quantity will not be affected if the load line quantity is already equal to or lower than the new order line quantity. When an order line is increased, the load line will be increased by the same
quantity as the order line. If there is a discrepancy between the order line quantity and the load line quantity, the discrepancy will remain. Even though the load line quantity is increased from 8 to 12 in the example above, only 8 remain reserved unless you enable automatic reservation. As the added quantity to the existing shipment has not been reserved, subsequently processing the wave without reservation will only create work for the already reserved quantity.

### Add a sales order line

To add a sales order line, do the following.

1. Go to **Sales and marketing > Sales orders > All sales orders".
1. Select the sales order that you just released to the warehouse. 
1. Create a line for item number "A0002".
1. In the **Quantity** field, enter "10". (Make sure you are using warehouse "24".) The new line will automatically be added to the existing shipment. 
1. Click **Save**.
1. Go back to **Sales and marketing > Sales orders > All sales orders** and select the sales order. Click **Warehouse** and under **Related information** click **Shipment details**. 
1. On the **Shipment details** page, on the **Load lines** FastTab, take note of the second load line.

Because the new sales order line added to the existing shipment wasn't reserved, processing the wave at this point will create work only for the quantity for the first sales order line/first load line.

### Process a wave

To process the wave, do the following.

1. Go to **Warehouse management > Outbound waves > Shipment waves > All waves**. 
1. Select the wave that you previously created.
1. Click **Wave** and then under **Wave**, click **Process*. 

The wave will process and create work for the reserved quantities for the
load lines. The shipment status will transition from "open" to "waved". As the shipment status is updated to "waved", any changes such as line quantity decrease, increase, or new line added to the sales order won't impact the existing load lines associated with the waved shipment.

Sales order line quantity updates won't be reflected on or validated against a load line associated with a shipment with the status of "waved" or higher. Changes to the load line quantity must be done directly on the load line. 

Validation is performed when work has been created for the load
line and a reservation has been made. A decrease in the sales order line quantity is then  validated against the work line reservation.

