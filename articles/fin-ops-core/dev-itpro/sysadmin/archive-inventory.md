---
title: Archive Dynamics 365 Supply Chain Management Inventory transactions data
description: Learn about how to archive Microsoft Dynamics 365 Supply Chain Management Inventory transactions data, including prerequisites.
author: pnghub
ms.author: gned, amiyaaloke
ms.topic: conceptual
ms.date: 4/10/2024
ms.custom:
ms.reviewer: twheeloc
---
# Archive Dynamics 365 Supply Chain Management Inventory transactions data

This article explains how to archive Dynamics 365 Supply Chain Management Inventory transactions.

The *Archive with Dataverse long term retention* feature optimizes storage and system performance by moving `InventTransArchive` records to a Microsoft Azure data lake and replicating corresponding records to the `InventTransArchiveHistory` table. Records in the `InventTransArchive` table represent inventory transactions that have already been consolidated (see also [Consolidate inventory transactions](../../../supply-chain/inventory/archive-inventory-transactions.md)).

## Prerequisites

Before you can  use this feature, you must enable it for your system and consolidate the transactions that you want to archive, as described in the following subsections.

### Turn on the features in Supply Chain Management

If your system doesn't already include the features described in this article, go to the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace and turn on both the following features:

- *Inventory transaction consolidation* – This feature consolidates inventory transactions by moving them from the `InventTrans` table to the `InventTransArchive` table.
- *Archive with Dataverse long term retention* – This feature moves archived inventory transactions from the `InventTransArchive` table to  Dataverse long term retention and replicates the data to the `InventTransArchiveHistory` table.

### Considerations before you purge inventory transactions

- The **Reverse** function of the *Inventory transaction consolidation* feature isn't available for purged inventory transaction records.
- The unpurge activity isn't available from the Dataverse long term retention to Supply Chain Management.

### Consolidate inventory transactions before you purge

The purge operation can only move consolidated transaction records. Follow the instructions provided in [Consolidate inventory transactions](../../../supply-chain/inventory/archive-inventory-transactions.md) before you proceed with the purge operation.

## Set up an archival job

To move `InventTransArchive` records to the Dataverse long term retention, follow these steps.

1. Go to **Workspaces** \> **Archive with Dataverse long term retention** \> **Inventory transactions**.
1. Select **New long term retention job** to open the **Long term retention job creation** wizard.
1. Enter a name for the job, and then select **Next**.
1. Select the period that was processed by the *Inventory transaction consolidation* feature, and then select **Next**.
1. Enter the start date and time of the long term retention job, and then select **Next**.
1. Review the job details, and create the long term retention job.

You receive a message that the long term retention job has been created. The archived records are purged on the scheduled date.

## View the status of the long term retention job

To view the results of the long term retention job, follow these steps.

1. Go to **Workspaces** \> **Archive** \> **Inventory transactions**.
1. A list of long  term retention jobs is shown. Select the job where the **Job status** field is set to **Completed**.
1. Under **Results**, select the link.
1. View the **Inventory transactions archive progress** information.
1. Select **View detailed logs** to view the Archive job message log. This log describes the steps of the long term retention job in detail.

## View historical data

When the long term retention job moves archived inventory transactions from the `InventTransArchive` table to the Dataverse long term retention, the same data is replicated to the `InventTransArchiveHistory` table. To view the historical data in the `InventTransArchiveHistory` table, follow these steps.

1. Go to **Workspaces** \> **Archive** \> **Inventory transactions**.
1. A list of long term retention jobs is shown. Select the job where the **Job status** field is set to **Completed**.
1. Select **View historical data** to view the data in the `InventTransArchiveHistory` table.
