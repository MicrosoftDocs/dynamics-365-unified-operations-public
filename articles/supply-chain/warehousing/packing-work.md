---
title: Packing work for packing outbound containers and processing shipments
description: Learn about the "Packing" work order type, which manages work for packing containers and supports partial shipments of packed containers.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSPackingWorkLocationSetup, WHSPack, WHSContainerTable, WHSCloseContainerProfile, WHSPackProfile
ms.topic: how-to
ms.date: 10/05/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Packing work for packing outbound containers and processing shipments

[!INCLUDE [banner](../../includes/banner.md)]

This article describes the *Packing* work order type, which manages work for packing containers. It supports partial shipments of packed containers that are related to loads where inventory items remain unpacked. Packing work lets you use [confirm and transfer](confirm-and-transfer.md) functionality to confirm outbound shipments that are associated with containers.

Packing work is automatically created when inventory that is related to source document work is put in locations of the *Packing location* type. The work consists of two lines, one for *Pick* and one for *Put*. The system automatically maintains it as part of a container close and reopen process.

> [!NOTE]
> In Supply Chain Management version 10.0.45 and later, the Warehouse Management mobile app can record the worker IDs of workers that use it to do packing work. Learn more in [Create containers](warehouse-app-packing-containers.md#create-containers), [Close containers](warehouse-app-packing-containers.md#close-containers), and [Pack inventory into containers](warehouse-app-packing-containers.md#pack-inventory-into-containers).

For more information about how to set up and use the container packing process, see [Pack containers for shipment](packing-containers.md).

<a name="set-up-packing-location"></a>

## Set up a location for packing work

Use the following procedure to set up packing locations. For each location, you can select whether the system automatically creates packing work.

1. Go to **Warehouse management** > **Setup** > **Packing** > **Packing station setup**.
1. On the Action Pane, select **New** to add a packing station setup record.
1. In the new record, set the following fields:

    - **Warehouse** – Select or enter the warehouse where the packing location is located.
    - **Location** – Select or enter the packing location. Assign this location to a location profile that uses the location type configured as the packing location type for your company on the **Warehouse management parameters** page. Learn more in [Pack containers for shipment](packing-containers.md).
    - **Create packing work** – Select this checkbox to create packing work each time that items are delivered to the packing location. The work includes links to related load lines, so that partial loads can be packed and shipped.
    - **Container packing policy** – Select the container closing profile to stamp on each work container that's converted into a packing station container at this location. Learn more in [Convert work containers at a packing station](#convert-containers-at-packing-station).
    - **Force container closing profile** – Select this checkbox to require that the system always apply the **Container packing policy** value that you set here, instead of any closing profile that's set for the worker or for the default packing profile on the **Pack profile setup** page.
    - **Default packing profile** – Select the default packing profile to use for containers that are packed at this packing station.

> [!CAUTION]
> Before enabling the **Create packing work** option, make sure the packing station is empty (no items are present).

<a name="convert-containers-at-packing-station"></a>

## Convert work containers at a packing station

Supply Chain Management works with two kinds of containers, and it handles them differently:

- *Work containers* are created by the [wave containerization](wave-containerization.md) process, which plans the contents of each container before picking begins. The system closes a work container automatically, as the final step of work execution. Because the container is already closed by the time it reaches the packing station, workers can't weigh it, manifest it through a transportation management system, or print a shipping label for it as an individual container.
- *Packing station containers* are created by a worker at a packing station. They stay open until a worker explicitly closes them, so they can be weighed, manifested, and labeled first.

You can set up the system so that it converts a work container into a packing station container when the container arrives at a packing station. The container then stays open, and workers handle it exactly as if they built it at the packing station themselves.

### Prerequisites

Before you can use the functionality that's described in this section, ensure your system meets the following requirements:

- You must be running Supply Chain Management version 10.0.49 or later.
- The packing station must be set up to create packing work, as described in [Set up a location for packing work](#set-up-packing-location).

### When the system converts a container

The system converts a container only when all the following conditions are met. Otherwise, the system automatically closes the container and packing continues as usual.

- The put is the step that closes the work. The system evaluates conversion only when a put completes both the work line and the whole work header. Earlier puts never trigger conversion.
- The put location is a packing station where **Create packing work** is turned on, and the work is for an outbound shipment.
- The container is still open. A container that's already closed can't be converted.
- The contents of the container belong to a single work header. The system skips any container that is shared with another work, that has a parent container, or that is itself a parent container.

When the system converts a container, it makes the following changes:

- It moves the container build ID to a separate field, where it remains available for tracing, and it clears the original field. As a result, no other process treats the container as a work container any longer.
- It stamps the container with the container closing profile that's defined for the packing station.
- It updates the container, and each of its lines, to reflect the packing station location and the dimensions that the items were put to, including the tote license plate, if one was used.

Conversion occurs before the system creates the packing work for the put, so the new packing work reflects the converted container.

> [!NOTE]
> The system doesn't convert containers that are marked as error containers. Instead, the system unpacks them. It removes the container reference from the work lines and deletes the container, so that the items arrive at the packing station as unpacked inventory.

### Choose how the system handles work containers put at a packing station

To choose how the system handles work containers that are put at a packing station, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse management parameters**.
1. Open the **Packing** tab.
1. Set the **Convert work containers to packing station containers** field to one of the following values:

    - *Not allowed* – The system never converts work containers. Workers can still put them at a packing station, but the system automatically closes each container during work execution, as it did before this functionality was introduced.
    - *Aligned with work headers* – The system converts each work container whose contents belong to a single work header, as described in [When the system converts a container](#when-the-system-converts-a-container). The system automatically closes containers that don't meet the conditions.

1. Close the page to save your changes.

### Set up the packing station for container conversion

A work container can arrive at any packing station, so the system can't infer which container closing profile to stamp on it. You must therefore define the profile on each packing station where conversion can occur.

Set the **Container packing policy** field for the packing station, as described in [Set up a location for packing work](#set-up-packing-location). If a work container reaches a packing station where this field is blank, the system shows the following error, and the put can't be completed: *A container closing profile must be specified on the packing station setup to convert work containers to packing station containers.*

To prevent workers from applying a different profile to containers at the station, also turn on the **Force container closing profile** option. The system then always applies the profile that you specify here, and it ignores any profile that's set for the worker or for the default packing profile. If you use this option together with the **Default packing profile** field, the two profiles must specify the same container closing profile.

## Example scenario

This example scenario shows how to process an outbound sales order flow by packing a container and shipping a partial load.

### Make sample data available

To work through this scenario by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Also, you must select the **USMF** legal entity before you begin.

You can also use this scenario as guidance for using the feature on a production system. However, in that case, you must substitute your own values for each setting that is described here.

### Configure packing work for warehouse packing location

To get started, you must configure the *Packing* work process for a specific warehouse and location.

1. Go to **Warehouse management** > **Setup** > **Packing** > **Packing station setup**.
1. On the Action Pane, select **New** to add a setup record.
1. In the new record, set the following values:

    - **Warehouse:** *62*
    - **Location:** *Pack*
    - **Create packing work:** *Yes*

1. Close the **Packing station setup** page.

### Create a load template that allows partial shipping

To enable a load to be delivered over multiple shipments, associate it with a load template that allows partial shipping. Follow these steps to create the required template.

1. Go to **Warehouse management** > **Setup** > **Load** > **Load templates**.
1. On the Action Pane, select **New** to add a setup record.
1. In the new record, set the following values:

    - **Load template ID:** *Partial*
    - **Allow load split during ship confirm:** *Yes*

1. Close the **Load templates** page.

Learn more in [Confirm and transfer](Confirm-and-transfer.md).

### Process a sales order

Follow these steps to process a sales order and partially ship it.

1. Complete the [example scenario](packing-containers.md#scenario) that's provided in [Pack containers for shipment](packing-containers.md). During that scenario, you create a sales order for two pieces of one item. You then pack just one of the pieces into a container and close the container. Make a note of the shipment ID that you create, as instructed in the scenario.
1. Go to **Warehouse management** > **Work** > **All work**.
1. In the filter area, select the **Show closed work** checkbox. Then enter the shipment ID in the **Filter** field, and select to filter by **Shipment ID** value. You should now see three work headers. One is for the sales order picking work and has a status of *Closed*. Two are for the packing process: one is related to the closed container and has a status of *Closed*, and the other is related to the unpacked remaining item and has a status of *Open*.
1. Select the **Load ID** value for any of the work headers to open **Load details** page for the load.
1. Switch to the **Header** view.
1. On the **General** FastTab, select the **Edit** button for the **Load template ID** field. Then select the partial shipping load template that you created for this scenario (*Partial*).
1. On the Action Pane, on the **Ship and receive** tab, in the **Confirm** group, select **Outbound shipment**.
1. In the **Ship confirm** dialog box, select the **Split quantity to new load** option.
1. Select **OK**.

You shipped one container that is related to the original load, and the system creates a new load for the remaining items that must still be packed into containers.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
