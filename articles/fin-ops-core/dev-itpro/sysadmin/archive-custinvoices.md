---
title: Archive Dynamics 365 Finance customer invoice data
description: Learn how to archive customer invoice data by using Microsoft Dataverse long term retention.
author: JodiChristiansen
ms.date: 03/13/2026
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: jchrist
ms.search.validFrom: 2024-12-05
ms.dyn365.ops.version: 10.0.24
---

# Archive Dynamics 365 Finance customer invoice data

[!INCLUDE[banner](../includes/banner.md)]

This article explains how to archive Microsoft Dynamics 365 Finance customer invoice data.

> [!IMPORTANT]
> You can archive customer invoice data only for fiscal periods that are on hold or closed.

## Prerequisites

Before you can archive customer invoice transactions, make sure the following prerequisites are met:

- In Feature management, enable the **(Preview) Archive Customer invoice with long term retention** and **Archive with Dataverse long term retention** features. To learn more about how to set up the archive feature, see [Set up and manage archive data in finance and operations apps](archive-setup-manage.md).
- The fiscal period must have a status of **On hold** or **Permanently closed** for the date range that you use in the archive job.

## Set up an archival job

To set up an archival job, follow these steps:

1. Go to **System administration** > **Workspaces** > **Archive with Dataverse long term retention**.
1. In the **Archive with Dataverse long term retention** workspace, select **Customer invoice**.
1. Select **New long term retention** to open a wizard that you can use to schedule a new **Customer invoice long term retention** job.
1. Enter a name for the job, and then select **Next**. You can schedule each new long term retention job for sales order invoices, free text invoices, or both.
1. On the **Define criteria** page, select to archive sales order invoices, free text invoices, or both.
1. Use the **From date** and **To date** fields to define a date range. The fiscal periods must have a status of **On hold** or **Permanently closed** for that date range.
1. Select one or more legal entities. The system creates one job for each legal entity and each invoice type that you select.
1. Select **Next**.
1. Select the type of scheduling. Two types are supported:

    - **Single run** – The long term retention and **Save to history** processes run continuously until both are completed. The system always archives data in Dataverse long term retention first. Then the save to history tables occurs.
    - **Daily during allotted time** – The long term retention runs continuously until it's completed. The **Save to history** process runs during the specified start and stop archiving time.

1. Select **Finish** to schedule the archive job for the selected invoice types and legal entities.
1. Select the link in the **Results** column to view the progress or detailed logs.

## View historical data from the history table

To view the historical transactional details, select an archive job, and then select **View history data**. The **Archived invoices** page shows the invoices and lines.

## Capacity reports

The Finance application tables that are moved to Dataverse long term retention appear in the Power Platform admin center, under the database storage capacity reports. You can view the live and history tables in the **Finance** section of the Power Platform admin center capacity reports.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
