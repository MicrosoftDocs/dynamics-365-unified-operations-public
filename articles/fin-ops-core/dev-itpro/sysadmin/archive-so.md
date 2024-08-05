---
title: Archive Dynamics 365 Supply Chain Management Sales orders data
description: Learn about how to archive Dynamics 365 Supply Chain Management Sales orders data, including prerequisites and an overview of installing solutions in Power Platform.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 4/09/2024
ms.custom:
ms.reviewer: twheeloc
---

# Archive Dynamics 365 Supply Chain Management Sales orders data

This article explains how to archive Dynamics 365 Supply Chain Management Sales orders data.

## Prerequisites

The following prerequisites must be met before sales orders can be archived:

- The sales orders are fully invoiced.
- The sales orders shouldn't be part of an intercompany order chain.

## Install the solution in Microsoft Power Platform

For information about how to install the solution in Microsoft Power Platform, see [Set up and management](archive-setup-manage.md).

## Turn on the feature in Dynamics 365 Supply Chain Management

The **Archive with Dataverse long term retention** feature should be enabled.

## Set up an archival job

To schedule the long-term retention job, follow these steps.

1. In Dynamics 365 Supply Chain Management, go to **System administration** \> **Archive with Dataverse long term retention workspace**.
1. Select **Sales orders scenario**.
1. Select **New long term retention** to open a wizard that you can use to schedule a new sales order archival job with Dataverse long-term retention.
1. Enter a name for the job, and then select **Next**.
1. Select the date of the oldest sales orders to archive ("from" date). Select the date of the newest sales orders to archive ("to" date).
1. Select the legal entity (company) to archive the sales orders for.
1. Select **Next**.
1. Select the type of scheduling. Two types are supported:

    - **Single run** – Long-term retention and saving to history run continuously until both processes are completed. Data is always archived in Dataverse long-term retention first. Then the save to history tables occurs.
    - **Daily during allotted time** – The long-term retention runs continuously until it's completed. The **Save to history** process runs only during the specified start and stop archiving time.

1. On the last page of the wizard, confirm the details, and then select **Finish** to schedule the **Sales orders archive with Dataverse long term retention** job for the selected interval and company.

The archive jobs appear on the dashboard.

## View the status of the long term retention job

Select **View progress** on the archival job dashboard to view job status details.

## View historical data

The **Archive with Dataverse long term retention** workspace shows the full archiving history. Each row in the grid shows information such as the date when the archive was created, the user who created it, and its status.

To view details about a selected archive, follow these steps.

1. Select the job, and then select **View history data** on the toolbar.
1. The **Archived sales orders** page shows every sales order that's included in the archive job. To view an order, including its header and all its order lines, select it in the grid.
1. On the Action Pane, select **Archived sales order details**. From the order details, you can view more related information about the order.
1. Select **Inquiry**.
1. On the menu, select the type of records to view.
