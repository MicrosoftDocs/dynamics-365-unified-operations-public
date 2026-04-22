---
title: Archive data in Dynamics 365 finance and operations apps with Dataverse
description: Learn about how to archive data in Microsoft Dynamics 365 finance and operations apps, including an overview on business application data lifecycles.
author: Weijiesa 
ms.author: Weijiesa 
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/22/2026
ms.reviewer: twheeloc
---

# Archive data in Dynamics 365 finance and operations apps with Dataverse

This article describes how to archive data in Microsoft Dynamics 365 Finance and Operations apps. Finance and Operations apps support custom retention policies for securely archiving and retaining unlimited data for the long term in a cost-efficient way. Finance and Operations apps set no limit on active data and therefore support your business growth. Nevertheless, you might want to consider moving historical, inactive data that's required for compliance and regulatory reasons to Dataverse long term retention.

## Business application data lifecycle

The business application data lifecycle has three stages:

1. Active data
1. Transitions to historical, inactive data that's required for compliance and regulatory reasons
1. Transitions to deleted data

By archiving data, organizations can achieve the following benefits:

- Secure historical, inactive application data for the long term to meet audit, legal, and regulatory requirements.
- Reduce the size of the application database and the capacity it consumes, which can potentially improve application performance associated with very large tables.

## Finance and operations data types that you can archive by using Dataverse long-term retention

This feature currently supports archiving the following types of finance and operations data by using Dataverse long-term retention:

- Dynamics 365 Finance General ledger
- Dynamics 365 Finance Tax transactions
- Dynamics 365 Supply Chain Management Inventory transactions
- Dynamics 365 Supply Chain Management Inventory journals
- Dynamics 365 Supply Chain Management Sales orders
- Dynamics 365 Commerce transactions

Support for additional data types is planned in future releases.

> [!IMPORTANT]
> Microsoft identified a synchronization issue that affects certain Data Archive scenarios when synchronizing Dynamics 365 finance and operations data to the [Dataverse-managed data lake](archive-view.md#view-archived-data-in-the-dataverse-managed-data-lake). In these scenarios, private or internal fields aren't copied. To resolve this issue, Microsoft updates the affected fields to make them public.
>
> The affected fields remain available in your Dynamics 365 finance and operations tables. We will fix the data synchronization issue by copying the missing fields from those tables into our Dataverse-managed data lake.
>
> When you install the hotfix in your Dynamics 365 finance and operations environment, which makes the affected fields public, the system automatically detects the update. No action on your part is needed. This detection occurs automatically through a [Proactive quality update](../get-started/quality-updates-schedule.md) by June 2026, depending on your current version. Alternatively, you can choose to install the hotfix manually to trigger detection sooner.
>
> These are the minimum application build versions:
>
> | Release | Availability | Platform number |
> |---|---|---|
>
> | 10.0.45/Platform update 69 | 10.0.2345.xxx or higher| 7.0.7690.144 |
> | 10.0.46/Platform update 70 | 10.0.2428.162 or higher| 7.0.7778.98 |
> | 10.0.47/Platform update 71 | 10.0.2527.94 or higher| 7.0.7858.80 |
> 
> To support the fix, the system temporarily disables the creation of new archive jobs while allowing any in-progress scheduled jobs to complete. After the data synchronization issue is resolved, the system re-enables the archive jobs. If you need further assistance, contact Microsoft Support.


## How archiving of finance and operations data works

Application administrators can schedule archival jobs and specify criteria for supported functional scenarios. The process archives data from the tables for the functional scenarios to Dataverse long-term retention.

When you initiate an archival job from the Finance and operations archive workspace, it goes through the following stages:

- The process replicates data from the live application tables in the functional scenario to Dataverse long-term retention.
- The process marks data that meets the archival criteria as ready for archiving in the live finance and operations application tables.
- The process marks the live table records as retained (archived) in Dataverse long-term retention.
- A reconciliation process verifies that all the live application table records that the process previously marked as ready for archiving are available in Dataverse long-term retention.
- The process moves live application data that it previously marked as ready for archiving to history tables in the finance and operations apps database and deletes it from the live application tables. Specific inquiry pages in Dynamics 365 finance and operations apps can access this history table data. You can either restore data from history tables to the live table or permanently purge it. The permanently purge functionality will be supported in a future release.

## Restoring data from history tables to live tables

You can restore data from history tables back to live tables from the archive workspace. When you restore data back from history tables to live tables, the corresponding archived data in Dataverse long-term retention also goes through a status change from inactive to active, as the data is no longer considered to be archived.

## Customization

The archival framework includes custom fields and custom tables in supported functional scenarios. Therefore, you can build your own archival scenario for custom tables. You must configure the table customizations before you initiate an archival job.

> [!NOTE]
> During archiving, the process doesn't archive data from tables outside the functional scenario, even if the data is related. For example, when you archive inventory transaction tables, the process doesn't automatically archive the sales tables.

> [!IMPORTANT]
>
> - The long-term-retained data is read-only.
> - The X++ delete action isn't honored when a data archival policy runs to move data out of the live finance and operations database.
> - Finance and operations attachments aren't currently supported.
> - The archival process for scenarios that involve Dataverse long term retention has multiple stages that run sequentially in the background. The process can take up to 14 days.
> - You can't move the archived data in Dataverse long term retention back to the live application table.
> - Dataverse security that's backed by Microsoft Entra ID secures the archived data in Dataverse long term retention.
> - Customers who use a self-managed encryption key (bring your own key [BYOK]) in Dataverse should be aware that long term-retained data is encrypted through a Microsoft-managed key. Customers should consider migrating to a customer-managed key. For more information, see [Migrate bring-your-own-key environments to customer-managed key](/power-platform/admin/cmk-migrate-from-byok).

## Understanding Dataverse storage costs for archived data

On average, every gigabyte (GB) that you move from the finance and operations apps to Dataverse long term retention consumes 50 percent less database capacity. Live application data is compressed in Dataverse long term retention. Savings can vary, depending on the table data. You might notice savings that are more than or less than 50 percent. Savings might be more evident when higher volumes of data (hundreds of GBs) are retained.

By allowing access through an inquiry page in finance and operations apps, archived data is made available in the history tables. History tables that have no indexes consume on average 30 percent (or more) less capacity than the live tables, depending on the table and indexes. If in-app access to archived data isn't required, permanently delete the data from the history tables to achieve full savings.

## Storage capacity reports

Administrators can view the storage size in the existing Power Platform admin center reports for both finance and operations tables and Dataverse long term retention.

### View the storage consumed by archived data in Dataverse long term retention

To view the storage consumed by archived data, follow these steps:

- Go to the [Power Platform admin center reports for Dataverse](/power-platform/admin/capacity-storage).

On the **Dataverse database storage** report, the archived finance and operations tables that have the "\-Retained" suffix provide a logical view of the storage capacity consumed by the finance and operations archived data in Dataverse long term retention.

For example, when the administrator views the **Dataverse database storage** report, the General ledger tables appear as **\<*tablename*\>-Retained**. These tables provide a logical view of the storage capacity consumed by the Finance table that's archived in Dataverse long term retention. In the example of the report in the following illustration, the mesrp\_generaljournalentrybientity-Retained table is a Finance General ledger functional scenario table that is archived. If the \<*tablename*\>-Retained table isn't visible on the report, download the report to Excel for viewing.

:::image type="content" source="./media/storage.png" alt-text="Screenshot of the Dataverse database storage report example.":::

To view the storage consumed by finance and operations data, follow these steps:

1. Go to the [Power Platform admin center reports for finance and operations apps](/power-platform/admin/finance-operations-storage-capacity).
1. Select **Capacity** \> **Finance and operations**.
1. The administrator can view details of both the finance and operations application tables and the history tables. History tables that have no indexes consume less capacity than live application tables.

The live table consumes the highest capacity, followed by the history table, and then the \<*tablename*\>-Retained table in Dataverse long term retention.

To get maximum capacity savings in production, consider purging data from the history tables.

To understand the capacity reduced savings, compare the table data for the live, history, and \<*tablename*\>-Retained tables from the reports after an archival policy run.

> [!NOTE]
> After archiving, the automatic tuning process can take up to seven days before the reduced capacity is reflected in the history table. It can take up to a day before the archived data capacity for \<*tablename*\>-Retained tables is reflected in the Dataverse database capacity.
