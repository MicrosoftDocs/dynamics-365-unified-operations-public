---
title: Set up cluster picking
description: This article describes how to set up cluster picking and how to apply item confirmation with cluster picking.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 12/06/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
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
> If you have multiple work records for an item that has **Material picking in license plate locations** set to *Staging*, then the Warehouse Management mobile app may show the error message "Current work is frozen" during the cluster picking process. As a workaround, either make sure that you only pick inventory from locations that aren't license plate tracked for the raw material cluster picking process or set **Material picking in license plate locations** to *Order picking* for these items. See also [Release a production order](../production-control/tasks/release-production-order.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
