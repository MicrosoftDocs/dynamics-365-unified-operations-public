---
# required metadata

title: Set up cluster picking
description: This topic describes how to set up cluster picking and how to apply item confirmation with cluster picking.
author: Mirzaab
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  WHSClusterProfile, WHSRFAutoConfirm, WHSWorkCluster
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up cluster picking

[!include[banner](../includes/banner.md)]

This topic describes how to enable workers to use their mobile devices to group
picking work into clusters, so that they can pick items from a single location
for multiple work orders at the same time. This is called *cluster picking*.

## About cluster picking

After work orders are released to the warehouse, the worker can use a mobile
device to assign the orders to a cluster. The cluster will organize the picking
work for the worker. When a work order is assigned to a cluster, the worker must
use cluster picking to perform the picking work for the order. The worker cannot
use other picking methods. If a work order is assigned to a cluster by mistake,
the worker must break the cluster and then re-create it.

If needed, a worker can pass a cluster to another worker. This changes the
cluster status to Passed. When the worker uses a mobile device to indicate that
the picking and put away work is completed, the shipment or load must be
confirmed in the client.

## Enable cluster picking

To enable cluster picking, you must set up the following:

- **Cluster profiles** – Specify whether to automatically generate cluster
    IDs, the number of positions to use, when to break clusters, and how to
    sequence and verify the picking work.

- **Work templates** – Define how to create the picking work for cluster
    picking.

- **Location directives** – Specify where to pick items from, and where to put
    them.

- **Mobile device menu items** – Configure a mobile device menu item to use
    existing work that is directed by cluster picking. You must then add the
    menu item to a mobile device menu so that it is displayed on mobile devices.

- **Warehouse management parameters** – Specify the number sequence to use if
    you want to generate identifiers for clusters.

## Set up a cluster profile

To set up a cluster profile, follow these steps:

1. Click **Warehouse management** \> **Setup** \> **Mobile device** \>
    **Cluster profiles**.

1. Click **New** to create a new profile.

1. Click **Create cluster** and, under **Cluster sorting**, click **New** to set up
    the sorting criteria for the cluster. The sorting criteria control the order
    in which the worker will perform the picking work. You can add as many
    criteria as needed.

1. In the **Sequence number** field, enter a number to define the order in
    which the sorting criteria are processed.

1. In the **Field name** field, select the field that will determine the
    sorting. For example, if you select the **WMSLocationId** field, the work will
    be sorted by location.

1. In the **Sorting** field, select one of the following options.

| **Option**     | **Description**                                                                                                                                                                                                                    |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Ascending**  | Picking work is sequenced in ascending order based on the sorting criteria. For example, if you use the **WMSLocationId** field as sorting criteria, and your location IDs are 1, 2, 3, and 4, you will pick from location 4 first. |
| **Descending** | Picking work is sequenced in descending order based on the sorting criteria. For example, if you use the **WMSLocationId** field as sorting criteria, and your location IDs are 1, 2, 3, and 4, you will pick from location 1 first. |

## Item confirmation

When cluster picking is applied, item confirmation is crucial to verify the
items that are added to clusters. You can verify items in cluster picking during
the cluster picking process. The setup is based on the product bar code setup.

### Set up item verification with cluster picking

1. On a mobile device menu item, open the setup form for work confirmation:
    **Warehouse management** \> **Warehouse management** \> **Setup** \>
    **Mobile device** \> **Mobile device menu items**.

1. From the mobile device menu item, open **Work confirmation setup**. The
    **Product confirmation** option allows you to verify each piece of inventory
    from the mobile device when scanned.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]