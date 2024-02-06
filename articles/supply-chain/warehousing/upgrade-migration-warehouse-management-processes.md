---
title: Upgrade warehouse management from Microsoft Dynamics AX 2012 to Supply Chain Management 
description: This article provides an overview of product and warehouse management migration options.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form:  InventLocationWHSProcessEnablement, WHSLocationProfile, InventTableStorageDimensionGroupChange, InventUpdateBlockedItem, WHSParameters, WHSReservationHierarchy, WHSUOMSeqGroupTable
ms.topic: how-to
ms.date: 01/30/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Upgrade warehouse management from Microsoft Dynamics AX 2012 to Supply Chain Management

[!include [banner](../includes/banner.md)]

This article provides an overview of the process of upgrading from Microsoft Dynamics AX 2012 R3, running the WMSII module, to Supply Chain Management .

Supply Chain Management no longer supports the legacy *WMSII* module from Microsoft Dynamics AX 2012. Instead, you can use the *Warehouse management* module. In the WMSII module, the Location and Pallet ID inventory dimensions could be selected for financial inventory, however, the Pallet ID inventory dimension cannot be used for financial inventory in Supply Chain Management .

During an upgrade, all products that are associated with a storage dimension group that uses the Pallet ID inventory dimension are identified, marked as blocked, and not processed for upgrade.

## Upgrading to Supply Chain Management when AX 2012 R3 WMSII is used

After the upgrade, you can use a set of options on the **Change storage dimension group for items** page to unblock products that were blocked during upgrade, and then process transactions for those products.

### Enabling items in Supply Chain Management

This change is required because in Supply Chain Management, item tracking is part of the warehouse management processes (WMS). For these processes, all warehouses and their locations must be associated with a location profile. If you want to use WMS, the following must be configured:

- Existing warehouses must be enabled to use WMS
- Existing released products must be associated with a storage dimension group that uses WMS

If the source storage dimension groups use the Pallet ID inventory dimension, the locations of existing on-hand inventory that used the Pallet ID inventory dimension must be associated with a location profile in which the **Use license plate tracking** parameter is selected. If the existing warehouses should not be enabled to use WMS, you can change the storage dimension groups of the existing on-hand inventory to groups that handle only the Site, Warehouse, and Location inventory dimensions.

> [!NOTE]
> You can change the storage dimension group for items even if open inventory transactions exist.

## Find products that were blocked because of pallet ID

To view the list of released products that were blocked during upgrade and can't be processed, go to **Inventory management** \> **Setup** \> **Inventory** \> **Items blocked for inventory updates**.

## Change storage dimension group for blocked products

To be used as part of a warehouse management process, an item must be associated with a storage dimension group in which the Location inventory dimension is active, and the **Use warehouse management processes** parameter is selected. When this setting is selected, the Site, Warehouse, Inventory status, Location, and License plate inventory dimensions become active.

To unblock products that were blocked during upgrade, you must select a new storage dimension group for the products. Note that you can change the storage dimension group even if open inventory transactions exist. To use items that were blocked during upgrade, you have two options:

- Change the storage dimension group for the item to a storage dimension group that uses only the Site, Warehouse, and Location inventory dimensions. As a result of this change, the Pallet ID inventory dimension is no longer used.
- Change the storage dimension group for the item to a storage dimension group that uses WMS. As a result of this change, the License plate inventory dimension is now used.

## Enable warehouses to use WMS

Follow these steps to enable a warehouse to use WMS:

1. Create at least one new location profile.
1. Go to **Warehouse management** \> **Setup** \> **Enable warehouse management processes** \> **Enable warehouse setup**.
1. On the **Enable warehouse setup** page, add the warehouses that should be enabled. You can complete this step either directly on the page or by using the Microsoft Office integration.
1. Assign a location profile to all the locations. You can easily complete this step by using the Microsoft Office integration directly from the page. You can either export and import the data, or use the data entity processing in [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities.md).
1. Validate the changes. As part of the validation process, various validations of data integrity occur. As part of a larger upgrade process, issues that occur might have to be adjusted on the source implementation. In this case, an additional data upgrade will be required.
1. Process the changes.

## Change the storage dimension group for items to use WMS

This section describes how to change product storage dimension groups for items as part of the process of upgrading warehouse management from Microsoft Dynamics AX 2012 to Supply Chain Management.

### Purpose of changing storage dimension groups for items

Changing storage dimension groups for items lets you migrate existing items with open inventory transactions so that they can use the new storage dimension, which is a necessary for using WMS in Supply Chain Management.

In a typical migration scenario, you'll have existing items with the location dimension enabled. The migration process enables those items to fulfil the WMS item requirements and ensures that all the related data matches the new settings, thereby enabling business processes to proceed after the migration.

To use WMS, your items must meet the following requirements:

- The [storage dimension group](/training/modules/configure-inventory-management-dyn365-supply-chain-mgmt/3-2-storage-dim) for each item must have **Use warehouse management process** set to *Yes*. The storage dimension represents how you store or retrieve items in your inventory.
- An [inventory reservation hierarchy](flexible-warehouse-level-dimension-reservation.md#inventory-reservation-hierarchy) must be assigned.
- A **unit sequence group** must be assigned. The unit sequence group defines the sequence of units that can be used in warehouse operations.

### Prerequisite settings

You must make the following settings before you start migrating items:

1. Create a new **Inventory status** value and assign it as the **Default inventory status ID** value in the **Warehouse management parameters** settings.
1. Create a new storage dimension group where the **Use warehouse management processes** parameter is set to *Yes*.
1. On the **Reservation hierarchy** page, define a new reservation hierarchy to accommodate each item's storage and tracking dimension groups.
1. Create one or more **unit sequence groups** that include the units used for each item's inventory units.

### Change storage dimension groups for items

Dynamics 365 Supply Chain Management provides a migration tool that helps you change the storage dimension group for items. Follow these steps to migrate an item.

1. Go to either of the following locations:

    - **Inventory Management** \> **Setup** \> **Inventory** \> **Change storage dimension group for items**
    - **Warehouse management** \> **Setup** \> **Enable warehouse management processes** \> **Change storage dimension group for items**

1. On the Action Pane, select **New** to add a row to the grid and make the following settings for it:
    - **Item number** – Select the item number to migrate.
    - **Storage dimension group** – Select the new storage dimension group that you plan to migrate the item to.
    - **Reservation hierarchy** – Select the reservation hierarchy that applies to the migrated item.
    - **Unit sequence groups** – Select the unit sequence group that applies to the migrated item.

    Continue working until you have added all of the rows you need. You can complete this step directly on the page (as described here), or by importing many rows at once using either Microsoft Office integration or the data entity process described in [data management](../../fin-ops-core/dev-itpro/data-entities/data-entities.md).

1. On the Action Pane, select **Validate changes**. The system now validates all of the rows on the page to ensure data integrity will be maintained. As part of a large migration process, you may need to fix issues by adjusting data on the source implementation, so several additional rounds of data migration may be required. Among other things, the validation checks for the following conditions:

    - A default inventory status must be defined.
    - Inventory on-hand with pallets must not exist on non-license-plate-tracked locations.
    - Inventory on-hand without pallets must not exist on license-plate-tracked locations.
    - All combinations of storage dimension groups and reservation hierarchies must be valid.
    - Items migrating to use WMS must not be enabled to use catch weight.

1. On the Action Pane, select **Process changes**. Updating all the inventory dimensions can take a while. You can monitor the progress by checking the batch jobs tasks. The process uses both parallel processing and the batch framework, and the difference is handled by different batch tasks.

    > [!NOTE]
    > If you upgrade from a version that supports pallets, the upgrade process will identify the items that have the pallet dimension active and create a record on the **Items blocked for inventory updates** page for each of them. This is done to block the items from all inventory processes because the item is configured using unsupported settings. Items that are blocked must be migrated.

### Unsupported scenarios

The following scenarios aren't supported:

- **Catch weight enabled items**: Catch weight enabled items have the pallet dimension active, so they must be downgraded to a dimensions group where only the location is active.
- **Reserve ordered transactions**: Because of the way reservations work for WMS-enabled items, there are certain constraints on the state of the inventory transactions. If there are reserved ordered transactions with a *hole* in the dimensions, then then the item can't be converted. A hole could exist for an item that has the batch dimension active and has the batch placed below the location in the reservation hierarchy. If a reservation exists on site, warehouse, or batch, then the location is missing, which is what we refer to as a *hole*. This isn't supported. The mitigation is to either assign the missing dimensions or clear the dimensions, so the hole is removed.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]