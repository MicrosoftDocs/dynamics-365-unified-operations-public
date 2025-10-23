---
title: Packing work for packing outbound containers and processing shipments
description: Learn about the "Packing" work order type, which manages work for packing containers and supports partial shipments of packed containers.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 7/13/2022
ms.reviewer: kamaybac
ms.search.form: WHSPackingWorkLocationSetup, WHSPack, WHSContainerTable
---

# Packing work for packing outbound containers and processing shipments

[!include [banner](../../includes/banner.md)]

This article describes the *Packing* work order type, which manages work for packing containers and supports partial shipments of packed containers that are related to loads where inventory items remain unpacked. Packing work lets you use [confirm and transfer](confirm-and-transfer.md) functionality to confirm outbound shipments that are associated with containers.

Packing work is automatically created when inventory that is related to source document work is put in locations of the *Packing location* type. The work consists of two lines, one for *Pick* and one for *Put*, and is automatically maintained as part of a container close/reopen process.

> [!NOTE]
> In Supply Chain Management version 10.0.45 and later, the Warehouse Management mobile app can record the worker IDs of workers that use it to do packing work. Learn more in [Create containers](warehouse-app-packing-containers.md#create-containers), [Close containers](warehouse-app-packing-containers.md#close-containers), and [Pack inventory into containers](warehouse-app-packing-containers.md#pack-inventory-into-containers).

For more information about how to set up and use the container packing process, see [Pack containers for shipment](packing-containers.md).

## Set up a location for packing work

Use the following procedure to set up packing locations. For each location, you can select whether the system automatically creates packing work.

1. Go to **Warehouse management \> Setup \> Packing \> Packing station setup**.
1. On the Action Pane, select **New** to add a packing station setup record.
1. In the new record, set the following fields:

    - **Warehouse** – Select or enter the warehouse where the packing location is located.
    - **Location** – Select or enter the packing location. This location must be assigned to a location profile that uses the location type that is configured as the packing location type for your company on the **Warehouse management parameters** page. Learn more in [Pack containers for shipment](packing-containers.md).
    - **Create packing work** – Select this checkbox to create packing work each time that items are delivered to the packing location. The work includes links to related load lines, so that partial loads can be packed and shipped.

> [!CAUTION]
> Before enabling the **Create packing work** option, make sure the packing station is empty (no items are present).

## Example scenario

This example scenario shows how to process an outbound sales order flow by packing a container and shipping a partial load.

### Make sample data available

To work through this scenario by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

You can also use this scenario as guidance for using the feature on a production system. However, in that case, you must substitute your own values for each setting that is described here.

### Configure packing work for warehouse packing location

To get started, you must configure the *Packing* work process for a specific warehouse and location.

1. Go to **Warehouse management \> Setup \> Packing \> Packing station setup**.
1. On the Action Pane, select **New** to add a setup record.
1. In the new record, set the following values:

    - **Warehouse:** *62*
    - **Location:** *Pack*
    - **Create packing work:** *Yes*

1. Close the **Packing station setup** page.

### Create a load template that allows partial shipping

To enable a load to be delivered over multiple shipments, you must associate it with a load template that allows for partial shipping. Follow these steps to create the required template.

1. Go to **Warehouse management \> Setup \> Load \> Load templates**.
1. On the Action Pane, select **New** to add a setup record.
1. In the new record, set the following values:

    - **Load template ID:** *Partial*
    - **Allow load split during ship confirm:** *Yes*

1. Close the **Load templates** page.

Learn more in [Confirm and transfer](Confirm-and-transfer.md).

### Process a sales order

Follow these steps to process a sales order and partially ship it.

1. Complete the [example scenario](packing-containers.md#scenario) that is provided in [Pack containers for shipment](packing-containers.md). During that scenario, you'll create a sales order for two pieces of one item. You'll then pack just one of the pieces into a container and close the container. You should make a note of the shipment ID that you create, as instructed in the scenario.
1. Go to **Warehouse management \> Work \> All work**.
1. In the filter area, select the **Show closed work** checkbox. Then enter the shipment ID in the **Filter** field, and select to filter by **Shipment ID** value. You should now see three work headers. One is for the sales order picking work and has a status of *Closed*. Two are for the packing process: one is related to the closed container and has a status of *Closed*, and the other is related to the unpacked remaining item and has a status of *Open*.
1. Select the **Load ID** value for any of the work headers to open **Load details** page for the load.
1. Switch to the **Header** view.
1. On the **General** FastTab, select the **Edit** button for the **Load template ID** field. Then select the partial shipping load template that you created for this scenario (*Partial*).
1. On the Action Pane, on the **Ship and receive** tab, in the **Confirm** group, select **Outbound shipment**.
1. In the **Ship confirm** dialog box, select the **Split quantity to new load** option.
1. Select **OK**.

You have now shipped one container that is related to the original load, and the system has created a new load for the remaining items that must still be packed into containers.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
