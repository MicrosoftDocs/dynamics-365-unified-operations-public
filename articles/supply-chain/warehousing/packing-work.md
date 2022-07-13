---
title: Packing work for outbound container packing and shipment processing
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

# Packing work for outbound container packing and shipment processing

[!include [banner](../../includes/banner.md)]

This article describes the *Packing* work order type, which manages work for packing containers and supports partial shipments of packed containers related to loads with remaining unpacked inventory items. Packing work lets you use [confirm and transfer](confirm-and-transfer.md) to confirm outbound shipments that are associated with containers.

Packing work is created automatically when inventory related to source document work is put at locations of type *Packing location*. The work will consist of two lines, one for *Pick* and one for *Put*, and the work will automatically be maintained as part of a container close/reopen process.

For more information about how to set up and use the container packing process, see [Packing containers](packing-containers.md).

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
    - **Location** - Select or enter the packing location. This location must be assigned to a **Location profile** that uses the **Location type** configured as the **Packing location type** configured for your company on the **Warehouse management parameters** page (see also [Packing containers](packing-containers.md)).
    - **Create packing work** - Select this check box to create packing work each time items are delivered to this location. The work will include links to related load lines, which makes it possible to pack and ship partial loads. <!-- KFM: What happens when we disable this? -->

## Example scenario

This example scenario shows how to process an outbound sales order flow by packing a container and shipping a partly load.

### Make sample data available

To work through this scenario using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

You can also use these scenarios as guidance for using the feature on a production system. However, in that case, you must substitute your own values for each setting that is described here.

### Configure packing work for warehouse packing location

To get started, you must configure the *Packing* work process for **Warehouse** *62*, **Location** *Pack*. Do the following steps:

 1. Go to **Warehouse management > Setup > Packing > Packing station setup**.
 1. Select **New** on the Acton Pane to add a new setup record.
 1. Make the following settings in the new record:
    - **Warehouse:** *62*
    - **Location:** *Pack*
    - **Create packing work:** *Yes*
 1. Close the **Packing station setup** page.

### Create a new load template to set up partial load shipping <!-- KFM: Continue here -->

To define that a load is allowed to get shipped partly you associate it with a load template allowing this:

1. Go to **Warehouse management > Setup > Load > Load templates**
1. Select **New** on the Acton Pane to add a new setup record
1. Make the following settings in the new record
    - **Load template ID** - Enter **Partly**
    - **Allow load split during ship confirm** - Enable
1. Close the *Load templates* page

You can read more about the **Confirm and transfer** capability [here](Confirm-and-transfer.md).

### Process a sales order flow

1. Follow the [example](packing-containers.md) <!-- Link to Example scenario section around line 230 in Packing-containers.md -->  which will pack 1 pcs of an item into a container and close the container
1. Open **Warehouse management > Work > All work**
1. In the filter area enable **Show closed work** and filter by the **Shipment ID**. You should now see three work headers. One *Closed* for the sales order picking, bringing the inventory items to the **Pack** location. Two for the packing process where one is *Closed* related to the closed container, and one *Open* for the remaining packing of the last item.
1. Click on the **Load ID** value for one of the work headers to go to **Load details** page for the actual load
1. Click on the **Header** view option
1. In the **General** section click to edit the **Load template ID** field and select the newly create **Partly** value
1. In the Action Pane select **Ship and receive > Confirm > Outbound shipment**
1. In the **Ship confirm** dialog box, in the **Load split method during ship confirm** field, select **Split quantity to new load**.
1. Select OK

In this example you have now shipped one container related to the original load and the system has created a new load for the remaining items which are missing to get packed into containers.


<!-- Update existing scenario to only pack 1 pcs of of the two in Packing-containers.md 

1. In the **PACK ITEM** section keep **Quantity** field equal to "1.00" and lookup and select *Item number* **A0001** in the **Identifier** field. You should now have packed 1 out of the 2 pcs of item *A0001*.

Delete:  All the items for the shipment has now been packed into containers -->

[!INCLUDE[footer-include](../../includes/footer-banner.md)]