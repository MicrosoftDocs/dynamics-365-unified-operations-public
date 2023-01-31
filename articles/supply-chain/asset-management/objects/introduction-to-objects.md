---
# required metadata

title: Introduction to assets
description: This article provides an overview of assets in Asset Management.
author: johanhoffmann
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetTimeline, EntAssetObjectTableLookup, EntAssetObjectTableParent, EntAssetObjectOverview, EntAssetObjectImage, EntAssetObjectTable, EntAssetLifecycleStateLog, EntAssetObjectWorkOrderActive, EntAssetObjectAttribute
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: ["2214", "intro-internal"]
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Introduction to assets

[!include [banner](../../includes/banner.md)]

 

This article provides an overview of assets in Asset Management. An *asset* is any type of equipment, such as a machine or a machine part, that requires maintenance, service, or repair.

An asset is automatically updated with related information. For example, this related information might be about new or updated work orders. You can create assets by using either the **All assets** menu item or the **Pending assets** menu item. This article explains how to create assets by using the **All assets** menu item. For information about how to create assets by using the **Pending assets** menu item, see [Create assets based on purchase orders](../objects/create-objects-based-on-purchase-orders.md).

## All assets

Select **Asset management** \> **Assets** \> **All assets**. The **All assets** list page shows all assets and some of the information that is related to them. To view only active assets, select **Active assets**. To view only assets that are installed on the functional locations that you're related to as a maintenance worker, select **My active assets**. (This relation is set up on the **Workers** page. For more information, see [Maintenance workers and worker groups](../setup-for-objects/workers-and-worker-groups.md).)

In the **All assets** grid view, select a link in the **Asset** column to view the details of the selected record. To edit the record, select the **Edit** button. The details view shows detailed information that is related to the asset. A **Related information** pane on the right contains additional asset-related information. Expand the pane to show the related information for the selected asset.

The buttons on the Action Pane are organized on tabs. The following table briefly describes the buttons that are related to Asset Management.

| Button name          | Description                                                                                                                                                       |
|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Edit                 | Edit the selected asset.                                                                                                                                         |
| New                  | Create a new asset.                                                                                                                                                |
| Delete               | Delete the selected asset.                                                                                                                                       |
| Move asset           | Move assets to another asset structure, or to another location in the same asset structure.                                                                                         |
| Replace asset        | Replace one child asset in an asset hierarchy with another asset.                                                                                                  |
| Install asset        | Install an asset on a functional location.                                                                                                                          |
| Copy asset           | Copy an asset hierarchy to another asset.                                                                                                                          |
| Requests             | Open the **Active requests** list page, where you can view maintenance requests that have been created for the selected asset.                                                                         |
| Event history        | View an overview of the various registrations that have been made on the asset.                                                                                                         |
| Asset BOM            | View a list of all items (spare parts and other items) that are used on an asset.                                                                                  |
| Work orders          | Open the **Active work orders** list page, where you can view work orders for the asset.                                                                                        |
| Checklist            | View an overview of maintenance checklists and measurements that have been registered on the asset.                                                                                                 |
| Maintenance downtime | Create or view maintenance downtime registrations on the asset.                                                                                                       |
| Project transactions | View all posted transactions that are related to work orders that have been created for the asset.                                                                                       |
| Asset measures       | Create or view asset measures on the asset.                                                                                                               |
| Maintenance schedule | Open the **Open maintenance schedule** list page, where you can view maintenance plans, maintenance requests, and maintenance rounds that are associated with the asset, and that have a status of **Created**. |
| Update asset state   | Update the asset lifecycle state. You can select multiple assets on the **All assets** list page and then update the asset lifecycle state for all of them at the same time.              |
| Lifecycle state log  | Open a log that shows the lifecycle states of the selected asset.                                                                                                                 |
| Asset documents      | View a list of the documents that are attached to an asset. These documents are set up at **Asset management** \> **Setup** \> **Asset documents**.                 |
| Attributes           | Create or view asset attributes.                                                                                                                             |
| Image                | Select an image for the asset.                                                                                                                                   |
| Parent assets        | View parent asset history for the selected asset.                                                                                                                |
| Functional locations | View functional location history for the selected asset.                                                                                                          |
| Condition assessment | Register condition assessment measurements on the asset.                                                                                                         |
| Faults               | Open the **Asset faults** list page,  where you can view faults that have been registered on the asset.                                                                                             |
| Cost control         | Compare budget costs and actual costs on the asset.                                                                                                              |
| Hour control         | Compare forecast hours and actual hours on the asset.                                                                                                              |
| Asset KPIs           | Calculate and view key performance indicators (KPIs) for the asset.                                                                                              |
| Job types            | View an overview of the current default job types for the asset.                                                                                                            |
| Criticality types    | View or update asset criticality types.                                                                                                                              |
| Spare parts          | View a list of approved and alternative spare parts that can be used on the asset.                                                                               |
| Asset consumption    | Print a report that shows consumption registrations on the asset.                                                                                                |
| Asset fault          | Print a report that shows fault registrations on the asset.                                                                                                      |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]