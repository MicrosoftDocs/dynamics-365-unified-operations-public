---
title: Packing containers with the Warehouse Management mobile app
description: This article describes the process for packing containers by using the Warehouse Management mobile app.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSMobileAppFlowStepListPage, WHSMobileAppFlowStepAddDetour,WHSMobileAppFlowStepDetourSelectFields, WHSRFMenuItem, WHSPackProfile, WHSWorker, WHSPack
ms.topic: conceptual
ms.date: 10/14/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Packing containers with the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.31 GA -->

Traditionally, warehouse workers have performed packing activities at a specific packing station that is configured in Microsoft Dynamics 365 Supply Chain Management, and they have used a process that is optimized for shipments of small to medium-sized parcels. To help improve efficiency in larger packing areas, and to better support the packing and shipment of larger items, the Dynamics 365 Warehouse Management mobile app provides a mobile packing experience that gives workers the freedom to move around while they perform their packing activities.

This article describes how to use the shipment container packing process in the Warehouse Management mobile app. This process can be used in combination with the process on the **Pack** page in the Supply Chain Management web client. For more information about the warehouse management packing process, see [Pack containers for shipment](packing-containers.md).

## The Warehouse Management mobile app packing process

As soon as the shipment inventory items have been brought forward to the packing area, workers can start the *Pack inventory into containers* process in the Warehouse Management mobile app.

![Warehouse app packing flow.](media/wma-packing-flow.png "Warehouse app packing flow")

To take advantage of all the supported packing processes in the Warehouse Management mobile app, you must set up three mobile device menu items:

- **Pack inventory into containers** – This menu item is used for the main process of packing items into containers.
- **Container creation** – This menu item is used to create containers that shipment items will be packed into.
- **Container closing** – This menu item is used to close the shipment containers.

We recommend that you use the [detour]( warehouse-app-detours.md) functionality. This functionality makes Warehouse Management mobile app operations easier by embedding the *Container creation* and *Container closing* processes into the **Pack inventory into containers** menu item. We also recommend that you add several lookup options to the Warehouse Management mobile app by using [data inquiries](warehouse-app-data-inquiry.md) in combination with the [detour]( warehouse-app-detours.md) functionality. This approach is especially effective in situations where bar codes are unreadable or missing.

### Pack inventory into containers

During the *Pack inventory into containers* process, workers must identify and confirm the following information:

- **Packing location** – This value identifies the location where container packing occurs. (You can assign a default value for each worker by going to **Warehouse management \> Setup \> Worker**.)
- **Shipment ID** – This value is used to validate which inventory items should be packed.
- **Item number** and **Quantity** – These values identify what will be packed.
- **Container ID** – This value identifies the container that the shipping items will be packed into.

> [!NOTE]
> A default container packing policy must be assigned to each relevant worker on the **Worker** page (**Warehouse management \> Setup \> Worker**).

### Create containers

To create containers by using the Warehouse Management mobile app, workers must have the following information:

- **Packing location** – This value identifies the location where the container is created. (You can assign a default value for each worker by going to **Warehouse management \> Setup \> Worker** and/or by setting up a [detour](warehouse-app-detours.md).)
- **Shipment ID** – This value is used to validate which inventory items should be packed into the container. (You can assign a default value by setting up a [detour](warehouse-app-detours.md).)
- **Container type ID** – This value is used to identify the maximum physical volume and maximum weight capacity of the container.
- **Container ID** – This value is a unique number that identifies the shipping container.

> [!NOTE]
> A default container packing policy must be assigned to each relevant worker on the **Worker** page (**Warehouse management \> Setup \> Worker**).

### Close containers

Workers can trigger the *Container closing* process directly, by using a Warehouse Management mobile app menu. Alternatively, you can set up a [detour](warehouse-app-detours.md) to embed the process into the **Pack inventory into containers** menu item. During the *Container closing* process, the following values must be specified:

- **Container ID** – The container that is being closed.
- **Weight** – The weight of the container. The system assigns a default value, based on the item master weight definition.

## Supported and unsupported processes

The following table shows which processes are and aren't supported when the container packing process in the Warehouse Management mobile app is used instead of the **Pack** page in the Supply Chain management web client. Some rows use parentheses in the *Supported in the mobile app* column; these indicate either a partial-yes or partial-no status, which is clarified in the *Notes* column.

| Logic | Supported in the mobile app | Notes |
|---|---|---|
| Items enabled for **Catch weight** | No | |
| Identification of license plate | (No) | Only shipment ID identification is supported. The "from" license plate will be selected automatically. |
| Identification of tracking dimensions | (No) | Tracking dimensions that are related to the shipment will be selected automatically. |
| Identification of product variant dimensions | Yes | |
| Identification via GS1 bar code scanning | No | |
| Identification item via bar code setup | (Yes) | However, quantity and unit (piece-by-piece) scanning isn't supported. |
| New container | Yes | <p>Containers can be created either automatically by using the *Autocreate container at container close* process or manually by using the **Container creation** mobile device menu item. The menu item also captures the container type and enters a default number sequence if the **Container ID mode** field is set to *Auto*. |
| Print container label | Yes | Labels can be printed either automatically during *Container creation* process or manually by using the **Print container label** mobile device menu item. For more information about how to set up label printing, see [Print container labels](print-container-labels.md). |
| Close container | Yes | Containers can be closed by using the **Container closing** mobile device menu item, which also captures the weight. |
| Release container | No | The release of containers depends on the container closing policy. It isn't available as a mobile device menu option. Workers can't trigger or confirm a release by using the mobile app. |
| Reopen container | No | |
| Change container packing policy | No | The default policy that is assigned to each worker on the **Worker** page (**Warehouse management \> Setup \> Worker**) is always used. |
| Release shipment | No | |
| Work details | (Yes) | You can make this information visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md). |
| Containers for shipment (Open/Closed) | (Yes) | You can make this information visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md). |
| Shipment details | (Yes) | You can make this information visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md). |
| Display dimensions | (No) | You can make this information visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md). However, capture of dimensions isn't supported. |
| Manifest containers | No | Only automatic manifesting setup is supported |
| Unmanifest containers | No | |
| Manifest container group | No | No weight capturing process is supported. |
| Unmanifest container group | No | |
| Manifest shipment | No | No weight capturing process is supported. |
| Unmanifest shipment | No | |
| Transport route rate details | (No) | You can make this information visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md). |
| Transport shipment accessorial charges | (No) | You can make this information visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md). |
| Transport status | (No) | You can make this information visible (read-only) by setting up a [data inquiry detour](warehouse-app-data-inquiry.md). |
| Print packing slip | No | The setting for processing sales packing slips as part of closing the last container for a shipment doesn't apply when the Warehouse Management mobile app is used. |
| Print container content | (No) | Only automatic printing (as part of the *Container closing* process) can be set up. |
| Print shipping label | (No) | Only automatic printing (as part of the *Container closing* process) can be set up. |
| Pack (all shipment items) | No | Each item number must be identified and packed individually. |
| Pack items (based on defined quantity) | (Yes) | However, items can be packed only *after* the item number has been identified by updating the quantity as part of the *Pack inventory into containers* process. |
| Container group license plate ID with delayed work creation | No | No group license plate ID can be specified. |
| Container type creation | No | |

## Next steps

- Work through an example that shows how to set up and use this feature. See [Example scenario – Pack containers with the Warehouse Management mobile app](warehouse-app-pack-containers-scenario.md).
- Learn how to set up container labels and print them from the mobile app. See [Print container labels](print-container-labels.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
