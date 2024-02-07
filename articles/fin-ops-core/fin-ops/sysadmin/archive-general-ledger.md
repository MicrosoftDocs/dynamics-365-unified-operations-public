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

 
Important:  

General ledger archive can only occur for fiscal years that have run the year-end-close process 

The archival jobs must be run for different years in chronological order. For example, GL 2020 data is required to be archived prior to GL 2021data 

 Setting up an archival job  

Prerequisites 

The following rules apply to archive general ledger transactions: 

All periods for a fiscal year and company must not be in Open state. 

Year end close must be run for the company for the fiscal year. 

General ledger transactions for the previous fiscal year for the company must be achieved. 


Explain the steps involved.  

Go to System administration -> Archive with Dataverse long term retention workspace and select General Ledger functional scenario. 

Click on the Refresh button to populate General Ledger fiscal years and company dataset to archive. 

Run refresh after performing period and year end close on the general ledger data for fiscal years and the companies. Ready to archive state must be in Ready state to schedule a new long term retention job. 

Click on New long term retention button to open UI wizard to schedule a new general ledger long term job. Enter job name and click on Next button. 

New long term retention jobs can be scheduled for one or more companies at a time. However, execution of these jobs is sequential. On the define criteria page, select the fiscal years and company combination that you want to archive general ledger data and click next. 
 
There are two types of scheduling that are supported: 

Single Run: long term retention and saving to history will run continuously until both are completed. Data is always archived in long term retention in Dataverse followed by save to history tables. 
Daily during allotted time: In this scheduling option long term retention will run continuously until completed. The Save to History runs only during the start and stop archiving time. 


Confirm the details on the last step of the UI wizard and click Finish to schedule the GL archive job for selected fiscal years and the companies. 

 Archive jobs for selected fiscal years and companies will be scheduled for archiving. 

 Click on View progress for the job to see the detailed logs. 

 Archived general ledger transactions from a completed archive job can be optionally restored back to live tables from the history tables. On completion of restore job, the retained status is reset in Dataverse managed data lake. To restore, select a fiscal year and company with job status completed, choose start date and time of job execution and click Ok. 

View historical data from history table 
To view the historical transactional detail, select the menu item General Ledger – Inquiries and reports – voucher transactions history. 

Important: Trial balance data will remain in summary form for viewing of archived data, but drilling into transactional detail will show an empty inquiry – as the data has moved to Dataverse long term storage and the local history copy. 

View the archived data in Dataverse managed data lake  

Below is a sample view of a SQL query with  Fabric and Dataverse managed data lake  to view the archived data. More details. 

Capacity reports 

The Dynamics 365 Finance and Operations live application tables moved to Dataverse long term retention will show up under the DB storage capacity reports. 

Assume a scenario where Finance General Ledger data is archived. The admin will see the GL tables in the Dataverse DB storage report as  <tablename-Retained>.  These tables provide a logical view of the storage capacity consumed by the FnO table archived in DV long term retention. For example, the mesrp_generaljournalentrybientity-Retained table in the below report is an Finance GL functional scenario table that has been archived. If the <tablename-Retained> is not visible in the report, download the report into excel to view the same. 


Finance and Operations storage capacity reports 

The live and history tables are available in the Power Platform admin center capacity reports under the Finance and Operations section. Note that the history table contains a copy of the archived data in Dataverse long term retention.  
  

The history tables have very few indexes than the live application tables and consumes less capacity than the live application table. Post archival, the auto tuning process could take up to 7 days before the reduced capacity is reflected in the history table. 

To understand the capacity reduced savings, compare the table data, for the live, history and <tablename-Retained> tables, from the reports post an archival policy run. Note that post archival, the auto tuning process could take up to 7 days before the reduced capacity is reflected in the history table and up to a day before the archived data capacity for <tablename-Retained shows up in the Dataverse DB capacity. 

The live table will consume the highest capacity, followed by the history table and then the <tablename-Retained> in Dataverse long term retention.  

In production, to get maximum capacity savings, you should consider purging the data from the history tables. 

Inventory Transactions  

(separate section in public docs) 

This article explains how to create a data archival job for a Supply Chain Inventory Transaction 

 

Archive inventory transactions - Supply Chain Management | Dynamics 365 | Microsoft Learn consolidates and compress the inventory transactions table (InventTrans) and archives the original records into InventTransArchive table. This feature remissions the data volume issue of table InventTrans and improve the system performance. 

New feature Archive with Dataverse long term retention is released to move the records of InventTransArchive to data lake and replicate corresponding records to InventTransArchiveHistory in Dynamics 365 Supply Chain Management for performance optimization. 

 

Prerequisites 

Inventory transactions archive feature has been turned on. 

Inventory transactions have been archived from InventTrans table to InventTransArchive table. 

Install solution in your Power platform 

Refer to Setup and Management  

Hold -> D365 Finance and Operations - Archival with DV LTR.docx (sharepoint.com) 

Turn on the features in your Dynamics 365 Supply Chain Management 

If your system doesn't already include the features that is described in this article, go to Feature management, and turn on the Inventory transactions archive and Archive with Dataverse long term rentention feature.  

Inventory transactions archive  

Archive inventory transaction from InventTrans to InventTransArchive. (https://learn.microsoft.com/en-us/dynamics365/supply-chain/inventory/archive-inventory-transactions) 
