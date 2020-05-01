---
# required metadata

title: License plate receiving via the Warehousing mobile app
description: This topic explains how to set up the Warehousing mobile app to support using a license plate receiving process to receive physical inventory.
author: perlynne
manager: tfehr
ms.date: 04/29/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: perlynne
ms.search.validFrom: 2020-03-31
ms.dyn365.ops.version: Release 10.0.11
---

# License plate receiving via the Warehousing mobile app

This topic explains how to set up the Warehousing mobile app so that it supports using a license plate receiving process to receive physical inventory.

You can use this functionality to quickly record the receipt of inbound inventory that is related to an advance ship notice (ASN). The system automatically creates an ASN when warehouse management processes are used to ship a transfer order. For the purchase order process, an ASN can be manually recorded, or it can be automatically imported by using an inbound ASN data entity process.

The ASN data is linked to loads and shipments via the *packing structures*, where pallets (parent license plates) can contain cases (nested license plates).

> [!NOTE]
> To reduce the number of inventory transactions when packing structures that have nested license plates are used, the system records the physical on-hand inventory on the parent license plate. To trigger the movement of the physical on-hand inventory from the parent license plate to the nested license plates, based on the packing structure data, the mobile device must provide a menu item that is based on the *Pack to nested license plates* work creation process.

## Warehousing mobile device app processing

When a worker scans an incoming license plate ID, the system initializes a license plate receiving process. Based on this information, the content of the license plate (data coming from the ASN) gets physically registered at the inbound dock location. The flows that follow will depend your business process needs.

## Work policies

As with (for example) the *Report as finished* mobile device menu item process, the license plate receiving process supports several workflows based on the defined setup.

### Work policies with work creation

Registration of physical on-hand where either the same warehouse worker immediately process a put-away work process following the inbound receiving (*License plate receiving and put away*) or where the registration and put away process gets handled as two different warehouse operations (License plate receiving) following the processing of the put-away work by using the existing work process via another mobile device menu item.

### Work policies without work creation

You can use the license plate receiving process without creating work. By defining **Work policies** with a **Work order type** of *Transfer receipt* and/or *Purchase orders*, and using the **Process** for *License plate receiving (and put away)*, the following two Warehousing app processes won't create work, but only register the inbound physical inventory on the license plate at the inbound receiving dock:

- *License plate receiving*
- *License plate receiving and put away*

> [!NOTE]
> - You must define at least one location for a work policy in the **Inventory locations** section. You can't specify the same location for multiple work policies.
> - The warehousing mobile device menu item option **Print label** won't print a license plate label without work creation.

To make this functionality available on your system, the *License plate receiving enhancements* feature must be enabled in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Receive inventory on a location which does not track license plates

It is possible to use a warehouse location that is assigned to a **Location profile** without **Use license plate tracking** enabled and thereby directly register the inventory on-hand on a location when receiving inventory without work creation.

## Add mobile device menu items for each receiving location within a warehouse

The *License plate receiving enhancements* feature lets you receive at any location within a warehouse by adding location-specific license plate receiving (and put away) menu items to the warehousing mobile app. Previously, the system only supported receiving at the default location defined for each warehouse, but with this feature, mobile device menu items for license plate receiving (and put away) now provide the **Use default data** option (already available for some other types of menu items), which lets you choose a custom **To location** for each menu item.

To make this functionality available on your system, the *License plate receiving enhancements* feature must be enabled in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Show or skip the receiving summary page

You can use the *Control whether to display a receiving summary page on mobile devices* feature to take advantage of an additional detailed Warehouse app flow as part of the license plate receiving process.

When this feature is turned on, mobile device menu items for license plate receiving or license plate receiving and put-away will provide a **Display receiving summary page** setting. This setting has the following options:

- **Display a detailed summary** – During license plate receiving, workers will see an extra page that shows the full ASN information.
- **Skip the summary** – Workers won't see the full ASN information. Warehouse workers also won't be able to set a disposition code or add exceptions during the receiving process.

To make this functionality available on your system, the *Control whether to display a receiving summary page on mobile devices* feature must be enabled in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Prevent transfer order shipped license plates from being used at warehouses other than the destination warehouse

A license plate receiving process can't be used if an ASN contains a license plate ID that already exists and has physical on-hand data at a warehouse location other than the warehouse location where the license plate registration occurs.

For transfer order scenarios where the transit warehouse doesn't track license plates (and therefore also doesn't track physical on-hand inventory per license plate), you can use the *Prevent transfer order shipped license plates from being used on other warehouses than the destination warehouse* feature to prevent physical on-hand updates of license plates that are in transit.

To make this functionality available on your system, the *Prevent transfer order shipped license plates from being used on other warehouses than the destination warehouse* feature must be enabled in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

To manage the functionality when this feature is available, follow these steps.

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **General** tab, on the **License plates** FastTab, set the **Transit warehouse license plate policy** field to one of the following values:

    - **Allow reuse of non-tracked license plate** – The system works the same way that it works when the *Prevent transfer order shipped license plates from being used on other warehouses than the destination warehouse* feature isn't available. This value is the default setting when you first activate the feature.
    - **Prevent reuse of non-tracked license plate** – Only on-hand updates that are related to a shipped license plate will be allowed at the destination warehouse until the transfer order has been received.

## More information

For more information about *Mobile device menu items*, see [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md).

For more information about the *Report as finished* production scenario, see the [Warehouse work policies overview](warehouse-work-policies.md).

For more information about inbound load management, see [Warehouse handling of inbound loads for purchase orders](inbound-load-handling.md).
