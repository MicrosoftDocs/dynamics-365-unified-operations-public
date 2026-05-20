---
title: Set up cluster picking
description: Learn how to set up cluster picking and how to apply item confirmation with cluster picking, including an outline on enabling cluster picking.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 04/24/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Set up cluster picking

[!include[banner](../includes/banner.md)]

This article describes how to enable workers to use their mobile devices to group picking work into clusters, so that they can pick items from a single location for multiple work orders at the same time. This process is called *cluster picking*.

## About cluster picking

After you release work orders to the warehouse, the worker can use a mobile device to assign the orders to a cluster. The cluster organizes the picking work for the worker. When you assign a work order to a cluster, the worker must use cluster picking to perform the picking work for the order. The worker can't use other picking methods. If you mistakenly assign a work order to a cluster, the worker must break the cluster and then re-create it.

If needed, a worker can pass a cluster to another worker. This action changes the cluster status to Passed. When the worker uses a mobile device to indicate that the picking and put away work is completed, the shipment or load must be confirmed in the client.

## Enable cluster picking

To enable cluster picking, set up the following components:

- **Cluster profiles** – Specify whether to automatically generate cluster IDs, the number of positions to use, when to break clusters, and how to sequence and verify the picking work.
- **Work templates** – Define how to create the picking work for cluster picking.
- **Location directives** – Specify where to pick items from, and where to put them.
- **Mobile device menu items** – Configure a mobile device menu item to use existing work that cluster picking directs. Then add the menu item to a mobile device menu so that it displays on mobile devices.
- **Warehouse management parameters** – Specify the number sequence to use if you want to generate identifiers for clusters.

## Set up a cluster profile

To set up a cluster profile, follow these steps:

1. Go to **Warehouse management \> Setup \> Mobile device \> Cluster profiles**.
1. Select a profile to edit or select **New** to create a new one.
1. In the header of the new or selected record, set a **Cluster profile ID**, **Name**, **Cluster type**, and **Sequence number**. The **Cluster type** specifies for which warehouse operation the cluster profile should be applied. The **Sequence number** determines the order in which the cluster profiles are applied if you have multiple profiles.
1. On the **General** FastTab, set up your profile options. Tooltips explain the purpose of each field. To see a tooltip, hover your mouse pointer over a field. Learn more about the **Cluster picking strategy** setting in the [Cluster picking strategy](#cluster-picking-strategy) section.
1. On the **Cluster sorting** FastTab, use the toolbar to add and remove sorting criteria for the cluster. The sorting criteria control the order in which the worker performs the work. You can add as many criteria as needed. For each row, make the following settings:
    - **Sequence number** – Enter a number to define the order in which the sorting criteria are processed.
    - **Field name** – Select the field that determines the sorting. For example, if you select the *WMSLocationId* field, the work is sorted by location.
    - **Sorting** – Select one of the following options:
        - *Ascending* – Work is sequenced in ascending order based on the sorting criteria. For example, if you use the *WMSLocationId* field as sorting criteria, and your location IDs are 1, 2, 3, and 4, workers pick from location 4 first.
        - *Descending* – Work is sequenced in descending order based on the sorting criteria. For example, if you use the *WMSLocationId* field as sorting criteria, and your location IDs are 1, 2, 3, and 4, workers pick from location 1 first.

## Item confirmation

When you apply cluster picking, item confirmation is crucial to verify the items that you add to clusters. You can verify items in cluster picking during the cluster picking process. The setup is based on the product bar code setup.

### Set up item verification with cluster picking

To enable workers to verify each item they pick during the cluster picking process, you must turn on product confirmation for the relevant mobile device menu item. Follow these steps to set it up:

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu items**.
1. In the list pane, select the menu item you want to set up.
1. On the Action Pane, select **Work confirmation setup**.
1. Do one of the following actions:
    - If a line exists for the **Work type** you want to set up, select it and then select **Edit** on the Action Pane.
    - If an appropriate line doesn't exist, select **New** on the Action Pane and then set the **Work type** to the appropriate type.
1. Mark the **Product confirm** check box for your new or selected line. This step allows workers to verify each piece of inventory by using the mobile device.

> [!NOTE]
> If you have multiple work records for an item that has **Material picking in license plate locations** set to *Staging*, the Warehouse Management mobile app might show the error message "Current work is frozen" during the cluster picking process. As a workaround, either make sure that you only pick inventory from locations that aren't license plate tracked for the raw material cluster picking process or set **Material picking in license plate locations** to *Order picking* for these items. Learn more in [Release a production order](../production-control/tasks/release-production-order.md).

## Cluster picking strategy

The cluster picking strategy controls whether workers pick inventory for all cluster positions at a location in a single step, or handle each position individually. Set this option as part of the cluster profile.

### Prerequisites

To use the cluster picking strategy feature, you must be running Supply Chain Management version 10.0.48 or later.

### Choose a cluster picking strategy

To set the cluster picking strategy for a selected cluster profile, follow these steps:

1. Go to **Warehouse management \> Setup \> Mobile device \> Cluster profiles**.
1. Select the profile you want to set a strategy for. Set up the profile as described in the [Set up a cluster profile](#set-up-a-cluster-profile) section.
1. On the **General** FastTab, set the **Cluster picking strategy** to one of the following options:
    - *Process by location* – At each pick location, the worker picks the total quantity across all cluster positions in a single step. The system then presents a sort step where the worker distributes the picked quantity to each position. You can fully customize cluster sort criteria. This strategy is the default.
    - *Process by position (tracked items)* – At each pick location, the worker handles each cluster position one at a time, but only for items tracked by batch or serial number that are below the location level. The *Process by location* strategy still applies to non-tracked items at the same location.
    - *Process by position (all items)* – At each pick location, the worker handles every cluster position one at a time, regardless of whether the item has tracking dimensions.

> [!NOTE]
> When you select *Process by position (tracked items)*, the system excludes serial-tracked items where the serial number is captured at *packing* from by-position processing. Because the serial number isn't required until packing rather than picking, those items continue to use the *Process by location* flow.

### How the strategy affects the picking flow

With the default *Process by location* strategy, the picking sequence at a single location looks like this:

1. The worker arrives at the pick location.
1. The mobile device shows the *total* quantity to pick for all cluster positions at that location.
1. The worker picks the consolidated quantity in a single scan.
1. The device presents the sort step. The worker distributes the picked quantity to each cluster position.
1. The worker moves to the next location.

For items without tracking dimensions, this flow is efficient. For batch- or serial-tracked items, however, the sort step requires the worker to assign specific batch or serial numbers to specific positions, which can be complex and error-prone.

With either *Process by position* option, the sort step is eliminated:

1. The worker arrives at the pick location.
1. The device shows the pick screen for the *first* cluster position, displaying only the quantity needed for that position.
1. The worker picks the quantity and confirms.
1. The device advances to the next position at the same location, if applicable.
1. Steps 3 and 4 repeat until all positions at the location are complete.
1. The worker moves to the next location.

Because each pick step is already tied to a specific position, batch and serial numbers are captured per position at the moment of picking. No post-pick distribution is needed.

### Cluster picking strategy example

Consider a cluster with two positions picking a serial-tracked item:

- **Position 1** — Sales order 1, requires 1 unit
- **Position 2** — Sales order 2, requires 2 units

When you use the *Process by location* strategy, work proceeds as follows:

| Step | Screen prompt | Worker action |
|---|---|---|
| 1 | Pick 3 units from location A-01-01 | Scans item and license plate |
| 2 | Sort: assign quantity to Position 1 | Enters 1, confirms 1 unit |
| 3 | Sort: assign quantity to Position 2 | Enters 2, confirms 2 units |
| 4 | Put cluster to staging | Confirms location |

When you use either *Process by position* strategy (tracked items or all items), work proceeds as follows:

| Step | Screen prompt | Worker action |
|---|---|---|
| 1 | Position 1 – Pick 1 unit from location A-01-01 | Scans item and serial number |
| 2 | Confirm Position 1 | Confirms position |
| 3 | Position 2 – Pick 2 units from location A-01-01 | Scans item and serial numbers |
| 4 | Confirm Position 2 | Confirms position |
| 5 | Put cluster to staging | Confirms location |

### Effect of strategy on cluster sorting criteria

The cluster sort criteria (configured under **Cluster sorting** on the cluster profile) behave differently depending on the selected strategy.

| Strategy | Sort criteria |
|---|---|
| Process by location | Fully customizable |
| Process by position (tracked items) | Auto-set: Location \> Item number \> Work ID \> Line number (all ascending) |
| Process by position (all items) | Auto-set: Location \> Item number \> Work ID \> Line number (all ascending) |

> [!IMPORTANT]
> When you save a cluster profile with *Process by position (tracked items)* or *Process by position (all items)* selected, the system automatically deletes any existing sort criteria and creates the following four default sort fields:
>
> 1. Location (ascending)
> 2. Item number (ascending)
> 3. Work ID (ascending)
> 4. Line number (ascending)
>
> You can manually edit these sort criteria after they're created. However, changing the sort order can lead to a suboptimal picking route. For example, if the sort criteria no longer group work by location first, the system might direct the worker to pick one position at a location, then travel to a different location for another position, and then return to the original location to pick the remaining position there. This change results in unnecessary travel between locations.
>
> If you switch back to *Process by location* after previously using a *Process by position* strategy, the auto-created sort criteria remain in place. You can then edit or remove them as needed.
