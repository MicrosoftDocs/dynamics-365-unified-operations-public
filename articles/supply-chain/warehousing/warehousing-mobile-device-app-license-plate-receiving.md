---
# required metadata

title: Warehousing mobile-device app license plate receiving
description: Learn how to set up the Warehousing mobile-device app to support the receiving of physical inventory using a license plate receiving process.
author: perlynne
manager: tfehr
ms.date: 03/31/2020
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

# License plate receiving with the Warehousing mobile app

This topic describes how to set up the Warehousing mobile-device app to support the receiving of physical inventory using a license plate receiving process.

Use this functionality to quickly record the receipt of inbound inventory related to an advance ship notice (ASN). The system automatically creates an ASN when shipping a transfer order using warehouse management processes. For the purchase order process, an ASN can either be manually recorded or automatically imported using an inbound ASN data entity process.

The ASN data is linked to loads and shipments via the **Packing structures** where pallets (parent license plates) can contain cases (nested license plates).

> [!NOTE]
> To reduce the number of inventory transactions when using packing structures for cases the nested license plate structures will be recorded, but the physical on-hand representation will get recorded with physical on-hand on the parent license plate. A following process to move the physical inventory from the parent license plate to the individual nested license plates must follow via the process of using the **Pack to nested license plates** work creation process mobile device option.
<!-- KFM: I don't understand this note. Let's discuss and revise it. -->

## Warehousing mobile device app processing

When a worker scans an incoming license plate ID, the system initializes a license plate receiving process. Based on this information, the content of the license plate (data coming from the ASN) gets physically registered at the inbound dock location. The flows that follow will depend your business process needs.

## Work policies

As with (for example) the *Report as finished* mobile device menu item process, the license plate receiving process supports several workflows based on the defined setup.

### Work policies with work creation

Registration of physical on-hand where either the same warehouse worker immediately process a put-away work process following the inbound receiving (License plate receiving and put away) or where the registration and put away process gets handled as two different warehouse operations (License plate receiving) following the processing of the put-away work by using the existing work process via another mobile device menu item.
<!-- KFM: This sentence is very long and also incomplete. Let's discuss and revise it. -->

### Work policies without work creation

You can use the license plate receiving process without creating work by using the  *Warehouse app license plate receiving processing without work creation* feature. <!-- KFM: Where do we find this feature? I couldn't see it in feature management. -->

By defining **Work policies** with a **Work order type** of *Transfer receipt* and/or *Purchase orders*, and using the **Process** for **License plate receiving (and put away)**, the two Warehousing app process:

- License plate receiving
- License plate receiving and put away

will not create work, but only register the inbound physical inventory on the license plate at the inbound receiving dock.

<!-- KFM: What is the difference between "the process" and "Warehousing app process" in the above? -->

For more information about the *Report as finished* production scenario, see the [Warehouse work policies overview](warehouse-work-policies.md).

## Display or skip the receiving summary page

Use the *Control whether to display a receiving summary page on mobile devices* feature to leverage an additional detailed Warehouse app flow as part of the license plate receiving process.

To use this feature, it must first be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Control whether to display a receiving summary page on mobile devices*

When this feature is enabled, mobile device menu items that use a **Work creation process** of *License plate receiving* or *License plate receiving and put away* will provide a **Display receiving summary page** setting, which provides the following options:

- **Display a detailed summary** - Workers will see an extra page during license plate receiving that includes the full advance shipment notice (ASN) information.
- **Skip the summary** - Workers won't see the full ASN information. With this setting, warehouse workers also won't be able to set a disposition code or add exceptions during the receiving process.

## Prevent transfer order shipped license plates from being used at warehouses other than the destination warehouse

A license plate receiving process isn't allowed when an ASN contains a license plate ID that already exists with physical on-hand data at a warehouse location other than the one where the license plate registration is happening.

For transfer order scenarios where the transit warehouse doesn't track license plates (and thereby physical on-hand tracking per license plate <!-- KFM: this part in parenthesis is confusing, can we remove this? -->), you can prevent physical on-hand updates of license plates in transit by using the *Prevent transfer order shipped license plates from being used on other warehouses than the destination warehouse* feature.

To use this feature, it must first be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Prevent transfer order shipped license plates from being used on other warehouses than the destination warehouse*

To manage this option when the feature is available:

1. Go to **Warehouse management > Setup > Warehouse management parameters**.
1. Open the **General** tab.
1. On the **License plates** FastTab, set **Transit warehouse license plate policy** to one of the following:
    - **Allow reuse of non-tracked license plate** - <!-- KFM: Describe this setting here. Also, is this the default and also the same behavior as when the feature isn't enabled in FM? -->
    - **Prevent reuse of non-tracked license plate** - Only on-hand updates related to a shipped license plate will be allowed at the destination warehouse until the transfer order has been received.

## More information

<!-- To read more about inbound loads, see [\*\*\*NEW\_INBOUND\_LOAD\_PAGE\*\*\*. -- link to new page for Inbound load (Olga's doc.)] -->

For more information about mobile device menu items, see [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md).
