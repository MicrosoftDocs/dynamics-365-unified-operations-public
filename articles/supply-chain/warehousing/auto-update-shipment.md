---
# required metadata

title: Shipment auto-updates
description: This topic provides an overview of functionality that provides automatic updates for shipments.
author: Mirzaab
ms.date: 11/04/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSWaveTemplateTable,SalesTableListPage,SalesTable,WHSWaveTableListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2019-08-31
ms.dyn365.ops.version: 10.0.5

---

# Shipment auto-updates

[!include [banner](../includes/banner.md)]

The auto-update shipment functionality automatically updates quantities (both increases and decreases) on a load line that is associated with a shipment, after the load has been released to a warehouse. This functionality remains turned on until the load line on the shipment or load is processed on a wave. When it's used, order updates can automatically flow through to the warehouse, without requiring manual intervention, until warehouse work is created.

When the auto-update shipment functionality isn't used, only quantity decreases automatically flow until warehouse work is created. Users must manually update or delete lines, and they must then re-release lines if order quantities are increased or new order lines are added. By using the auto-update shipment functionality, businesses can seamlessly provide updates to the warehouse without having to worry that related shipments and loads won't reflect order line updates.

The auto-update shipment functionality applies to both sales order lines and transfer order lines, and it's turned on for a specific warehouse. Therefore, companies can apply different auto-update shipment policies across warehouses, as they require. By default, the auto-update shipment policy for quantity decreases is applied for all warehouses that use warehouse management processes. When this default policy setting is used, only quantity decreases automatically flow through to a shipment and load until warehouse work is created. This behavior resembles the behavior that was used before the auto-update shipment functionality was introduced.

## Main elements of the functionality

The auto-update shipment functionality relies primarily on the shipment status to determine whether the quantity on a load line should be changed when a change is made on a sales order line or transfer order line. It also relies primarily on the shipment status to determine when a new load line should automatically be added to an existing load. When the shipment status is **Waved** or higher, no automatic update occurs.

Wave status is also considered for automatic updates. When the wave that is related to the load line has a status of **Held**, **Executing**, **Released**, **Picked**, or **Shipped**, if a user tries to reduce the quantity on a load line (via a quantity decrease on the sales order line or transfer order line), the following error message is shown: "Reservations cannot be removed because there is work created which relies on the reservations." Additionally, when the wave has one of the previously mentioned wave statuses, if a user tries to indirectly increase the load line quantity by increasing the quantity on the sales order line or transfer order line, the quantity on the load line isn't automatically increased. In this case, the load line must be manually updated.

## Scenarios

The auto-update shipment functionality supports four scenarios: adding a new order line, increasing the quantity on an order line, decreasing the quantity on an order line, and removing an order line.

- **Add a new order line** – When the **Auto update shipment** field on the **Warehouse** FastTab of the **Warehouses** page (**Warehouse management \> Setup \> Warehouse \> Warehouses**) is set to **Always**, if a shipment exists for the order, and a new order line is added to a sales order or transfer order after a load has already been created for the sales order, the existing load isn't updated. A new load line that has no reference to the existing load is created and associated with the existing shipment. The new line is added to the load and released.
- **Increase the quantity on an order line** – When the **Auto update shipment** field is set to **Always**, if a shipment exists for the order, and the quantity on an existing sales order line or transfer order line is increased after a load has already been created for the sales order, the load line is increased by the same quantity as the order line. If the load was released, but no work was created, the load line is increased by the same quantity as the order line.
- **Decrease the quantity on an order line** – When the **Auto update shipment** field is set to **Always** or **On quantity decrease**, if a shipment exists for the order, and the quantity on an existing sales order line or transfer order line is decreased after a load has already been created for the sales order, the quantity on the associated load line is updated to match, unless the quantity on that load line already equals or is less than the new quantity on the order line. In that case, the load line isn't affected. If the load was released, but no work was created, the quantity on the associated load line is updated to match, unless the quantity on the load line already equals or is less than the new quantity on the order line. In that case, the load line is affected.
- **Remove an order line** – When the **Auto update shipment** field is set to **Always** or **On quantity decrease**, if the user tries to remove an order line that a load line exists for, an error message is shown.

## Example scenario

For this scenario, you must have demo data installed, and you must use the **USMF** demo data company.

### Turn on the auto-update shipment functionality

To turn on the auto-update shipment functionality, follow these steps.

1. Go to **Warehouse management \> Setup \> Warehouse \> Warehouses**.
2. Select warehouse **24**.
3. On the **Warehouse** FastTab, in the **Auto update shipment** field, change the value from **On quantity decrease** to **Always**.

After you change the value to **Always**, any increases or decreases in the quantities on sales order lines and transfer order lines, and any additions of new lines, are reflected on shipments and loads for the selected warehouse, given the previously mentioned update constraints.

### Change the wave template so that load lines aren't automatically processed

To configure the wave template so that it doesn't automatically process load lines, follow these steps.

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
2. Select wave template **24 Shipping default**.
3. Select **Edit**.
4. On the **General** FastTab, set the **Automate wave creation** option to **Yes**, and make sure that all other options are set to **No**.

It's important that no work be automatically created and released as part of the wave creation process. After work is created that is related to the load line that was created for the sales order line, the load line is no longer automatically updated if the quantity on the sales order line is changed.

### Create a sales order

To create a sales order, follow these steps.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
2. Select customer **US-003**.
3. Create a line for item number **A0001**.
4. Enter a quantity of **10**. (Make sure that you're using warehouse **24**.)
5. Select **Save**.
6. On the Action Pane, on the **Warehouse** tab, in the **Actions** group, select **Release to warehouse**. A shipment and a wave are created.

Because you changed the wave template in the previous procedure, no load or work is created. The shipment status is **Open**, and the wave status is **Created**.

### Decrease the quantity on a sales order line

To decrease the quantity on a sales order line, follow these steps.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
2. Select the sales order that you just released to the warehouse.
3. Select the sales order line. In the **Quantity** field, change the value from **10** to **8**.
4. From the sales order line, select **Warehouse \> Shipment details**. On the **Shipment details** page, on the **Load lines** FastTab, the quantity reflects the change on the sales order line.

### Increase the quantity on a sales order line

To increase the quantity on a sales order line, follow these steps.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
2. Select the sales order that you previously released to the warehouse.
3. Change the line quantity from **8** to **12**.
4. Select **Save**.
5. Go back to the **All sales orders** page, and select the sales order again.
5. On the Action Pane, on the **Warehouse** tab, in the **Related information** group, select **Shipment details**. On the **Shipment details** page, on the **Load lines** FastTab, the quantity reflects the change on the sales order line.

Although the quantity on the load line was increased from 8 to 12, only eight items remain reserved, unless automatic reservation is turned on. Because the quantity that was added to the existing shipment hasn't been reserved, if the wave is processed at this point, without reservation, work is created only for the quantity that has already been reserved.

> [!NOTE]
> When the quantity on an order line is decreased, the quantity on the load line isn't affected if it already equals or is less than the new quantity on the order line. When the quantity on an order line is increased, the load line is increased by the same quantity as the order line. If the quantity on the order line differs from the quantity on the load line, the difference remains.

### Add a sales order line

To add a sales order line, follow these steps.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
2. Select the sales order that you previously released to the warehouse.
3. Create a line for item number **A0002**.
4. In the **Quantity** field, enter **10**. (Make sure that you're using warehouse **24**.) The new line is automatically added to the existing shipment.
5. Select **Save**.
6. Go back to the **All sales orders** page, and select the sales order again.
7. On the Action Pane, on the **Warehouse** tab, in the **Related information** group, select **Shipment details**. On the **Shipment details** page, on the **Load lines** FastTab, notice the second load line.

Because the sales order line that you just added to the existing shipment hasn't been reserved, if the wave is processed at this point, work is created only for the quantity on the first sales order line and the first load line.

### Process a wave

To process the wave, follow these steps.

1. Go to **Warehouse management \> Outbound waves \> Shipment waves \> All waves**.
2. Select the wave that you previously created.
3. On the Action Pane, on the **Wave** tab, in the **Wave** group, select **Process**.

The wave is processed and creates work for the reserved quantities on the load lines. The shipment status is updated from **Open** to **Waved**. As the shipment status is updated to **Waved**, any changes that occur, such as decreases or increases in line quantities, or the addition of new lines to the sales order, don't affect the existing load lines that are associated with the waved shipment.

If a shipment has a status of **Waved** or higher, updates to the quantity on a sales order line aren't reflected on or validated against a load line that is associated with the shipment. Changes to the quantity on a load line must be made directly on the load line.

Validation is done after work has been created for the load line and a reservation has been made. A decrease in the quantity on the sales order line is then validated against the work line reservation.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]