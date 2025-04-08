---
title: Archive Dynamics 365 Supply Chain Management inventory-related documents
description: Learn how to archive Microsoft Dynamics 365 Supply Chain Management inventory-related documents.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 9/06/2024
ms.custom:
ms.reviewer: twheeloc
---
# Archive Dynamics 365 Supply Chain Management inventory-related documents

This article explains how to archive Microsoft Dynamics 365 Supply Chain Management inventory-related documents.

For the removed inventory transactions, a scheduled job moves the corresponding inventory transactions originator from the `InventTransOrigin` table to the `InventTransOriginHistory` table.

## Prerequisites

Before you can use this feature, you must enable it for your system.

### Turn on the feature in Dynamics 365 Supply Chain Management

To enable the archive feature in Feature management, follow these steps.

1. In Dynamics 365 finance and operations apps, go to **Feature management**.
2. Select the **Archive with Dataverse long term retention** feature for overall archival service integration. This feature enables all supported finance and operations functional scenarios for archiving through Dataverse long term retention.

The **Archive with Dataverse long term retention** workspace should now be available in the **Workspaces** list in finance and operations apps.

## Set up an archival job

To move inventory journal records to Dataverse long term retention, follow these steps.

1. Go to **Workspaces** \> **Archive with Dataverse long term retention**.
2. Select **Inventory transactions originator**.
3. Select **New long term retention job** to open a wizard that you can use to schedule a new inventory transactions originator archival job with Dataverse long term retention.
4. Enter a name for the job, and then select **Next**.
5. Select the legal entity of the inventory transactions originator that must be purged, and then select **Next**.
6. Enter the start date and time of the job, and then select **Next**.
7. Select **Finish** to schedule the archive job.

    You receive a message that the long term retention job was created.

## View the status of the long term retention job

To view the results of the long term retention job, follow these steps.

1. Go to **Workspaces** \> **Archive with Dataverse long term retention**.
2. Select **Inventory transactions originator**.
3. In the list of long term retention jobs, select the job where the **Job status** field is set to **Completed**.
4. Under **Results**, select the link.

## View historical data from the history table

When an inventory transactions originator is archived by using Dataverse long term retention, the archived data is replicated to a history table in the Dynamics 365 Supply Chain Management database. Users can view the archived data by using an inquiry page.

To view the historical data, follow these steps.

1. Go to **Workspaces** \> **Archive with Dataverse long term retention**.
2. Select **Inventory transactions originator**.
3. In the list of long term retention jobs, select the job where the **Job status** field is set to **Completed**.
4. Select **View historical data** to view the data in the history table.

## Capacity reports

The capacity that is consumed by inventory transactions originator tables that are archived by using Dataverse long term retention appears under the database storage capacity reports in Power Platform admin center. The capacity that is consumed by the live and history tables in the finance and operations tables is available in the **Finance** section of the capacity reports in Power Platform admin center.
