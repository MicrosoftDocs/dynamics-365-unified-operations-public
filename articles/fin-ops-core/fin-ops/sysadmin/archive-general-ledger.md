---
title: Archive data in Dynamics 365 Finance General ledger (preview)
description: This article explains how to archive data in Dynamics 365 Finance General ledger. 
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# Archive data in Dynamics 365 Finance General ledger (preview)

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

This article explains how to archive data in Dynamics 365 Finance General ledger.  
 
>[!Important]
> General ledger archive can only occur for fiscal years that have run the year-end-close process.
> The archive jobs must be run for different years in chronological order. For example, 2020 General ledger data must be archived before 2021 General ledger data. 

## Prerequisites 

The following prerequisites must be met before archiving general ledger transactions: 
 - All periods for a fiscal year and the company must not be **Open**.
 - Year-end close must be run for the company for the fiscal year.
 - General ledger transactions for the previous fiscal year for the company must be achieved. 

## Set up an archival job 

To set up an archive job, follow these steps:
1. Go to **System administration** > **Archive with Dataverse long term retention** workspace.
2. Select **General Ledger functional scenario**.
3. Click **Refresh** to populate General Ledger fiscal years and company dataset to archive.
4. Run the refresh after performing period and year end close on the general ledger data for fiscal years and the companies. Ready to archive state must be in Ready state to schedule a new long term retention job.
5. Click **New long term retention** to open a wizard to schedule a new general ledger long term job.
6. Enter a job name and click **Next**. 

New long term retention jobs can be scheduled for one or more companies at a time. Execution of these jobs is sequential. 
7. On the **Define criteria** page, select the fiscal years and company combination to archive general ledger data. 
8. Click **Next**. 
 
Two types of scheduling are supported: 
 - **Single run** - Long term retention and saving to history will run continuously until both are completed. Data is always archived in long term retention in Dataverse followed by saving to history tables.
 - **Daily during allotted time** - This option runs the job continuously until completed. The **Save to history** runs only during the start and stop archiving time.

8. Click **Finish** to schedule the archive job for selected fiscal years and the companies. 
9. Archive jobs for selected fiscal years and companies will be scheduled for archiving.
10. Click **View progress** to view the detailed logs.
11. Archived general ledger transactions from a completed archive job can be optionally restored back to live tables from the history tables. When the restore job completes, the retained status is reset in Dataverse managed data lake. To restore data, select a fiscal year and company with job status completed, choose start date and time of job execution and click **Ok**. 

### View historical data from history table 
To view the historical transactional detail, follow these steps:
1. Go to **General Ledger** > **Inquiries and reports** > **Voucher transactions history**. 

>[!Important]
> Trial balance data is in summary for viewing of archived data, but drilling into transactional detail display empty window. The data was moved to Dataverse long term storage and the local history copy. 

### Capacity reports 

The Dynamics 365 Finance application tables moved to Dataverse long term retention will show up under the database storage capacity reports. 

For example, Finance General Ledger data is archived. The administrator sees the General ledger tables in the Dataverse database storage report as tablename **Retained**. These tables provide a logical view of the storage capacity consumed by the Finance table archived in Dataverse long term retention. For example, the mesrp_generaljournalentrybientity-Retained table in a report is an Finance General ledger functional scenario table that has been archived. If the tablename-Retained isn't visible in the report, download the report into excel to view. 


### Finance storage capacity reports 

The live and history tables are available in the Power Platform admin center capacity reports under the **Finance** section. 
>[!Note]
>The history table contains a copy of the archived data in Dataverse long term retention.   

The history tables have less indexes than the live application tables and consumes less capacity than the live application table. Post archival, the auto tuning process could take up to seven days before the reduced capacity is reflected in the history table. 

To understand the capacity reduced savings, compare the table data, for the live, history and tablename-Retained tables, from the reports post an archival policy run. 
>[!Note]
>After archiving, the auto tuning process can take up to seven days before the reduced capacity is reflected in the history table and up to a day before the archived data capacity for tablename-Retained shows up in the Dataverse Ddatabase capacity. 

The live table consumes the highest capacity, followed by the history table and then the tablename-Retained in Dataverse long term retention.  

In production, to get maximum capacity savings, consider purging data from the history tables. 

