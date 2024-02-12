---
title: Archive data in Dynamics 365 finance and operations with Dataverse (preview) 
description: This article describes how to archive data in Dynamics 365 finance and operations. 
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---

# Overview (preview)  

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

This article describes how to archive data in Dynamics 365 finance and operations. Dynamics 365 finance and operations supports custom retention policies to securely archive and retain unlimited data long term in a cost-efficient way. While Dynamics 365 finance and operations supports your business growth with no limit on active data, you might want to consider moving historical inactive data, required for compliance and regulatory reasons, to Dataverse long term retention. 

>[!NOTE]
> This feature doesn't limit the total records that can be archived, however, the largest table that can be archived is limited to a maximum 100M records. It's recommended to trim any table with greater than 100M records. 

## Business application data lifecycle 

The business application data lifecycle has three stages: 
 - First - active data
 - Second - transitions to historic inactive data required for compliance and regulatory reasons
 - Third - transitions to deleted data. 

Dynamics 365 finance and operations applications allows organizations to receive the following benefits with archiving:
 - Secures historical inactive application data long term for audit, legal, and regulatory requirements.
 - Reduces the application database size and the capacity consumed to potentially improve application performance associated with very large tables. 

## Dynamics 365 finance and operations data types that can be archived with Dataverse longterm retention  

This feature currently supports:
 - Dynamics 365 Finance General ledger
 - Dynamics 365 Supply Chain inventory transactions
 - Dynamics 365 Supply Chain sales order

Additional data types are planned for future releases.  

### How does archiving Dymamics 365 finance and operations data work 

Application administrators can schedule archiving jobs with criteria for supported functional scenarios. The data from the tables for the functional scenario are archived in Dataverse long term retention, within a Dataverse managed data lake. 

When an archive job is initiated from the Dynamics 365 finance and operations archival workspace, it contains multiple stages:
1. Data from the live application tables in the functional scenario being archived is replicated into a Dataverse managed data lake.
2. Data that meets the archival criteria is marked as ready for archival in the live Dynamics 365 finance and operations application tables.
3. The live table records will be marked as retained(archived) in Dataverse long term retention.
4. A reconciliation process verifies that all the live application table records previously marked as ready for archival are available in Dataverse long term retention.
5. Live application data previously marked as archiving is moved to history tables in the Dynamics 365 finance and operations database, and are deleted from the live application tables. Application specific inquiry pages access this history table data from the live application. Data from history tables can be either restored back to live table or purged permanently. This functionality is planned for a future release.  

>[!Note]
>During archiving, no data is archived from tables outside the functional scenario, even if they are related. For example, when inventory transaction tables are archived, the Sales tables aren't archived automatically. 

### Customization 

The archiving framework includes custom fields and custom tables in supported functional scenarios. This enables customers to build their own archival scenario for custom tables. Customers need to configure the table customizations prior to initiating an archival job. 

 
Important 
 - The long-term retained data is Read-only.
 - X++ delete action isn't honored when data archival policy is run to move data out of the live Dynamics 365 finance and operations database.
 - Dynamics 365 finance and operations attachments aren't currently supported.
 - The archive process for scenarios with Dataverse long term retention entails multiple stages that run sequentially in the background and the process can take up to 14 days to complete.
 - The archived data in Dataverse long term retention can't be moved back to the live application table.
 - The archived data in Dataverse long term retention is secured with Dataverse security backed by Microsoft Entra ID.
 - Customers using self-managed encryption key (BYOK) in Dataverse should be aware that long term retained data in the Azure data lake is encrypted with Microsoft managed key. Customer should consider migrating to customer managed key. For more information, see [Migrate bring-your-own-key environments to customer-managed key](/power-platform/admin/cmk-migrate-from-byok). 

 
### Understanding Dataverse storage costs for archived data  

Every GB moved from the database to Dataverse long term retention (Dataverse managed data lake), consumes, on average, 50% less database capacity. Live application data is compressed in Dataverse long term retention.  

This cost saving is passed onto the customer. The amount of compression depends on the kind of data. You might notice larger than 50% savings or lower than 50%. Savings might be more evident when higher volumes of data (hundreds of GB) are retained.  

Archived data is available in the history tables by allowing access using a Dynamics 365 finance and operations inquiry page. History tables don't contain indexes will consume 10% to 30% less capacity than the live tables, depending on the table and indexes. When in-app access to archived data isn't required, delete the data permanently from the History tables to get full savings. 

### Storage capacity reports 

Administrators can view the storage size in the existing Power Platform admin center reports for Dynamics 365 finance and operations tables as well as Dataverse long term retention. 

### View the storage consumed by the archived data in Dataverse long term retention  

To view storage consumed by archived data, follow these steps:
1. Go to [Power Platform admin center reports](https://learn.microsoft.com/power-platform/admin/capacity-storage) for Dataverse.
2. The archived Dynamics 365 finance and operations tables with a prefix **Retained** in the Dataverse DB storage report provide a logical view of the storage capacity consumed by the Dynamics 365 finance and operations archived in Dataverse long term retention.  

To view storage consumed by the Dynamics 365 finance and operations data, follow these steps:
1. Go to [Power Platform admin center reports for Dynamics 365 finance and operations](https://learn.microsoft.com/power-platform/admin/finance-operations-storage-capacity).
2. Select **Capacity** > **Finance and operations**.
3. The administrator can view details of the Dynamics 365 finance and operations application tables as well as the history tables. The history tables with no indexes consume lesser capacity than the live application table.  

 

Refer to Finance General Ledger documentation for  examples. 
