---
# required metadata


title: Upgrade warehouse management from Microsoft Dynamics AX 2012 to Supply Chain Management 

description: This topic provides an overview of product and warehouse management migration options.
author: perlynne
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  InventLocationWHSProcessEnablement, WHSLocationProfile, InventTableStorageDimensionGroupChange, InventUpdateBlockedItem, WHSParameters, WHSReservationHierarchy, WHSUOMSeqGroupTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 1714054
ms.assetid: 79a1a3b9-3a36-4162-8839-ec39b5e26602
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Upgrade warehouse management from Microsoft Dynamics AX 2012 to Supply Chain Management 


[!include [banner](../includes/banner.md)]

This topic provides an overview of the process of upgrading from Microsoft Dynamics AX 2012 R3, running the WMSII module, to Supply Chain Management .

Supply Chain Management no longer supports the legacy **WMSII** module from Microsoft Dynamics AX 2012. Instead, you can use the **Warehouse management** module. In the WMSII module, the Location and Pallet ID inventory dimensions could be selected for financial inventory, however, the Pallet ID inventory dimension cannot be used for financial inventory in Supply Chain Management .

During an upgrade, all products that are associated with a storage dimension group that uses the Pallet ID inventory dimension are identified, marked as blocked, and not processed for upgrade.

## Upgrading to Supply Chain Management when AX 2012 R3 WMSII is used
After the upgrade, you can use a set of options in the **Change storage dimension group for items** form to unblock products that were blocked during upgrade, and then process transactions for those products.

### Enabling items in Supply Chain Management 
This change is required because in Supply Chain Management, item tracking is part of the warehouse management processes. For these processes, all warehouses and their locations must be associated with a location profile. If you want to use warehouse management processes, the following must be configured:
-   Existing warehouses must be enabled to use warehouse management processes 
-   Existing released products must be associated with a storage dimension group that uses warehouse management processes 

If the source storage dimension groups use the Pallet ID inventory dimension, the locations of existing on-hand inventory that used the Pallet ID inventory dimension must be associated with a location profile in which the **Use license plate tracking** parameter is selected. If the existing warehouses should not be enabled to use warehouse management processes, you can change the storage dimension groups of the existing on-hand inventory to groups that handle only the Site, Warehouse, and Location inventory dimensions. 

> [!NOTE] 
>  You can change the storage dimension group for items even if open inventory transactions exist.

## Find products that were blocked because of Pallet ID
To view the list of released products that were blocked during upgrade and can't be processed, click **Inventory management** &gt; **Setup** &gt; **Inventory** &gt; **Items blocked for inventory updates**.

## Change storage dimension group for blocked products 
 
To be used as part of a warehouse management process, an item must be associated with a storage dimension group in which the Location inventory dimension is active, and the **Use warehouse management processes** parameter is selected. When this setting is selected, the Site, Warehouse, Inventory status, Location, and License plate inventory dimensions become active.

To unblock products that were blocked during upgrade, you must select a new storage dimension group for the products. Note that you can change the storage dimension group even if open inventory transactions exist. To use items that were blocked during upgrade, you have two options:

-   Change the storage dimension group for the item to a storage dimension group that uses only the Site, Warehouse, and Location inventory dimensions. As a result of this change, the Pallet ID inventory dimension is no longer used.
-   Change the storage dimension group for the item to a storage dimension group that uses the warehouse management processes. As a result of this change, the License plate inventory dimension is now used.

## Configure warehouse management processes
Before you can use released products in the **Warehouse management** module, the products must use a storage dimension group where the **Use warehouse management processes** parameter is selected.

### Enable warehouses to use warehouse management processes

1.  Create at least one new location profile.
2.  Click **Warehouse management** &gt; **Setup** &gt; **Enable warehouse management processes** &gt; **Enable warehouse setup**.
3.  On the **Enable warehouse setup** page, add the warehouses that should be enabled. You can complete this step either directly on the page or by using the Microsoft Office integration.
4.  Assign a location profile to all the locations. You can easily complete this step by using the Microsoft Office integration directly from the page. You can either export and import the data, or use the data entity processing in [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities.md).
5.  Validate the changes. As part of the validation process, various validations of data integrity occur. As part of a larger upgrade process, issues that occur might have to be adjusted on the source implementation. In this case, an additional data upgrade will be required.
6.  Process the changes.

### Change the storage dimension group for items, so that it uses warehouse management processes

1.  Create a new **Inventory status** value, and assign it as the **Default inventory status ID** value in the **Warehouse management parameters** settings.
2.  Create a new storage dimension group where the **Use warehouse management processes** parameter is selected.
3.  On the **Reservation hierarchy** page, define a new reservation hierarchy according to the item’s storage and tracking dimension groups.
4.  Create one or more unit sequence groups that include at least the same units that are used for the items' inventory units.
5.  Click **Warehouse management** &gt; **Setup** &gt; **Enable warehouse management processes** &gt; **Change storage dimension group for items**.
6.  On the **Change storage dimension group for items** page, add the item numbers, storage dimension groups, and unit sequence groups. You can complete this step directly on the page, by using the Microsoft Office integration, or by using the data entity process in [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities.md).
7.  Validate the changes. As part of the validation process, various validations of data integrity occur. As part of a larger upgrade process, issues that occur might have to be adjusted on the source implementation. In this case, additional data upgrade will be required.
8.  Process the changes. An update of all the inventory dimensions can take a while. You can monitor the progress by using the batch jobs tasks.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]