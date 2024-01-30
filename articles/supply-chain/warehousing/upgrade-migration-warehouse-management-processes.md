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

After the upgrade, you can use a set of options in the **Change storage dimension group for items** form to unblock products that were blocked during upgrade, and then process transactions for those products.

### Enabling items in Supply Chain Management

This change is required because in Supply Chain Management, item tracking is part of the warehouse management processes (WMS). For these processes, all warehouses and their locations must be associated with a location profile. If you want to use WMS, the following must be configured:

- Existing warehouses must be enabled to use WMS
- Existing released products must be associated with a storage dimension group that uses WMS

If the source storage dimension groups use the Pallet ID inventory dimension, the locations of existing on-hand inventory that used the Pallet ID inventory dimension must be associated with a location profile in which the **Use license plate tracking** parameter is selected. If the existing warehouses should not be enabled to use WMS, you can change the storage dimension groups of the existing on-hand inventory to groups that handle only the Site, Warehouse, and Location inventory dimensions.

> [!NOTE]
> You can change the storage dimension group for items even if open inventory transactions exist.

## Find products that were blocked because of Pallet ID

To view the list of released products that were blocked during upgrade and can't be processed, click **Inventory management** &gt; **Setup** &gt; **Inventory** &gt; **Items blocked for inventory updates**.

## Change storage dimension group for blocked products

To be used as part of a warehouse management process, an item must be associated with a storage dimension group in which the Location inventory dimension is active, and the **Use warehouse management processes** parameter is selected. When this setting is selected, the Site, Warehouse, Inventory status, Location, and License plate inventory dimensions become active.

To unblock products that were blocked during upgrade, you must select a new storage dimension group for the products. Note that you can change the storage dimension group even if open inventory transactions exist. To use items that were blocked during upgrade, you have two options:

- Change the storage dimension group for the item to a storage dimension group that uses only the Site, Warehouse, and Location inventory dimensions. As a result of this change, the Pallet ID inventory dimension is no longer used.
- Change the storage dimension group for the item to a storage dimension group that uses WMS. As a result of this change, the License plate inventory dimension is now used.

## Configure WMS

Before you can use released products in the **Warehouse management** module, the products must use a storage dimension group where the **Use warehouse management processes** parameter is selected.

### Enable warehouses to use WMS

1. Create at least one new location profile.
1. Click **Warehouse management** &gt; **Setup** &gt; **Enable warehouse management processes** &gt; **Enable warehouse setup**.
1. On the **Enable warehouse setup** page, add the warehouses that should be enabled. You can complete this step either directly on the page or by using the Microsoft Office integration.
1. Assign a location profile to all the locations. You can easily complete this step by using the Microsoft Office integration directly from the page. You can either export and import the data, or use the data entity processing in [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities.md).
1. Validate the changes. As part of the validation process, various validations of data integrity occur. As part of a larger upgrade process, issues that occur might have to be adjusted on the source implementation. In this case, an additional data upgrade will be required.
1. Process the changes.

### Change the storage dimension group for items, so that it uses WMS

1. Create a new **Inventory status** value, and assign it as the **Default inventory status ID** value in the **Warehouse management parameters** settings.
1. Create a new storage dimension group where the **Use warehouse management processes** parameter is selected.
1. On the **Reservation hierarchy** page, define a new reservation hierarchy according to the item’s storage and tracking dimension groups.
1. Create one or more unit sequence groups that include at least the same units that are used for the items' inventory units.
1. Click **Warehouse management** &gt; **Setup** &gt; **Enable warehouse management processes** &gt; **Change storage dimension group for items**.
1. On the **Change storage dimension group for items** page, add the item numbers, storage dimension groups, and unit sequence groups. You can complete this step directly on the page, by using the Microsoft Office integration, or by using the data entity process in [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities.md).
1. Validate the changes. As part of the validation process, various validations of data integrity occur. As part of a larger upgrade process, issues that occur might have to be adjusted on the source implementation. In this case, additional data upgrade will be required.
1. Process the changes. An update of all the inventory dimensions can take a while. You can monitor the progress by using the batch jobs tasks.





## Change storage dimension group for items to use warehouse management process

This section provides an overview of process the change of product storage dimension group for items as part of the process of [upgrading warehouse management from Microsoft Dynamics AX 2012 to Supply Chain Management](upgrade-migration-warehouse-management-processes.md).

### Purpose to change storage dimension group for items

With the change storage dimension groups for items to use warehouse management process, you can migrate existing items with open inventory transactions so that they can use the new storage dimension, which is a necessary upgrade process to the Warehouse management feature in Dynamics 365 Supply Chain Management.

The typical migration scenario is that you have existing items with the location dimension enabled, and the migration process enables those items to fit the warehouse management item requirements and make sure all the related data matches the item's new settings enabling business processes to proceed after the migration.

The requirements for items to use warehouse management process include:

1. The [storage dimension group](/training/modules/configure-inventory-management-dyn365-supply-chain-mgmt/3-2-storage-dim) for the item must have 'Use warehouse management process' = 'Yes'. The storage dimension represents how you store or retrieve items in your inventory.
1. An [inventory reservation hierarchy](flexible-warehouse-level-dimension-reservation.md#inventory-reservation-hierarchy) must be assigned.

1. A **unit sequence group** must be assigned. The unit sequence group defines the sequence of units that can be used in warehouse operations.

### Prerequisite settings

1. Create a new **Inventory status** value and assign it as the **Default inventory status ID** value in the **Warehouse management parameters** settings.
1. Create a new storage dimension group where the **Use warehouse management processes** parameter is selected.
1. On the **Reservation hierarchy** page, define a new reservation hierarchy according to the item's storage and tracking dimension groups.
1. Create one or more **unit sequence groups** that include at least the same units that are used for the items' inventory units.

### Change storage dimension groups for items

Dynamics 365 Supply Chain Management provides you with a migration cockpit to change the storage dimension group for items. You can access the cockpit from:

- **Inventory Management &gt; Setup &gt; Inventory &gt; Change storage dimension group for items**. Or,
- **Warehouse management** &gt; **Setup** &gt; **Enable warehouse management processes** &gt; **Change storage dimension group for items**.

1. Click **+New** to create a new record.
1. Enter the **item number**, **storage dimension** group that you plan to change to, **reservation hierarchy** and **unit sequence groups**. You can complete this step directly on the page, by using the Microsoft Office integration, or by using the data entity process in [data management](../../fin-ops-core/dev-itpro/data-entities/data-entities.md)
1. **Validate changes**. As part of the validation process, various validations of data integrity occur. As part of a large upgrade process, issues that occur might have to be adjusted on the source implementation. In this case, additional data upgrade will be required.

    The validation checks several conditions, such as:

    - A default inventory status must be defined.
    - Inventory on-hand on pallets must not exist on non-licenses- plate-tracked locations.
    - Inventory on-hand without pallets must not exist on license-plate-tracked locations.
    - That the combination of the selected storage dimension group and reservation hierarchy is valid.
    - If migrating to use warehouse management processes, the item cannot be enabled with catch weight.

1. **Process changes**. An update of all the inventory dimensions can take a while, you can monitor the progress by using the batch jobs tasks. Migration supports the parallel processing for parts of the process. The batch framework is used, and the difference will be handled by different batch tasks.

    > [!NOTE]
    > If you upgrade from a version that supported pallets, the upgrade will identify the items that had the pallet dimension active and create a record in the **Items blocked for inventory updates** form. This is done to block the items from all inventory processes because the item is configured using unsupported settings. Items that are blocked must be migrated.

### Unsupported scenarios

- Catch weight enabled items: Catch weight enabled items have the pallet dimension active, they will need to be downgraded to a dimensions group where only the location is active.
- Reserve Ordered transactions: Because of the way reservations work for warehouse management enabled items there are certain constraints on the state of the inventory transactions. If there are Reserved ordered transactions with a "hole" in the dimensions, the item cannot be converted. A "hole" could exist for an item that has the batch dimension active and has the batch placed below the location in the reservation hierarchy. If a reservation exists on site, warehouse, batch, then the location is missing, which is what we refer to as a "hole". This is not supported. The mitigation is to either assign the missing dimensions or clear the dimensions, so the "hole" is removed.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]