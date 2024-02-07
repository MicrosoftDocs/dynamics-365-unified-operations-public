---
title: Finance and Operations – archival with Dataverse long term data retention 
description: This article describes how Finance and Operations – archival with Dataverse long term data retention. 
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---

Overview (preview)  

(separate page under <Archive Historic records>) 

[This topic is pre-release documentation and is subject to change.] 

Dynamics 365 Finance and Operations apps supports the ability custom retention policies to securely archive and retain unlimited data long term in a cost-efficient way. While Finance and Operations can support your business growth with no limit on active data, you might want to consider moving historical inactive data, required for compliance and regulatory reasons, to Dataverse long term retention. 

Important 

This is a preview feature. 

Preview features aren’t meant for production use and may have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback. 

Be a licensed Dynamics 365 Finance and Operations customer. 

While this feature has no limit on the total records, that can be archived, the largest table that can be archived is limited to a maximum 100M records. As the limitation is being worked on, it is recommended to trim any table with greater than 100M records. 

Business application data lifecycle 

Consider the business application data lifecycle in three stages. First active data, which over time transitions to historic inactive data required for compliance and regulatory reasons, and finally transitions to deleted data. 

Dynamics 365 Finance and Operations applications allows organizations to get immediate and ongoing benefits with archival. 

Securely retain the historical inactive application data long term for audit, legal, and regulatory requirements. 

Reduce the application database size and the capacity consumed to potentially improve application performance associated with very large tables. 

 

Types of Dynamics 365 Finance and Operations data that can be archived with Dataverse long term retention 

The preview supports Finance General ledger, Supply Chain Inventory Transactions, Supply Chain Sales Order. Finance Tax transactions, Retail transactions and Finance Journals are planned over next few months. Other scenarios will be considered based on customer feedback. 

How does Finance and Operations archival work 

Application admins can schedule archival jobs with a criteria, for a supported functional scenario. The data from the tables in archival scope for the functional scenario will be archived in Dataverse long term retention, within a Dataverse managed data lake. 

 

When an archival job is initiated from the Finance and Operations archival workspace, it entails multiple stages -  

The very first time, the data from all the live application tables in the archival scope for the functional scenario being archived is replicated into a Dataverse managed data lake.  

The data that meets the archival criteria is marked as ready for archival in the live Finance and Operations application tables. 

These live table records will then be marked as retained(archived) in Dataverse long term retention. 

A reconciliation process verifies that all the live application table records previously marked as ready for archival is available in Dataverse long term retention. 

The live application data previously marked as ready for archival is then also moved to the history tables, within the Finance and Operations database, and deleted from the live application tables. Application specific inquiry forms allow access to this history table data from the live application. Data from history tables can be (1)restored back to live table and (2) purged permanently. This is not yet available in preview. 

 

Note – During archival, no data is archived from tables outside the functional scenario, even if they are related. For example, when Inventory Transaction tables are archived, the Sales tables are not archived automatically. 

 

 

 

 

Customization 

The archival framework supports customization to include custom fields, custom tables in supported functional scenarios, and enabling customers to build their own archival scenario for custom tables. Customers will be required to leverage this capability to ensure table customizations are configured prior to initiating an archival job. 

 

Important 

The long-term retained data is Read-only. 

X++ delete action is not honored when data archival policy is run to move data out of the live AX DB. 

FnO attachments are not currently supported. 

The archival process for a scenario with Dataverse long term retention entails multiple stages that run sequentially in the background and the process can take up to 14 days to complete .  

Data from history tables can be restored back to live tables. (add link to restore page) When data is restored back from history tables to live tables, the corresponding archived data in Dataverse long term retention will also go through a status change from inactive to active, as the data is no longer considered to be archived.  

While data from the history table can be restored back to the live table, the inactive data retained with Dataverse long term retention cannot be moved back to the live application database.  

(Restore history to live functionality not avail on initial release)  

The archived data in Dataverse long term retention cannot be moved back to the live application table. 

The archived data in Dataverse long term retention is always secured with Dataverse security backed by Microsoft Entra ID. 

Customers using self-managed encryption key (BYOK) in Dataverse should be aware that long term retained data in the Azure data lake is encrypted with Microsoft managed key. Consider migrating to customer managed key. More information: Migrate bring-your-own-key environments to customer-managed key. 

 

 

 

Understanding Dataverse storage costs for archived AX DB data  

Every GB moved from AX database to Dataverse long term retention (Dataverse managed data lake), will consume, on average, 50% less database capacity. This is because the live application data is compressed in Dataverse long term retention.  

 

This saving is passed onto the customer. The amount of compression depends on the kind of data. With some data you might notice larger than 50% savings while in others you might notice lower than 50%. It is indeterministic. You might also notice that savings are more evident when higher volumes of data (hundreds of GB) are retained.  

 

Note that the archived data is also made available in the history tables. It allows access via Finance and Operations application inquiry form. History tables do not contain indexes and will consume less capacity than the live tables - (10% to 30% less depending on the table and indexes. When in-app access to archived data is not required, delete the data permanently from the History tables to get full savings. 

 

Storage capacity reports 

The admin role can view the storage size in the existing Power Platform admin center reports for Finance and Operations tables as well as Dataverse long term retention. 

Viewing the storage consumed by the archived data in Dataverse long term retention  

In the Power Platform admin center reports for Dataverse, the admin will see the archived FnO tables with a prefix <-Retained> in the Dataverse DB storage report. These tables provide a logical view of the storage capacity consumed by the FnO table archived in DV long term retention.  

Viewing the storage consumed by the Finance and Operations data 

In the Power Platform admin center reports for Finance and Operations, select Capacity and then Finance and Operations. The admin can view details of the FnO live application tables as well as the history tables. The history tables with no indexes consume lesser capacity than the live application table.  

 

Refer to Finance General Ledger documentation for  examples. 
