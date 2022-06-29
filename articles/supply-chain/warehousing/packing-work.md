---
title: Packing work for container packing processing and 'Confirm and transfer"
description: This topic provides details about the work order type "Packing", which is optimized for managing work for container packing processing and enables the capability of using 'Confirm and transfer' for the outbound shipment confirmation for shipments associated with containers. Packing work orders store links to each related load line, which enable workers to pack and ship partial loads. For locations configured to use this feature, the system will generate a new packing work order each time items are delivered to a packing station.
author: perlynne
ms.date: 6/29/2022
ms.topic: article
ms.search.form: WHSPackingWorkLocationSetup, WHSPack, WHSContainerTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.24
---

# Packing work for outbound container packing and shipment processing

[!include [banner](../../includes/banner.md)]

This topic provides details about the work order type "Packing", which is optimized for managing work for container packing processing and enables partly shipping of the already packed containers related to loads with remaining unpacked inventory items, by using the [confirm and transfer](Confirm-and-transfer.md) capability.

The *Packing* work will automatically get created when the inventory related to source document work gets put at locations of type *Packing location*. The work will consist of two lines, one for *Pick* and one for *Put* and the work will automatically get maintained as part of a container close/reopen process.

You can read more about how to setup and use the container packing process here: [Packing containers](packing-containers.md) <!-- UPDATE!!! -->

## Turn on the feature

If your system doesn't already include the features described in this topic, go to [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and turn on the following features as part of the *Warehouse management* module in the following order:

1. *Confirm and transfer*
1. *Packing work for packing stations*

## Configure *Packing work*

You can for each packing location define if the system automatically should create *Packing* work or not. This setup gets define by:

 1. Go to **Warehouse management > Setup > Packing > Packing station setup**
 1. Select **New** on the Acton Pane to add a new setup record
 1. Make the following settings in the new record
    - **Warehouse** - Select or enter the warehouse
    - **Location** - Select or enter the packing location. Note that the locations must be related to a *Packing location type*. You can read more about how to enable the packing process here: [Packing containers](packing-containers.md) <!-- UPDATE!!! -->
    - **Create packing work** - When enabled *Packing* work will get created when items are delivered to the packing location, including links to related load lines making it possible to pack and ship partial loads.



# Example scenario

In the following example you will process an outbound sales order flow in the *Contoso demo data* company **USMF** by packing a container and shipping a partly load.

## Configure packing work for warehouse packing location

First you must configure the *Packing* work process within warehouse **62** for *Location* **Pack**:

 1. Go to **Warehouse management > Setup > Packing > Packing station setup**
 1. Select **New** on the Acton Pane to add a new setup record
 1. Make the following settings in the new record
    - **Warehouse** - Select or enter warehouse **62**
    - **Location** - Select or enter packing location **Pack**
    - **Create packing work** - Enable
 1. Close the *Packing station setup* page


## Configure *partly load shipping* via new *Load template*

To define that a load is allowed to get shipped partly you associate it with a load template allowing this:

1. Go to **Warehouse management > Setup > Load > Load templates**
1. Select **New** on the Acton Pane to add a new setup record
1. Make the following settings in the new record
    - **Load template ID** - Enter **Partly**
    - **Allow load split during ship confirm** - Enable
1. Close the *Load templates* page

You can read more about the **Confirm and transfer** capability [here](Confirm-and-transfer.md).

## Process a sales order flow

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