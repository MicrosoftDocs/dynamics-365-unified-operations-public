---
# required metadata

title: Release to warehouse rule
description: Release to warehouse rule provides flexibility when releasing to warehouse. It serves as a defining setup parameter to determine whether release of partially reserved order lines is allowed by the system or not.
author: mirzaab
manager: AnnBe
ms.date: 02/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSParameters
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: Release 10.0.8
---

# Release to warehouse rule

The release to warehouse rule feature provides flexibility when releasing to the warehouse. It provides a configuration option for each warehouse, which lets you decide whether release of partially reserved order lines is allowed for that warehouse or not. It works hand-in-hand with advanced cross-docking functionality in situations where part of an order line quantity is marked against a supply source and the remaining part can be processed in the warehouse, thus allowing the the line to be released so warehouse processing of the available inventory quantity can continue.

## Enable release to warehouse rule

### Turn on the feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - Warehouse management
- **Feature name** - Warehouse release rule

### Initialize the feature

Once the feature is enabled on your system, you must initialize it to set the rule to the correct initial state for all warehouses.

- For warehouses that aren't enabled for warehouse management, the rule will initially be set to **Not applicable**. <!-- KAMAYBACH: how do we enable a warehouse for warehouse management? Do we have a link for this? (maybe https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/warehouse-management-overview ?) -->
- For warehouses that are enabled for warehouse management, the rule will initially be set to **Allow partial reservation**

To initialize the enable release to warehouse rule for all warehouses:

1. Go to **Warehouse management > Setup > Warehouse management parameters**.
1. Open the **General** tab of the **Warehouse management parameters** page.
1. In the **Company information** section, select **Initialize release to warehouse** rule. (If this link isn't shown, then the feature either isn't turned on or has already been initialized.)
1. You are prompted to confirm the action. Select **Yes** to initialize the feature.

<!-- HHM: <a name="set-option-warehouse"></a> -->

## Set the release to warehouse rule for each warehouse

On activating the feature, each of your warehouses will have an initial setting for it, as described in the previous section. You can now set this option as needed for each warehouse by doing the following:

1. Go to **Warehouse management > Setup > Warehouse > Warehouses**.
1. Select the warehouse you want to configure.
1. Select **Edit** to put the page into edit mode.
1. Expand the **Warehouse** FastTab.
1. In the **Reservations** section of the **Warehouse** FastTab, find **Requirement for inventory reservation** (Controls if partial release of orders is allowed. When set to Require full reservation, orders will not be able to be released if the total quantity is not either physically reserved or planned for cross docking)
1. Select one of the following options:
    - **Not applicable** – When the feature is first enabled an initialized, this value is automatically assigned to all warehouses that aren't enabled for warehouse management and can't be changed. You can't select this option for warehouses that are enabled for warehouse management.
    - **Allow partial reservation** – Allows orders to be released with any quantity reserved. The system will evaluate whether the unreserved quantity should be marked for advanced cross docking, and will mark that quantity as needed. If no marking exists, the system will only create work for the reserved quantity. When the feature is first enabled an initialized, this value is automatically assigned to all warehouses that are enabled for warehouse management. This option isn't available for warehouses that aren't enabled for warehouse management.
    - **Require full reservation** – Orders can only be released if the entire quantity is reserved. This option isn't available for warehouses that aren't enabled for warehouse management.
1. Select **Save**.

## Scenarios

This section provides two scenario scripts that you can work through to get a feel for what this feature does and how to work with it.

### Enable sample data

To work through these scenarios using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

You can also use these scenarios as guidance for how to use this feature when working on a production system, but then you must then substitute your own values, and you may be missing some types of required records that would otherwise be provided by the standard demo data.

<!-- HHM: <a name="demo1"></a> -->

### Scenario 1: Require full Release (no planned cross-docking)

This scenario illustrates how this feature works for warehouses set to **Require full reservation**.

1. Go to **Warehouse management > Setup > Warehouse > Warehouses** and set warehouse 62 to **Require full reservation**, as described in [Set the release to warehouse rule for each warehouse](#set-option-warehouse).
1. Go to **Sales and marketing > Sales orders > All sales orders**.
1. Select **New** to create a new sales order.
1. The **Create sales order** flyout opens. Make the following settings here:
    - On the **Customer** FastTab, set **Customer account** to "US-004".
    - On the **General** FastTab, set **Warehouse** to "62".
1. Select **OK** to create the new sales order and close the flyout.
1. Your new sales order opens. Add the following two order lines to the **Sales order lines** table:
    - ***Line 1***: Set **Item number** to *A0001*, and **Quantity** to *2*.
    - Select **Add line** in the **Sales order lines** action pane.
    - ***Line 2***: Set **Item number** to *A0002*, and **Quantity** to *2*.
1. Select the first order line, in the **Sales order lines** action pane open the **Inventory** drop-down list and select **Reservation**.
1. The **Reservation** page opens. Select **Reserve lot** to reserve your selected line's full quantity in the warehouse.
1. Close the **Reservation** page to return to your sales order.
1. Do not reserve the second order line.
1. In the **Sales orders** action pane select the **Warehouse** tab and select **Release to warehouse**.
1. Note that the following error is now shown: "The full quantity must be physically reserved." Therefore, the system doesn't create any work, shipment or load for the order.

> [!NOTE]
> The same error will be also shown when the second line is partially reserved.

### Scenario 2: Allow Partial Release

This scenario illustrates how this feature works for warehouses set to **Allow Partial Release**.

1. Go to **Warehouse management > Setup > Warehouse > Warehouses** and set warehouse *62* to **Allow partial reservation**, as described in [Set the release to warehouse rule for each warehouse](#set-option-warehouse).
1. As you did in the [previous scenario](#scenario1), go to **Sales and marketing > Sales orders > All sales orders**, create a new sales order for **Customer account** "US-004" from **Warehouse** "62", and add the following two order lines:
    - Line 1: Set **Item number** to "A0001", **Quantity** to "2", and **Unit** to "Pcs".
    - Line 2: Set **Item number** to "A0002", **Quantity** to "2", and **Unit** to "Pcs".
1. As you did in the [previous scenario](#scenario1), reserve the full quantity for order line 1, but don't reserve order line 2.
1. Open the **Warehouse** tab and select **Release to warehouse**.
1. Note that this time, no error is shown. Instead, the system creates work, shipments, and loads as required and displays the results.

1. To view the work, shipment and loads information, do the following from the **Sales order lines** action pane:

    - ***Line 1***: Select **Warehouse**, note that the three menu options are all activated, select each to view the details of the *Shipment*, *Load* and *Work* created when the order was released to the warehouse.
    - ***Line 2***: Select **Warehouse**, note that only *Work details* is active, select it to open. No work has been created because no inventory was reserved, therefore, no Shipment or Load was created either.

> [!NOTE]
> The same results is expected when the second line is partially reserved. In this case, work will be created for the reserved line quantity, but not for the unreserved quantity.
