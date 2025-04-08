---
title: Upgrade warehouse management from Microsoft Dynamics AX 2012 to Supply Chain Management 
description: Access an overview of product and warehouse management migration options with an outline on upgrading to Supply Chain Management.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 01/30/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:  InventLocationWHSProcessEnablement, WHSLocationProfile, InventTableStorageDimensionGroupChange, InventUpdateBlockedItem, WHSParameters, WHSReservationHierarchy, WHSUOMSeqGroupTable
---

# Upgrade warehouse management from Microsoft Dynamics AX 2012 to Supply Chain Management

[!include [banner](../includes/banner.md)]

This article provides an overview of the process of upgrading from Microsoft Dynamics AX 2012 R3, running the *WMSII* module, to Dynamics 365 Supply Chain Management.

Supply Chain Management no longer supports the legacy *WMSII* module from Dynamics AX 2012. Instead, you can use the *Warehouse management* module. In the *WMSII* module, the Location and Pallet ID inventory dimensions can be selected for financial inventory. However, the Pallet ID inventory dimension can't be used for financial inventory in Supply Chain Management.

During an upgrade, all products that are associated with a storage dimension group that uses the Pallet ID inventory dimension are identified, marked as blocked, and not processed for upgrade.

## Upgrading to Supply Chain Management when AX 2012 R3 WMSII is used

After the upgrade, you can use a set of options on the **Change storage dimension group for items** page to unblock products that were blocked during upgrade, and then process transactions for those products.

### Enabling items in Supply Chain Management

This change is required because in Supply Chain Management, item tracking is part of the warehouse management processes (WMS). For these processes, all warehouses and their locations must be associated with a location profile. If you want to use WMS, the following configuration must be done:

- Existing warehouses must be enabled to use WMS.
- Existing released products must be associated with a storage dimension group that uses WMS.

If the source storage dimension groups use the Pallet ID inventory dimension, the locations of existing on-hand inventory that used the Pallet ID inventory dimension must be associated with a location profile where the **Use license plate tracking** parameter is selected. If the existing warehouses should not be enabled to use WMS, you can change the storage dimension groups of the existing on-hand inventory to groups that handle only the Site, Warehouse, and Location inventory dimensions.

> [!NOTE]
> You can change the storage dimension group for items even if open inventory transactions exist.

## Find products that were blocked because of the pallet ID

To view the list of released products that were blocked during upgrade and can't be processed, go to **Inventory management** \> **Setup** \> **Inventory** \> **Items blocked for inventory updates**.

## Change the storage dimension group for blocked products

To be used as part of a warehouse management process, an item must be associated with a storage dimension group in which the Location inventory dimension is active, and the **Use warehouse management processes** parameter is selected. When this setting is selected, the Site, Warehouse, Inventory status, Location, and License plate inventory dimensions become active.

To unblock products that were blocked during upgrade, you must select a new storage dimension group for the products. Note that you can change the storage dimension group even if open inventory transactions exist. To use items that were blocked during upgrade, you have two options:

- Change the storage dimension group for the item to a storage dimension group that uses only the Site, Warehouse, and Location inventory dimensions. As a result of this change, the Pallet ID inventory dimension is no longer used.
- Change the storage dimension group for the item to a storage dimension group that uses WMS. As a result of this change, the License plate inventory dimension is used.

## Enable warehouses to use WMS

Follow these steps to enable a warehouse to use WMS.

1. Create at least one new location profile.
1. Go to **Warehouse management** \> **Setup** \> **Enable warehouse management processes** \> **Enable warehouse setup**.
1. On the **Enable warehouse setup** page, add the warehouses that should be enabled to use WMS. You can complete this step either directly on the page or by using the Microsoft Office integration.
1. Assign a location profile to all the locations. You can easily complete this step directly from the page by using the Microsoft Office integration. You can either export and import the data, or use the data entity processing in [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities.md).
1. Validate the changes. As part of the validation process, various validations of data integrity occur. As part of a larger upgrade process, issues that occur might have to be adjusted on the source implementation. In this case, an additional data upgrade will be required.
1. Process the changes.

## Change the storage dimension group for items to use WMS

This section describes how to change product storage dimension groups for items as part of the process of upgrading warehouse management from AX 2012 to Supply Chain Management.

### Purpose of changing storage dimension groups for items

By changing storage dimension groups for items, you can migrate existing items that have open inventory transactions so that they use the new storage dimension that's required to use WMS in Supply Chain Management.

In a typical migration scenario, you have existing items where the location dimension is enabled. The migration process enables those items to fulfill the WMS item requirements and ensures that all the related data matches the new settings. In this way, business processes can proceed after the migration.

To use WMS, your items must meet the following requirements:

- The [storage dimension group](/training/modules/configure-inventory-management-dyn365-supply-chain-mgmt/3-2-storage-dim) for each item must have the **Use warehouse management processes** parameter set to *Yes*. The storage dimension represents how you store or retrieve items in your inventory.
- An [inventory reservation hierarchy](flexible-warehouse-level-dimension-reservation.md#inventory-reservation-hierarchy) must be assigned.
- A unit sequence group must be assigned. The unit sequence group defines the sequence of units that can be used in warehouse operations.

### Prerequisite settings

You must configure the following settings before you start to migrate items:

1. Create a new **Inventory status** value, and assign it as the **Default inventory status ID** value in the **Warehouse management parameters** settings.
1. Create a new storage dimension group where the **Use warehouse management processes** parameter is set to *Yes*.
1. On the **Reservation hierarchy** page, define a new reservation hierarchy to accommodate each item's storage and tracking dimension groups.
1. Create one or more unit sequence groups that include the units that are used for each item's inventory units.

### Change storage dimension groups for items

Supply Chain Management provides a migration tool to help you change the storage dimension group for items. Follow these steps to migrate an item.

1. Go to one of the following locations:

    - **Inventory Management** \> **Setup** \> **Inventory** \> **Change storage dimension group for items**
    - **Warehouse management** \> **Setup** \> **Enable warehouse management processes** \> **Change storage dimension group for items**

1. On the Action Pane, select **New** to add a row to the grid. Set the following fields for the new row:

    - **Item number** – Select the item number to migrate.
    - **Storage dimension group** – Select the storage dimension group that you plan to migrate the item to.
    - **Reservation hierarchy** – Select the reservation hierarchy that applies to the migrated item.
    - **Unit sequence groups** – Select the unit sequence group that applies to the migrated item.

1. Repeat step 2 until you've added all the rows that you need.

    > [!TIP]
    > Instead of adding one row one at a time, as described here, you can import many rows at the same time by using either Microsoft Office integration or the data entity process that's described in [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities.md).

1. On the Action Pane, select **Validate changes**. The system validates all the rows on the page to ensure that data integrity will be maintained. As part of a large migration process, you might have to adjust data on the source implementation to fix issues. Therefore, several additional rounds of data migration might be required. The validation checks for the following conditions, among others:

    - A default inventory status must be defined.
    - On-hand inventory with pallets must exist only on license-plate-tracked locations.
    - On-hand inventory without pallets must not exist on license-plate-tracked locations.
    - All combinations of storage dimension groups and reservation hierarchies must be valid.
    - Items that are migrated to use WMS must not be enabled to use catch weight.

1. On the Action Pane, select **Process changes**. The update of all the inventory dimensions can take a while. You can monitor the progress by checking the batch job tasks. The process uses both parallel processing and the batch framework, and the difference is handled by different batch tasks.

    > [!NOTE]
    > If you upgrade from a version that supports pallets, the upgrade process identifies any items where the pallet dimension is active. Because these items use unsupported settings, the upgrade process creates a record for each of them on the **Items blocked for inventory updates** page. In this way, the items are blocked from all inventory processes. Blocked items must be migrated.

### Unsupported scenarios

The following scenarios aren't supported:

- **Catch-weight-enabled items:** Because the pallet dimension is active for catch-weight–enabled items, those items must be downgraded to a dimensions group where only the location dimension is active.
- **Reserve ordered transactions:** Because of the way that reservations work for WMS-enabled items, there are specific constraints on the state of the inventory transactions. If any reserved ordered transactions have a "hole" in the dimensions, the item can't be converted. A hole can occur for items where the batch dimension is active and is below the location dimension in the reservation hierarchy. If a reservation exists on the site, warehouse, or batch, the location is missing. We refer to this situation as a hole. Holes aren't supported. To fix the issue, remove the hole by either assigning the missing dimensions or clearing the dimensions.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
