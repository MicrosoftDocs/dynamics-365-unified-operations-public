---
# required metadata

title: License plate receiving via the Warehouse Management mobile app
description: This article explains how to set up the Warehouse Management mobile app to support using a license plate receiving process to receive physical inventory.
author: perlynne
ms.date: 04/29/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  WHSParameters, WHSRFMenuItem, WHSLicensePlate, WHSPackingStructure
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: perlynne
ms.search.validFrom: 2020-03-31
ms.dyn365.ops.version: 10.0.11
---

# License plate receiving via the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This article explains how to set up the Warehouse Management mobile app so that it supports using a license plate receiving process to receive physical inventory.

You can use this functionality to quickly record the receipt of inbound inventory that is related to an advance ship notice (ASN). The system automatically creates an ASN when warehouse management processes (WMS) are used to ship a transfer order. For the purchase order process, an ASN can be manually recorded, or it can be automatically imported by using an inbound ASN data entity process.

The ASN data is linked to loads and shipments via the *packing structures*, where pallets (parent license plates) can contain cases (nested license plates).

> [!NOTE]
> To reduce the number of inventory transactions when packing structures that have nested license plates are used, the system records the physical on-hand inventory on the parent license plate. To trigger the movement of the physical on-hand inventory from the parent license plate to the nested license plates, based on the packing structure data, the mobile device must provide a menu item that is based on the *Pack to nested license plates* work creation process.

## Warehousing mobile device app processing

When a worker scans an incoming license plate ID, the system initializes a license plate receiving process. Based on this information, the content of the license plate (data coming from the ASN) gets physically registered at the inbound dock location. The flows that follow will depend your business process needs.

## Work policies

As with (for example) the *Report as finished* mobile device menu item process, the license plate receiving process supports several workflows based on the defined setup.

### Work policies with work creation

When you register incoming items using a work policy that creates work, the system generates and saves put-away work records for each registration. If you use the *License plate receiving and put away* work process, then registration and put away are handled as a single operation using a single mobile device menu item. If you use the *License plate receiving* process, then the receiving and put-away processes are handled as two different warehouse operations, each with their own mobile device menu item.

### Work policies without work creation

You can use the license plate receiving process without creating work. If you define work policies that have a work order type of *Transfer receipt* and/or *Purchase orders*, and you use the process for *License plate receiving (and put away)*, the following two Warehousing mobile app processes won't create work. Instead, they will just register the inbound physical inventory on the license plate at the inbound receiving dock.

- *License plate receiving*
- *License plate receiving and put away*

> [!NOTE]
> - You must define at least one location for a work policy in the **Inventory locations** section. You can't specify the same location for multiple work policies.
> - The **Print label** option for Warehousing mobile device menu items won't print a license plate label without work creation.

To make this functionality available on your system, you must turn on the *License plate receiving enhancements* feature in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.32, this feature is turned on by default. As of Supply Chain Management version 10.0.36, this feature is mandatory and can't be turned off.

### Receive inventory on a location that doesn't track license plates

It's possible to use a warehouse location that is assigned to a location profile even when **Use license plate tracking** isn't turned on. Therefore, when you receive inventory, you can directly register the on-hand inventory on a location without work creation.

## Add mobile device menu items for each receiving location in a warehouse

The *License plate receiving enhancements* feature lets you receive at any location in a warehouse by adding location-specific license plate receiving (and put away) menu items to the Warehousing mobile app. Previously, the system supported receiving only at the default location that is defined for each warehouse. However, when this feature is turned on, mobile device menu items for license plate receiving (and put away) now provide the **Use default data** option, which lets you select a custom "to" location for each menu item. (This option was already available for some other types of menu items.)

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.32, it's turned on by default. As of Supply Chain Management version 10.0.36, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.36, then admins can turn this functionality on or off by searching for the *License plate receiving enhancements* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Show or skip the receiving summary page

You can use the *Control whether to display a receiving summary page on mobile devices* feature to take advantage of an additional detailed Warehouse Management mobile app flow as part of the license plate receiving process.

When this feature is turned on, mobile device menu items for license plate receiving or license plate receiving and put-away will provide a **Display receiving summary page** setting. This setting has the following options:

- **Display a detailed summary** – During license plate receiving, workers will see an extra page that shows the full ASN information.
- **Skip the summary** – Workers won't see the full ASN information. Warehouse workers also won't be able to set a disposition code or add exceptions during the receiving process.

To use this functionality, the *Control whether to display a receiving summary page on mobile devices* feature must be turned on for your system. As of Supply Chain Management version 10.0.21, this feature is turned on by default. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.25, then admins can turn this functionality on or off by searching for the *Control whether to display a receiving summary page on mobile devices* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Prevent transfer order–shipped license plates from being used at warehouses other than the destination warehouse

A license plate receiving process can't be used if an ASN contains a license plate ID that already exists and has physical on-hand data at a warehouse location other than the warehouse location where the license plate registration occurs.

For transfer order scenarios where the transit warehouse doesn't track license plates (and therefore also doesn't track physical on-hand inventory per license plate), you can use the *Prevent transfer order shipped license plates from being used on other warehouses than the destination warehouse* feature to prevent physical on-hand updates of license plates that are in transit. To make this functionality available, the *Prevent transfer order shipped license plates from being used on other warehouses than the destination warehouse* feature must be turned on for your system. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.25, then admins can turn this feature on or off by searching for it in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

To manage the functionality when this feature is available, follow these steps.

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **General** tab, on the **License plates** FastTab, set the **Transit warehouse license plate policy** field to one of the following values:

    - **Allow reuse of non-tracked license plate** – The system works the same way that it works when the *Prevent transfer order shipped license plates from being used on other warehouses than the destination warehouse* feature isn't available. This value is the default setting when you first activate the feature.
    - **Prevent reuse of non-tracked license plate** – Only on-hand updates that are related to a shipped license plate will be allowed at the destination warehouse until the transfer order has been received.

## More information

For more information about mobile device menu items, see [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md).

For more information about the *Report as finished* production scenario, see the [Warehouse work policies overview](warehouse-work-policies.md).

For more information about inbound load management, see [Warehouse handling of inbound loads for purchase orders](inbound-load-handling.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]