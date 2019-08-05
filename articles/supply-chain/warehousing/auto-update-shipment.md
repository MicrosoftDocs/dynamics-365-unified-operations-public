---
# required metadata

title: Shipment auto-updates
description: This topic provides an overview of functionality providing auto-updates for shipments.
author: josaw1
manager: AnnBe
ms.date: 08/05/2019
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

## What determines changes in status

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

- **Add a new order line:** When the **Auto update shipment** paramater, located on the **Warehouse** FastTab on the **Warehouse management > Setup > Warehouse > Warehouses** page, is set to
**Always**, a shipment exists for the order, and a new order line is added to
a sales or transfer order while a load has already been created for the sales
order, the existing load will not be updated. A new load line with no
reference to the existing load will be created and associated with the existing
shipment.

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

1. Go to **Warehouse management > Setup > Warehouse > Warehouses**. Select "Warehouse 24". 
1. Expand the **Warehouse** FastTab. Change the **Auto update shipment** parameter from **On quantity decrease** to **Always**.

Once you change the policy to "Always", any
increase or decrease to the sales and transfer order line quantities
(including adding new lines) will be reflected on shipments and loads for the
specific warehouse.

Change wave template to not automatically process, navigate to Warehouse
management Setup Waves Wave templates. Select wave template **24 Shipping
default**. In the **General** fast tab edit, such that **only** the **Automate
wave creation** parameter is Yes. All others must be set to No.

Note: *It is important that no work is automatically created and subsequently
released as part of the wave creation process. Once work is created relative to
the load line created for the sales order line, then the load line will no
longer be updated automatically from a sales order line quantity change.*

Create a sales order, navigate to Sales and marketing Sales orders all sales
orders. Select customer US-003. Create a line for item number A0001, quantity
10. Ensure that the warehouse is 24. Reserve the quantity and release to
warehouse. A shipment and a wave will be created. Due to the wave template
change, no load and no work are created. The status of the shipment is open, and
the status of the wave is created.

Decrease the quantity on the sales order line, navigate to Sales and marketing
Sales orders all sales orders. Select the sales order that you just released to
warehouse. Change the line quantity from 10 to 8. From the sales order line,
navigate to action pane Warehouse Shipment details. In the Shipment details
form, fast tab Load Lines the quantity is reflecting the change on the sales
order line.

Increase the quantity on the sales order line, navigate to Sales and marketing
Sales orders all sales orders. Select the sales order that you just released to
warehouse. Change the line quantity from 8 to 12. From the sales order line,
navigate to action pane Warehouse Shipment details. In the Shipment details
form, fast tab Load Lines the quantity is reflecting the change on the sales
order line.

*Note: Even though the load line quantity is increased from 8 to 12, only 8
remain reserved unless you enable automatic reservation. As the added quantity
to the existing shipment has not been reserved, subsequently processing the wave
without reservation will only create work for the already reserved quantity.*

*Note: For order line quantity decrease, if the load line quantity is already
equal to or lower than the new order line quantity, then load line quantity is
unaffected. For order line quantity increase, the load line is increased by same
quantity as the order line. If there is a discrepancy between order line and
load line quantity that discrepancy will remain.*

Add a new sales order line, navigate to Sales and marketing Sales orders all
sales orders. Select the sales order that you just released to warehouse. Create
a line for item number A0002, quantity 10. Ensure that the warehouse is 24. As
the warehouse is 24, the new line will automatically be added to the existing
shipment. From the sales order line, navigate to action pane Warehouse Shipment
details. In the Shipment details form, fast tab Load Lines, notice the second
load line.

*Note: As the new sales order line added to the existing shipment has not been
reserved, subsequently processing the wave as-is will create work for the
quantity for the first sales order line/ first load line only.*

Process the wave, navigate to Warehouse management Outbound waves Shipment waves
All Waves. Select the wave created previously. Navigate to ribbon Wave pane Wave
(action) Process. Process the wave.

*Note: The wave will process and create work for the reserved quantities for the
load lines. The shipment status will transition from Open to Waved.*

As the shipment status is updated to waved, any line quantity decrease, increase
or new line added to the sales order will not impact the existing load lines
associated with the waved shipment.

*Note: Sales order line quantity updates will not be reflected on or validated
against a load line associated with a shipment in status waved or higher.
Changes to the load line quantity must be done directly on the load line. Update
validation in the scenario is performed when work has been created for the load
line and reservations made. Then a decrease in the sales order line quantity is
validated against work line reservation.*

Add new order line. Create a **new** sales order, navigate to Sales and
marketing Sales orders all sales orders. Select customer US-003. Create a line
for item number A0001, quantity 5. Ensure that the warehouse is 24. Reserve the
quantity and release to warehouse. A shipment and a wave will be created. Due to
the wave template change, no load and no work are created. The status of the
shipment is open, and the status of the wave is created. As you want to manually
start preparing the load, navigate to Sales and marketing ribbon Warehouse Loads
Load planning workbench (action). In the **Load planning workbench** form with
the sales line selected, navigate to Load planning workbench ribbon **Supply and
Demand** Add To new load. Select any load template ID and proceed adding the
sales line to a new load.

*Note: In such a scenario, it is possible to transfer the new load line to the
existing load for consolidation in the shipment details form.*
