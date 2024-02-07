---
title: create a data archival job for a Finance General Ledger scenario
description: This article explains how to create a data archival job for a Finance General Ledger scenario. 
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# create a data archival job for a Finance General Ledger scenario

A screenshot of a computer

Description automatically generated 

 

Confirm the details on the last step of the UI wizard and click Finish to schedule the GL archive job for selected fiscal years and the companies. 

A screenshot of a computer

Description automatically generated 

Archive jobs for selected fiscal years and companies will be scheduled for archiving. 

A screenshot of a computer

Description automatically generated 

Click on View progress for the job to see the detailed logs. 

A screenshot of a computer

Description automatically generated 

Archived general ledger transactions from a completed archive job can be optionally restored back to live tables from the history tables. On completion of restore job, the retained status is reset in Dataverse managed data lake. To restore, select a fiscal year and company with job status completed, choose start date and time of job execution and click Ok. 

A screenshot of a computer

Description automatically generated  

 

View historical data from history table 

 

To view the historical transactional detail, select the menu item General Ledger – Inquiries and reports – voucher transactions history. 

A screenshot of a computer

Description automatically generated 

 

 

Important: Trial balance data will remain in summary form for viewing of archived data, but drilling into transactional detail will show an empty inquiry – as the data has moved to Dataverse long term storage and the local history copy. 

 

 

View the archived data in Dataverse managed data lake  

Below is a sample view of a SQL query with  Fabric and Dataverse managed data lake  to view the archived data. More details. 

A screenshot of a computer

Description automatically generated 

Capacity reports 

The Dynamics 365 Finance and Operations live application tables moved to Dataverse long term retention will show up under the DB storage capacity reports. 

 

Assume a scenario where Finance General Ledger data is archived. The admin will see the GL tables in the Dataverse DB storage report as  <tablename-Retained>.  These tables provide a logical view of the storage capacity consumed by the FnO table archived in DV long term retention. For example, the mesrp_generaljournalentrybientity-Retained table in the below report is an Finance GL functional scenario table that has been archived. If the <tablename-Retained> is not visible in the report, download the report into excel to view the same. 

 

A screenshot of a computer

Description automatically generated 

 

 

Finance and Operations storage capacity reports 

The live and history tables are available in the Power Platform admin center capacity reports under the Finance and Operations section. Note that the history table contains a copy of the archived data in Dataverse long term retention.  

 

A screenshot of a computer

Description automatically generated 

  

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
