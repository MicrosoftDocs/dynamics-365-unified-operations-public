---
title: Archive data in Dynamics 365 Finance General ledger (preview)
description: This article explains how to archive data in Microsoft Dynamics 365 Finance General ledger.
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/13/2024
ms.custom:

---
# Archive data in Dynamics 365 Finance General ledger (preview)

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

This article explains how to archive data in Microsoft Dynamics 365 Finance General ledger.

> [!IMPORTANT]
> - General ledger archiving can occur only for fiscal years that the year-end close process has been run for.
> - The archive jobs for different years must be run in chronological order. For example, 2020 General ledger data must be archived before 2021 General ledger data.

## Prerequisites

The following prerequisites must be met before you archive General ledger transactions:

- No periods for a fiscal year and the company can be open.
- Year-end close must be run for the fiscal year for the company.
- General ledger transactions for the previous fiscal year for the company must be archived.

## Set up an archival job

To set up an archival job, follow these steps.

1. Go to **System administration** \> **Archive with Dataverse long term retention** to open the **Archive with Dataverse long term retention** workspace.
1. Select **General Ledger functional scenario**.
1. Select **Refresh** to populate the General ledger fiscal years and company dataset to archive.

    > [!NOTE]
    > Run the refresh after you do period and year-end close on the General ledger data for the fiscal years and the companies. The **Ready to archive** state must be **Ready** before you can schedule a new long-term retention job.

1. Select **New long term retention** to open a wizard that you can use to schedule a new General ledger long-term retention job.
1. Enter a name for the job, and then select **Next**.

    New long-term retention jobs can be scheduled for one or more companies at a time. Execution of these jobs is sequential.

1. On the **Define criteria** page, select the combination of fiscal years and companies to archive General ledger data for.
1. Select **Next**.
1. Select the type of scheduling. Two types are supported:

    - **Single run** – Long-term retention and saving to history run continuously until both processes are completed. Data is always archived in Dataverse long-term retention first. Then the save to history tables occurs.
    - **Daily during allotted time** – The long-term retention runs continuously until it's completed. The **Save to history** process runs only during the specified start and stop archiving time.

1. Select **Finish** to schedule the archive job for the selected fiscal years and the companies.
1. Select **View progress** to view the detailed logs.
1. Optional: Archived General ledger transactions from a completed archive job can be restored back to live tables from the history tables. When the restore job is completed, the retained status is reset in the Dataverse-managed Azure data lake. To restore data, select a fiscal year and company that have a job status of **Completed**, select a start date and time for job execution, and then select **OK**.

## View historical data from the history table

To view the historical transactional details, follow this step.

- Go to **General ledger** \> **Inquiries and reports** \> **Voucher transactions history**.

> [!IMPORTANT]
> The view of archived data shows trial balance data in summary form. However, if you drill into transactional details, a blank window is shown. The data was moved to Dataverse long-term storage and the local history copy.

## Capacity reports

The Finance application tables that are moved to Dataverse long-term retention appear under the database storage capacity reports.

For example, Finance General ledger data is archived. When the administrator views the **Dataverse database storage** report, the General ledger tables are shown as **\<*tablename*\>-Retained**. These tables provide a logical view of the storage capacity that's consumed by the Finance table that's archived in Dataverse long-term retention. For example, the mesrp\_generaljournalentrybientity-Retained table on a report is a Finance General ledger functional scenario table that has been archived. If the \<*tablename*\>-Retained table isn't visible on the report, download the report to Excel for viewing.

### Finance storage capacity reports

The live and history tables are available in the **Finance** section of the Power Platform admin center capacity reports.

> [!NOTE]
> The history table contains a copy of the archived data in Dataverse long-term retention.

The history tables have fewer indexes and consume less capacity than the live application tables.

To understand the capacity reduced savings, compare the table data for the live, history, and \<*tablename*\>-Retained tables from the reports after an archival policy run.

> [!NOTE]
> After archiving, the automatic tuning process can take up to seven days before the reduced capacity is reflected in the history table. It can take up to a day before the archived data capacity for \<*tablename*\>-Retained tables is reflected in the Dataverse database capacity.

The live table consumes the highest capacity, followed by the history table, and then the \<*tablename*\>-Retained table in Dataverse long-term retention.

To get maximum capacity savings in production, consider purging data from the history tables.
