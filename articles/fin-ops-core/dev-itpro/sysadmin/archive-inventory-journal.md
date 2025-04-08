---
title: Archive Dynamics 365 Supply Chain Management Inventory journal data
description: Learn about how to archive Dynamics 365 Supply Chain Management Inventory journal data, including prerequisites and an overview on setting up archival jobs.
author: epodkolz
ms.author: epodkolzina
ms.topic: conceptual
ms.date: 4/10/2024
ms.custom:
ms.reviewer: twheeloc
---
# Archive Dynamics 365 Supply Chain Management Inventory journal data

This article explains how to archive Dynamics 365 Supply Chain Management Inventory journal data.

## Prerequisites

Before you archive inventory journal data, the following prerequisites must be met:

- The ledger period of the inventory journal that has to be archived must be closed.
- The period must be at least one year before the "from" period date of the archive.

## Turn on the feature in Dynamics 365 Supply Chain Management

1. In finance and operations apps, go to **Feature management**.
1. Select the **Archive with Dataverse long term retention** feature for overall archival service integration. This feature enables all supported finance and operations functional scenarios for archiving through Dataverse long term retention.

The **Archive with Dataverse long term retention** workspace should now be available in the **Workspaces** list in finance and operations apps.

## Set up an archival job

To move inventory journal records to Dataverse long term retention, follow these steps.

1. Go to **Workspaces** \> **Archive with Dataverse long term retention**.
1. Select **Inventory journal**.
1. Select **New long term retention job** to open a wizard where you can schedule a new Inventory Journal archival job with Dataverse long term retention.
1. Enter a name for the job, and then select **Next**.
1. Select the period of the inventory journal that must be purged, and then select **Next**.
1. Enter the start date and time of the job, and then select **Next**.
1. Select **Finish** to schedule the archive job.

You receive a message that the long term retention job has been created.

## View the status of the long term retention job

To view the results of the long term retention job, follow these steps.

1. Go to **Workspaces** \> **Archive with Dataverse long term retention** \> **Inventory journal**.
1. A list of long term retention jobs is shown. Select the job where the **Job status** field is set to **Completed**.
1. Under **Results**, select the link.
1. View the Inventory journal archive progress information.
1. Select **View detailed logs** to view the Archive job message log. This log describes the steps of the long term retention job in detail.

## View historical data from the history table

When inventory journal data is archived by using Dataverse long term retention, the archived data is replicated to a history table in the Dynamics 365 Supply Chain Management database. Users can then view the archived data by using an inquiry page.

To view the historical data, follow these steps.

1. Go to **Workspaces** \> **Archive with Dataverse long term retention** \> **Inventory journal**.
1. A list of long term retention jobs is shown. Select the job where the **Job status** field is set to **Completed**.
1. Select **View historical data** to view the data in the history table.

## Capacity reports

The capacity that's consumed by Inventory journal tables that are archived by using Dataverse long term retention appears under the database storage capacity reports in Platform admin center. The capacity that's consumed by the live and history tables in the finance and operations tables is available in the **Finance** section of the Power Platform admin center capacity reports.
