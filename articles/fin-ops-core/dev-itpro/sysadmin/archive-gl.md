---
title: Archive Dynamics 365 Finance General ledger data
description: Learn about how to archive Microsoft Dynamics 365 Finance General ledger data, including prerequisites and an overview on setting up archival jobs.
author: pnghub
ms.author: twheeloc
ms.topic: how-to
ms.date: 01/14/2026
ms.custom:
ms.reviewer: twheeloc
---
# Archive Dynamics 365 Finance General ledger data

This article explains how to archive Microsoft Dynamics 365 Finance General ledger data.

> [!IMPORTANT]
>
> - You can archive general ledger data only for fiscal years that have the year-end close process completed.
> - You must run the archive jobs for different years in chronological order. For example, you must archive 2020 general ledger data before you archive 2021 general ledger data.

## Prerequisites

Before you archive general ledger transactions, make sure the following prerequisites are met:

- No periods for a fiscal year and the company are open.
- You run year-end close for the fiscal year for the company.
- You archive general ledger transactions for the previous fiscal year for the company.

:::image type="content" source="media/archive-with-dataverse-longterm1.jpg" alt-text="Screenshot of archive with Dataverse long term retention.":::

## Set up an archival job

To set up an archival job, follow these steps:

1. Go to **System administration** \> **Archive with Dataverse long term retention** to open the **Archive with Dataverse long term retention** workspace.
1. Select **General Ledger functional scenario**.
1. Select **Refresh** to populate the General ledger fiscal years and company dataset to archive.

    > [!NOTE]
    > Run the refresh after you close the period and year-end on the General ledger data for the fiscal years and the companies. The **Ready to archive** state must be **Ready** before you can schedule a new long term retention job.

1. Select **New long term retention** to open a wizard that you can use to schedule a new General ledger long term retention job.

:::image type="content" source="./media/new-long-term-retenttion-job2.jpg" alt-text="Screenshot of new long term retention job for General ledger.":::

1. Enter a name for the job, and then select **Next**.

    You can schedule new long term retention jobs for one or more companies at a time. Execution of these jobs is sequential.

:::image type="content" source="./media/long-term-schedule3.jpg" alt-text="Screenshot of schedule new long term retention job for General ledger.":::  

1. On the **Define criteria** page, select the combination of fiscal years and companies to archive General ledger data for.
1. Select **Next**.
1. Select the type of scheduling. Two types are supported:

    - **Single run** – long term retention and saving to history run continuously until both processes are completed. Data is always archived in Dataverse long term retention first. Then the save to history tables occurs.
    - **Daily during allotted time** – The long term retention runs continuously until it's completed. The **Save to history** process runs only during the specified start and stop archiving time.

1. Select **Finish** to schedule the archive job for the selected fiscal years and the companies.
1. Select **View progress** to view the detailed logs.

## View historical data from the history table

To view the historical transactional details, follow these steps.

- Go to **General ledger** \> **Inquiries and reports** \> **Voucher transactions history**.

> [!IMPORTANT]
> The view of archived data shows trial balance data in summary form. However, if you drill into transactional details, a blank window is shown. The data is moved to Dataverse long term storage and the local history copy.

## Capacity reports

The Finance application tables that you move to Dataverse long term retention appear in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) under the database storage capacity reports. The live and history tables are available in the **Finance** section of the Power Platform admin center capacity reports.
