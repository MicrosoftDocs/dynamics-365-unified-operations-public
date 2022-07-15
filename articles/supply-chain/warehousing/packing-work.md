---
title: Packing work for packing outbound containers and processing shipments
description: This article describes the "Packing" work order type, which manages work for packing containers and supports partial shipments of packed containers related to loads with remaining unpacked inventory items. Packing work lets you use "confirm and transfer" to confirm outbound shipments that are associated with containers.
author: perlynne
ms.date: 7/13/2022
ms.topic: article
ms.search.form: WHSPackingWorkLocationSetup, WHSPack, WHSContainerTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29
---

# Packing work for packing outbound containers and processing shipments

[!include [banner](../../includes/banner.md)]

This article describes the *Packing* work order type, which manages work for packing containers and supports partial shipments of packed containers related to loads with remaining unpacked inventory items. Packing work lets you use [confirm and transfer](confirm-and-transfer.md) to confirm outbound shipments that are associated with containers.

Packing work is created automatically when inventory related to source document work is put at locations of type *Packing location*. The work will consist of two lines, one for *Pick* and one for *Put*, and the work will automatically be maintained as part of a container close/reopen process.

For more information about how to set up and use the container packing process, see [Pack containers for shipment](packing-containers.md).

## Turn on the feature

If your system doesn't already include the features described in this article, go to [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and turn on the following features (which are part of the *Warehouse management* module) in the following order:

1. *Confirm and transfer*
1. *Packing work for packing stations*

## Set up a location for packing work

Use the following procedure to set up packing locations. For each location, you can choose whether the system automatically should create packing work or not.

 1. Go to **Warehouse management > Setup > Packing > Packing station setup**
 1. Select **New** on the Acton Pane to add a new packing station setup record.
 1. Make the following settings in the new record:
    - **Warehouse** - Select or enter the warehouse where the packing location is located.
    - **Location** - Select or enter the packing location. This location must be assigned to a **Location profile** that uses the **Location type** configured as the **Packing location type** configured for your company on the **Warehouse management parameters** page (see also [Pack containers for shipment](packing-containers.md)).
    - **Create packing work** - Select this check box to create packing work each time items are delivered to this location. The work will include links to related load lines, which makes it possible to pack and ship partial loads. <!-- KFM: What happens when we disable this? -->

## Example scenario

This example scenario shows how to process an outbound sales order flow by packing a container and shipping a partial load.

### Make sample data available

To work through this scenario using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

You can also use this scenario as guidance for using the feature on a production system. However, in that case, you must substitute your own values for each setting that is described here.

### Configure packing work for warehouse packing location

To get started, you must configure the *Packing* work process for a specific warehouse and location. Do the following steps:

1. Go to **Warehouse management > Setup > Packing > Packing station setup**.
1. Select **New** on the Acton Pane to add a new setup record.
1. Make the following settings in the new record:
    - **Warehouse:** *62*
    - **Location:** *Pack*
    - **Create packing work:** *Yes*
1. Close the **Packing station setup** page.

### Create a load template that allows partial shipping

To allow a load to be delivered over multiple shipments, you must associate it with a load template that allows partial shipping. Follow these steps to create the required template:

1. Go to **Warehouse management > Setup > Load > Load templates**
1. Select **New** on the Acton Pane to add a new setup record
1. Make the following settings in the new record
    - **Load template ID:** *Partial*.
    - **Allow load split during ship confirm:**  *Yes*.
1. Close the **Load templates** page

For more information, see [Confirm and transfer](Confirm-and-transfer.md).

### Process a sales order

Follow these steps to process a sales order and partially ship it:

1. Start by following the [example scenario](packing-containers.md#scenario) provided in the [Pack containers for shipment](packing-containers.md) topic. During this scenario, you will create a sales order for two pieces of one item and pack just one of the pieces into a container and close the container. You should have also made a note of the shipment ID that you created, as instructed in the example scenario.
1. Open **Warehouse management > Work > All work**.
1. In the filter area, select the **Show closed work** check box. Then enter your shipment ID into the **Filter** field and choose to filter by  **Shipment ID**. You should now see three work headers. One is for the sales order picking work, which is *Closed*. Two are for the packing process, where one is *Closed* and related to the closed container, and one is *Open* for the still unpacked remaining item.
1. Select the **Load ID** value for any of the work headers to go to **Load details** page for the load.
1. Select on the **Header** view option.
1. On the **General** FastTab, Select the Edit button for the **Load template ID** field. Then select the partial-shipping load template you created for this scenario (*Partial*).
1. On the Action Pane, open the **Ship and receive** tab and, from the **Confirm** group, select **Outbound shipment**.
1. The **Ship confirm** dialog opens. Select the **Split quantity to new load** radio button.
1. Select **OK**.

You have now shipped one container related to the original load and the system has created a new load for the remaining items that still need to get packed into containers.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]