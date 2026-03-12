---
title: Set up cluster picking
description: Learn how to set up cluster picking and how to apply item confirmation with cluster picking, including an outline on enabling cluster picking.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 12/06/2022
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Set up cluster picking

[!include[banner](../includes/banner.md)]

This article describes how to enable workers to use their mobile devices to group picking work into clusters, so that they can pick items from a single location for multiple work orders at the same time. This is called *cluster picking*.

## About cluster picking

After work orders are released to the warehouse, the worker can use a mobile device to assign the orders to a cluster. The cluster will organize the picking work for the worker. When a work order is assigned to a cluster, the worker must use cluster picking to perform the picking work for the order. The worker cannot use other picking methods. If a work order is assigned to a cluster by mistake, the worker must break the cluster and then re-create it.

If needed, a worker can pass a cluster to another worker. This changes the cluster status to Passed. When the worker uses a mobile device to indicate that the picking and put away work is completed, the shipment or load must be confirmed in the client.

## Enable cluster picking

To enable cluster picking, you must set up the following:

- **Cluster profiles** – Specify whether to automatically generate cluster IDs, the number of positions to use, when to break clusters, and how to sequence and verify the picking work.

- **Work templates** – Define how to create the picking work for cluster picking.

- **Location directives** – Specify where to pick items from, and where to put them.

- **Mobile device menu items** – Configure a mobile device menu item to use existing work that is directed by cluster picking. You must then add the menu item to a mobile device menu so that it is displayed on mobile devices.

- **Warehouse management parameters** – Specify the number sequence to use if you want to generate identifiers for clusters.

## Set up a cluster profile

To set up a cluster profile, follow these steps:

1. Go to **Warehouse management \> Setup \> Mobile device \> Cluster profiles**.

1. Select **New** to create a new profile.

1. Select **Create cluster** and, under **Cluster sorting**, select **New** to set up the sorting criteria for the cluster. The sorting criteria control the order in which the worker will perform the picking work. You can add as many criteria as needed.

1. In the **Sequence number** field, enter a number to define the order in which the sorting criteria are processed.

1. In the **Field name** field, select the field that will determine the sorting. For example, if you select the **WMSLocationId** field, the work will be sorted by location.

1. In the **Sorting** field, select one of the following options:

    - *Ascending* – Picking work is sequenced in ascending order based on the sorting criteria. For example, if you use the **WMSLocationId** field as sorting criteria, and your location IDs are 1, 2, 3, and 4, you will pick from location 4 first. |
    - *Descending* – Picking work is sequenced in descending order based on the sorting criteria. For example, if you use the **WMSLocationId** field as sorting criteria, and your location IDs are 1, 2, 3, and 4, you will pick from location 1 first. |

## Item confirmation

When cluster picking is applied, item confirmation is crucial to verify the items that are added to clusters. You can verify items in cluster picking during the cluster picking process. The setup is based on the product bar code setup.

### Set up item verification with cluster picking

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu items**.
1. In the list pane, select the menu item you want to set up.
1. On the Action Pane, select **Work confirmation setup**.
1. Do one of the following action:
    - If there already exists a line for the **Work type** you want to set up, select it and then select **Edit** on the Action Pane.
    - If an appropriate line doesn't exist, select **New** on the Action Pane and then set the **Work type** to the appropriate type.
1. Mark the **Product confirm** check box for your new or selected line. This will allow workers to verify each piece of inventory using the mobile device.

> [!NOTE]
> If you have multiple work records for an item that has **Material picking in license plate locations** set to *Staging*, then the Warehouse Management mobile app may show the error message "Current work is frozen" during the cluster picking process. As a workaround, either make sure that you only pick inventory from locations that aren't license plate tracked for the raw material cluster picking process or set **Material picking in license plate locations** to *Order picking* for these items. Learn more in [Release a production order](../production-control/tasks/release-production-order.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]


## Cluster picking strategy

> [!NOTE]
> The cluster picking strategy feature is available in Dynamics 365 Supply Chain Management version 10.0.48 and later.

The **Cluster picking strategy** field on the cluster profile controls whether workers pick inventory for all cluster positions at a location in a single step, or handle each position individually. You set this field in the cluster profile.

The field offers three options.

| Option | Behavior |
|---|---|
| **Process by location** | Default behavior. At each pick location, the worker picks the total quantity across all cluster positions in a single step. The system then presents a sort step where the worker distributes the picked quantity to each position. Cluster sort criteria are fully customizable. |
| **Process by position (tracked items)** | At each pick location, the worker handles each cluster position one at a time, but only for items tracked by batch or serial number below the location level. Non-tracked items at the same location still use the process-by-location approach. |
| **Process by position (all items)** | At each pick location, the worker handles every cluster position one at a time, regardless of whether the item has tracking dimensions. |

> [!NOTE]
> When you select **Process by position (tracked items)**, serial-tracked items where the serial number is captured at *packing* are excluded from by-position processing. Because the serial number isn't required until packing rather than picking, those items continue to use the process-by-location flow.

### How the strategy affects the picking flow

With the default **Process by location** strategy, the picking sequence at a single location looks like this:

1. The worker arrives at the pick location.
2. The mobile device shows the *total* quantity to pick for all cluster positions at that location.
3. The worker picks the consolidated quantity in a single scan.
4. The device presents the sort step — the worker distributes the picked quantity to each cluster position.
5. The worker moves to the next location.

For items without tracking dimensions, this flow is efficient. For batch- or serial-tracked items, however, the sort step requires the worker to assign specific batch or serial numbers to specific positions, which can be complex and error-prone.

With either **Process by position** option, the sort step is eliminated:

1. The worker arrives at the pick location.
2. The device shows the pick screen for the *first* cluster position, displaying only the quantity needed for that position.
3. The worker picks the quantity and confirms.
4. The device advances to the next position at the same location, if applicable.
5. Steps 3 and 4 repeat until all positions at the location are complete.
6. The worker moves to the next location.

Because each pick step is already tied to a specific position, batch and serial numbers are captured per position at the moment of picking. No post-pick distribution is needed.

#### Example

Consider a cluster with two positions picking a serial-tracked item:

- **Position 1** — Sales order 1, requires 1 ea
- **Position 2** — Sales order 2, requires 2 ea

**With Process by location:**

| Step | Screen prompt | Worker action |
|---|---|---|
| 1 | Pick 3 ea from location A-01-01 | Scans item and license plate |
| 2 | Sort: assign quantity to Position 1 | Enters 1, confirms 1 ea |
| 3 | Sort: assign quantity to Position 2 | Enters 2, confirms 2 ea |
| 4 | Put cluster to staging | Confirms location |

**With Process by position (tracked items or all items):**

| Step | Screen prompt | Worker action |
|---|---|---|
| 1 | Position 1 – Pick 1 ea from location A-01-01 | Scans item and serial number |
| 2 | Confirm Position 1 | Confirms position |
| 3 | Position 2 – Pick 2 ea from location A-01-01 | Scans item and serial numbers |
| 4 | Confirm Position 2 | Confirms position |
| 5 | Put cluster to staging | Confirms location |

### Effect on cluster sort criteria

The cluster sort criteria (configured under **Cluster sorting** on the cluster profile) behave differently depending on the selected strategy.

| Strategy | Sort criteria |
|---|---|
| Process by location | Fully customizable |
| Process by position (tracked items) | Auto-set: Location → Item number → Work ID → Line number (all ascending) |
| Process by position (all items) | Auto-set: Location → Item number → Work ID → Line number (all ascending) |

> [!IMPORTANT]
> When you save a cluster profile with **Process by position (tracked items)** or **Process by position (all items)** selected, the system automatically deletes any existing sort criteria and creates the following four default sort fields:
>
> 1. Location (ascending)
> 2. Item number (ascending)
> 3. Work ID (ascending)
> 4. Line number (ascending)
>
> You can manually edit these sort criteria after they are created. However, changing the sort order can lead to a suboptimal picking route. For example, if the sort criteria no longer group work by location first, the system may direct the worker to pick one position at a location, then travel to a different location for another position, and then return to the original location to pick the remaining position there — resulting in unnecessary travel between locations.

> [!NOTE]
> If you switch back to **Process by location** after previously using a by-position strategy, the auto-created sort criteria remain in place. You can then edit or remove them as needed.
