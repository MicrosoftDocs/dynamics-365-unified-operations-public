---
title: Packing containers with the Warehouse Management mobile app
description: This article describes how packing containers with the Warehouse Management mobile app works.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSMobileAppFlowStepListPage, WHSMobileAppFlowStepAddDetour,WHSMobileAppFlowStepDetourSelectFields, WHSRFMenuItem, WHSPackProfile, WHSWorker, WHSPack
ms.topic: conceptual
ms.date: 10/14/2022
ms.custom: bap-template
---

# Packing containers with the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Businesses that ship large items or have large packing areas will benefit from this mobile packing experience. The Warehouse Management mobile app provides warehouse workers with the freedom to move around while performing their packing activities.

Traditionally, warehouse workers have performed packing activities at a specific packing station configured in Dynamics 365 Supply Chain Management, using a process optimized for shipments of small to medium sized parcels. To improve efficiency when working in larger packing areas, and to better support the packing and shipment of larger items, the Dynamics 365 Warehouse Management mobile app provides a mobile packing experience that gives workers the freedom to move around while performing packing activities.
This article describes how to use the shipment container packing process on the Warehouse Management mobile app, which can be used in combination with the Supply Chain Management web client **Pack** page process. You can read more about the  warehouse management packing process in [Pack containers for shipment](packing-containers.md).

## The Warehouse Management mobile app packing process

As soon as the shipment inventory items have been brought forward to the packing area, workers can start the **Pack inventory into containers** process on the Warehouse Management mobile app.

![Warehouse app packing flow.](media/wma-packing-flow.png "Warehouse app packing flow")

To leverage all the supported packing processes on the Warehouse Management mobile app, you must set up three mobile device menu items:

- **Pack inventory into containers** - Used for the main process to pack items into containers.
- **Container creation** - Used to create containers going to be used to pack shipment items into.
- **Container closing** -  Used to close the shipment containers.

We recommend that you use the [detour]( warehouse-app-detours.md) functionality to ease the Warehouse Management mobile app operations by having the **Container creation** and **Container closing** embedded into the **Pack inventory into containers** menu item. We also recommend that you add several lookup options to the Warehouse Management mobile app by using [data inquiries](warehouse-app-data-inquiry.md) in combination with the [detour]( warehouse-app-detours.md) functionality. This is especially effective in situations involving unreadable or missing barcodes.

### Pack inventory into containers

During the *Pack inventory into containers* process, workers must identify and confirm the following information:

- **Packing location** - Where the container packing occurs (you can assign default values for each worker by going to **Warehouse management \> Setup \> Worker**).
- **Shipment ID** - To validate which inventory items to pack.
- **Item number** and **Quantity** - To identify what is going to get packed.
- **Container ID** - The container where the shipping items will be packed into.

> [!NOTE]
> A default **Container packing policy** must be assigned to each relevant worker on the **Warehouse management \> Setup \> Worker** page.

### Create containers

Workers can create containers using the Warehouse Management mobile app provided they have the following information:

- **Packing location** - The location where the container is created (you can assign default values for each worker by going to **Warehouse management \> Setup \> Worker** and/or by setting up a [detour](warehouse-app-detours.md)).
- **Shipment ID** - To validate which inventory items should be packed into the container (you can assign a default value by setting up a [detour](warehouse-app-detours.md))
- **Container type ID** - To identify the maximum values for the maximum physical volume and weight capacity for the container.
- **Container ID** - A unique number that identifies the shipping container.

> [!NOTE]
> A default **Container packing policy** must be assigned to each relevant worker on the **Warehouse management \> Setup \> Worker** page.

### Close a container

Workers can trigger the container closing process directly using a Warehouse Management mobile app menu, or you can set up a [detour](warehouse-app-detours.md) to embed it into the **Pack inventory into containers** menu item. During this process, teh following values must be specified:

- **Container ID** - Identifies the container being closed.
- **Weight** - The weight of the container. The system assigns a default value based on the item master weight definition.

## Supported an unsupported processes

The following table shows which processes are and aren't supported when using the Warehouse Management mobile app container packing process when compared to using the Supply Chain management web client **Pack** page.

| Logic | Supported in the mobile app | Notes |
|---|---|---|
| Items enabled for **Catch weight** | No | |
| Identification of license plate | (No) | Only **Shipment ID** identification is supported. The from license plate will be selected automatically. |
| Identification of tracking dimensions | (No) | Tracking dimensions related to the shipment will be selected automatically. |
| Identification of product variant dimensions | Yes | |
| Identification via GS1 barcode scanning | No | |
| Identification item via barcode setup | (Yes) | But quantity and unit (piece-by-piece) scanning is not supported |
| New container | Yes | Both via **Container creation** mobile device menu item incl. container type capturing and number sequence defaulting when having *Container ID mode* as **Auto**. But as well container ID creation when using the *Autocreate container at container close* process <!--KFM: I don't understand this. Please clarify. --> |
| Print container label | Yes | Labels can be printed automatically during **Container creation** process or manually using the **Print container label** mobile device menu item. For more information about how to set this up, see  [Print container labels](print-container-labels.md). |
| Close container | Yes | Via the **Container closing** mobile device menu item, which also captures the weight. |
| Release container | No | Only possible based on the container closing policy (not available as a mobile device menu option). Workers aren't able to trigger the release, or reply yes or now, using the mobile app. <!--KFM: Please confirm my rephrasing. --> |
| Reopen container | No | |
| Change container packing policy | No | The default policy assigned to each worker (on the **Warehouse management \> Setup \> Worker** page) is always used. |
| Release shipment | No | |
| Work details | (Yes) | Can be made visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md). |
| Containers for shipment (Open/Closed) | (Yes) | Can be made visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md). |
| Shipment details | (Yes) | Can be made visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md). |
| Display dimensions | (No) | Can be made visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md), but capturing of dimensions isn't supported. |
| Manifest containers | No | Only automatic manifesting setup is supported |
| Unmanifest containers | No | |
| Manifest container group | No | No weight capturing process is supported. |
| Unmanifest container group | No | |
| Manifest shipment | No | No weight capturing process is supported. |
| Unmanifest shipment | No | |
| Transport route rate details | (No) | Can be made visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md). |
| Transport shipment accessorial charges | (No) | Can be made visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md). |
| Transport status | (No) | Can be made visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md). |
| Print packing slip | No | The setting to process sales packing slips as part of closing the last container for a shipment won't apply when using the Warehouse Management mobile app. |
| Print container content | (No) | Only automatic printing (as part of the the close-container process) can be setup. |
| Print shipping label | (No) | Only automatic printing (as part of the the close-container process) can be setup. |
| Pack (all shipment items) | No | Each item number must be identified and packed individually. |
| Pack items (based on defined quantity) | (Yes) | Yes, but only *after* the item number has been identified by updating the quantity as part of the *Pack inventory into containers* process |
| Container group license plate ID with delayed work creation | No | It isn't possible to specify a grouping license plate ID |
| Container type creation | No | |

## Next steps

- Work through an example of how to set up and use this feature by reading [Example scenario – Pack containers with the Warehouse Management mobile app](warehouse-app-pack-containers-scenario.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
