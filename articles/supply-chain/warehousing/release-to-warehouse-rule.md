---
title: Release to warehouse rule
description: Learn about about the Release to warehouse rule feature, which provides flexibility during release to the warehouse, including a step-by-step process.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 06/07/2024
ms.custom:
  - bap-template
ms.reviewer: kamaybac
ms.search.form: WHSParameters
---

# Release to warehouse rule

[!include [banner](../includes/banner.md)]

The *Release to warehouse rule* feature provides flexibility during release to the warehouse. It adds a configuration option for each warehouse. You can use this option to specify whether partially reserved order lines can be released for that warehouse. The feature works together with advanced cross-docking functionality in situations where part of an order line quantity is marked against a supply source, but the remaining part can be processed in the warehouse. Therefore, the line can be released so that warehouse processing of the available inventory quantity can continue.

## <a name="set-option-warehouse"></a>Set the release to warehouse rule for each warehouse

To set the release to warehouse rule for each warehouse, follow these steps.

1. Go to **Warehouse management \> Setup \> Warehouse \> Warehouses**.
1. Select the warehouse to configure.
1. Select **Edit** to put the page into edit mode.
1. On the **Warehouse** FastTab, in the **Reservations** section, the **Requirement for inventory reservation** field controls whether partial release of orders is allowed. Select one of the following values:

    - *Not applicable* – When the feature is first turned on and initialized, this value is automatically assigned to all warehouses that aren't enabled for warehouse management. It can't be changed. This value isn't available for warehouses that are enabled for warehouse management.
    - *Allow partial reservation* – Order lines can be released when any quantity is reserved. The system will evaluate whether the unreserved quantity should be marked for advanced cross-docking and will mark that quantity as required. If no marking exists, the system will create work only for the reserved quantity. When the feature is first turned on and initialized, this value is automatically assigned to all warehouses that are enabled for warehouse management. This value isn't available for warehouses that aren't enabled for warehouse management.
    - *Require full reservation* – Order lines can be released only if the whole quantity is reserved. They can't be released if the total quantity isn't either physically reserved or planned for cross-docking. This value isn't available for warehouses that aren't enabled for warehouse management.

1. Select **Save**.

## Scenarios

This section provides two scenarios that you can work through to learn what the feature does and how to use it.

### Make sample data available

To work through these scenarios by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

You can also use these scenarios as guidance for the feature when you work on a production system. However, in that case, you must substitute your own values, and you might be missing some types of required records that the standard demo data provides.

### <a name="scenario1"></a>Scenario 1: Require full release (no planned cross-docking)

This scenario shows how the feature works for warehouses that are set to **Require full reservation**.

1. Go to **Warehouse management \> Setup \> Warehouse \> Warehouses**.
1. For warehouse *62*, set the **Requirement for inventory reservation** field to **Require full reservation**, as described in the [Set the release to warehouse rule for each warehouse](#set-option-warehouse) section earlier in this article.
1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New** to create a sales order.
1. In the **Create sales order** dialog box, set the following values:

    - On the **Customer** FastTab, set the **Customer account** field to *US-004*.
    - On the **General** FastTab, set the **Warehouse** field to *62*.

1. Select **OK** to create the new sales order and close the dialog box.
1. Your new sales order is opened. It includes an empty line in the grid in the **Sales order lines** section. On this line, set the following values:

    - **Item number:** *A0001*
    - **Quantity:** *2*

1. Select **Add line** to add a new line, and set the following values:

    - **Item number:** *A0002*
    - **Quantity:** *2*

1. Select the first order line, and then, on the **Inventory** menu above the grid, select **Reservation**.
1. On the **Reservation** page, select **Reserve lot** to reserve the selected line's full quantity in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. Don't reserve the second order line.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.
1. Notice that you receive the following error message: "The full quantity must be physically reserved." Therefore, the system doesn't create any work, shipment, or load for the order.

    > [!NOTE]
    > You will receive the same error message if you partially reserve the second line.

### Scenario 2: Allow partial release

This scenario shows how the feature works for warehouses that are set to **Allow partial release**.

1. Go to **Warehouse management \> Setup \> Warehouse \> Warehouses**.
1. For warehouse *62*, set the **Requirement for inventory reservation** field to **Allow partial reservation**, as described in the [Set the release to warehouse rule for each warehouse](#set-option-warehouse) section earlier in this article.
1. As you did in the [previous scenario](#scenario1), go to **Sales and marketing \> Sales orders \> All sales orders**, and create a sales order for customer account *US-004* from warehouse *62*. Add the following two order lines:

    - **Line 1:** Set the **Item number** field to *A0001*, the **Quantity** field to *2*, and the **Unit** field to *Pcs*.
    - **Line 2:** Set the **Item number** field to *A0002*, the **Quantity** field to *2*, and the **Unit** field to *Pcs*.

1. As you did in the [previous scenario](#scenario1), reserve the full quantity for order line 1, but don't reserve order line 2.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.
1. Notice that you don't receive an error message this time. Instead, the system creates work, shipments, and loads as required, and shows the results.
1. To view the shipment, load, and work information, use the options on the **Warehouse** menu above the grid:

    - **Line 1:** Three options are available: **Shipment details**, **Load details**, and **Work details**. Select each option to view the details of the shipment, load, and work that were created when the order was released to the warehouse.
    - **Line 2:** Only the **Work details** option is available. Select it, and notice that no work has been created, because no inventory was reserved. Therefore, no shipment or load was created either.

> [!NOTE]
> The same result is expected when the second line is partially reserved. In this case, work will be created for the reserved line quantity but not for the unreserved quantity.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
