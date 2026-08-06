---
title: Finance and operations apps archive with Microsoft Dataverse long term retention FAQ
description: Access answers to frequently asked questions about archiving data in finance and operations apps with Microsoft Dataverse.
author: nandadevrmenon
ms.author: nrajeevmenon
ms.topic: faq
ms.date: 08/04/2026
ms.custom: 
  - bap-template
ms.reviewer: twheeloc
---

# Finance and operations apps archive with Microsoft Dataverse long term retention FAQ

[!include [banner](../includes/banner.md)]

## Does testing archiving with Dataverse long-term retention require a sandbox environment?

Yes, it requires use of a Tier-2 or greater sandbox instance. It doesn't work on Tier CHE.

## How long does my archival job take to complete?

The application assigns data archival jobs a lower priority. The duration of an archival job depends on the data volumes. A job can take around 7-14 days based on data volume.

## After data is archived, can I access the live data and the archived data from Dataverse long term retention?

Yes, you can use Microsoft Fabric (with the Power BI option) to query live and archived data. Dataverse makes it easy to set up Fabric.

## Can I view archived data from my finance and operations application?

Yes, an application-specific inquiry page is available so that you can view archived data. After data is permanently purged from history tables, it's no longer available for viewing. You can use Fabric (with the Power BI option) to query data from Dataverse long term retention.

## Can I restore data from Dataverse long term retention back to live tables?

No, data restore from Dataverse long term retention to live tables isn't supported.

## Do I save the maximum database capacity if I purge data from history tables?

To get full savings, purge data from history tables.

## Are related tables archived by this feature?

No, only the data from the live application tables that are in the scenario is archived. Dependent transactions outside the supported archive scenario aren't archived. For example, archiving of the Inventory Transaction table doesn't archive its original transactions. Administrators must set up archiving of the SalesOrder table separately.

## I linked my finance and operations environment with a Dataverse environment and ran a successful archival job from my workspace. Can I make a change to relink the finance and operations environment to a new Power Apps/CE environment?

No, don't make this change. It causes data loss.

## I ran a successful archival job from my archival workspace in finance and operations apps. When I refresh the finance and operations database with new production data, is my archived data refreshed with the same production Dataverse backup?

No, currently, a refresh of the finance and operations database doesn't automatically refresh Dataverse. You must refresh Dataverse separately from production.

A database refresh can also affect your archive jobs if you perform it by using Lifecycle Services. An Lifecycle Services database refresh doesn't copy information from Dataverse. As a result, Lifecycle Services doesn't copy any in-flight archive jobs from the source environment to the target environment. This design prevents failures that the lack of corresponding records in Dataverse would otherwise cause. You can restart these jobs after the refresh, and archiving continues as normal.

## There's no inventory closing for moving average transactions. Does this condition mean that I can't archive these transactions?

No, the inventory transaction archival scenario isn't limited for transactions. You can archive moving average transactions and standard cost transactions if they have closed inventory.

## How can I meet the requirement of my auditors who need to view the transactional data archived with Dataverse long term retention?

You can [view archived data](archive-view.md) in Dataverse long term retention with Microsoft Fabric.

You can also view the archived data from within the finance and operations History table for all the different scenarios. [General Ledger example](archive-gl.md#view-historical-data-from-the-history-table).

## I export finance and operations application data to my own data lake. If I archive data from my live finance and operations application tables, is the archived data removed from my own data lake?

Dataverse long-term retention isn't supported on Bring Your Own Database (BYOD), and data preservation in BYOD isn't guaranteed.

## I need to perform periodic data refreshes from the Dynamics 365 Finance and Operations production database to my sandbox environment. What guidance should I provide to customers using the Data Archive feature?

Two scenarios exist for this situation:

Scenario 1 - You executed the Data Archive scenario in the production environment
Restore the AXDB from LCS and copy the Dataverse environment from the Power Platform admin center to ensure both environments are identical at the time of the data refresh.

> [!NOTE]
> Ensure no archival jobs are running, as this condition could interfere with the execution of LTR jobs in the sandbox environment.

Scenario 2 - You're testing the Data Archive scenario on the sandbox environment and Data Archive isn't enabled in the production environment.
Restore the AXDB from LCS and copy the Dataverse environment from the Power Platform admin center to ensure both environments are identical at the time of the data refresh.
After restoring the AXDB and Dataverse environments, repeat all the steps related to the Data Archive setup in the sandbox. After this step is completed, restart the data archive testing from scratch.

## What should I do if the installation or upgrade of the Dynamics 365 Archive with Dataverse long term retention app from Power Platform fails?

### Prerequisites before installation

- **Complete all prerequisite setup steps.**

    Ensure that you complete all prerequisite setup steps. Incorrect setup can lead to installation failure.

- **Check application activity.**

    You must sign in to your finance and operations app within the last 30 days. If your organization is marked as dormant, installation might fail.

    If you sign in after more than 30 days, your organization might take **up to 4 hours** to be marked as active.

## What should I do if scheduling an archive job fails?

### Case 1: Change tracking or retention isn't enabled on live tables in sandbox environment

**Symptom**

You see an error message similar to the following when you try to schedule an archive job on your sandbox environment:

>An error occurred while creating the long term retention job. Entity:'mserp_salestablebientity' is not retention enabled. Error: FnO entity SalesTableBiEntity is either not enabled for Row Version ChangeTracking or not enabled for Retention.

**Resolution**

If you see this error in your sandbox environment after performing a database refresh from an environment where the data archive solution isn't installed, you need to set up data archival again in the sandbox. For more information, see [Archive FAQs - Data Refresh](archive-faq.md#i-need-to-perform-periodic-data-refreshes-from-the-dynamics-365-finance-and-operations-production-database-to-my-sandbox-environment-what-guidance-should-i-provide-to-customers-using-the-data-archive-feature).

This process also requires reinstalling the Archive with Dataverse Long Term Retention application from PPAC, to configure the tables for change tracking and long-term retention again.

If a newer application version is available for update in PPAC, installing the update is sufficient to configure the environment. Otherwise, delete all Dataverse solutions related to Data Archival from PowerApps Maker and install the application again from PPAC. The steps to follow are:

1. Delete solution `msdyn_ArchiveServiceAnchor`.
1. Delete all `ArchiveTablesVirtualEntities` and `ArchiveVirtualEntities solutions`.
1. Reinstall the Archive with Dataverse Long Term Retention application from PPAC.
1. Try scheduling the archive job again.

### Case 2: Entities with missing or non-public table fields

**Symptom**

You see an error message similar to the following when trying to schedule an archive job:

>An error occurred while creating the long term retention job. There are entities with missing or non-public table fields. EntityName: GeneralJournalAccountEntryBiEntity, MissingFields: [MissingCustomField1, MissingCustomField2]; EntityName: GeneralJournalEntryBiEntity, NonPublicFields: [PrivateCustomField3];

**Resolution**

This validation error occurs when you add customized fields to the live tables but don't add them to the corresponding F&O data entities, or if you add them to the entity but use a Private or Internal access modifier.
To fix this problem, make sure that for each customized table field, the following conditions are true:

- You expose the field in the corresponding data entity through a mapped field.
- The data entity field has the Public access modifier.

## What can I do if an archive job ends in an **Error** state in the workspace?

When a data archive job ends in an **Error** state, you can't schedule new archive jobs for the same archive scenario. Any existing job in a **Scheduled** state for that scenario stays in the queue. This behavior helps prevent further disruptions or data inconsistencies within that specific data archive scenario.
If you encounter this issue, contact Support for assistance in diagnosing and resolving the underlying cause.
You can continue to run other data archive scenarios. For example, you can execute the **Tax archive** job while the **General Ledger archive** job remains in a failed state.

### Common installation failure cases and resolutions

#### Case 1: Status error code or duplicate key error

##### Symptom 1: Status error code

**Error messages and behavior**

> Status code 503: Service unavailable

> Status code 500: Solution operation failed due to another import blocking the operation

Solution import progress is stuck.

**Resolution**

Wait a few minutes, and then try the installation again. Repeat this process until installation is successful.

##### Symptom 2: Duplicate key error during upgrade

**Error message**

> Cannot insert duplicate key exception when executing non-query

**Resolution**

1. In the maker portal, go to **Solutions**.
1. Delete the following solutions:

    - msdyn_ArchiveServicePermissions_PROD
    - msdyn_ArchiveServiceAnchor
    - msdyn_ArchiveService

1. Refresh, and then repeat the **Dynamics 365 Archive with Dataverse long term retention** installation from the Power Platform admin center.

#### Case 2: Missing license configuration key

**Error message**

> MCR call center config key needs to be enabled under License Configuration in order to enable change tracking for MCRSalesTableBiEntity.

**Resolution**

1. In Dynamics 365 finance and operations apps, go to **System administration** \> **License configuration**.
1. Select the following checkboxes and sub-checkboxes: **Retail channels** \> **Call center**.

#### Case 3: Virtual entity that isn't eligible for archival

**Error message**

> Failed to validate if retention is enabled for finance and operations apps ve : generaljournalentrybientity... entity isn't eligible for archival

**Resolution**

1. In the maker portal, go to **Tables** \> **Available Finance and Operations Entity**.
1. Ensure that the **Refresh** column is visible.
1. Refresh the previously mentioned entity.

    > [!NOTE]
    > If you add custom fields to the backing table of the entity (for example, `GeneralJournalEntry`), ensure that you add all custom fields to the entity **before** you refresh it.

#### Case 4: Data source configuration issue

**Error message**

> Unable to establish connection using data source: 'Finance and Operations Virtual Data Source Configuration'. Failed to sync entity metadata.

**Cause**

The user who is performing the installation in the Power Platform admin center either **doesn't exist** or **isn't an administrator** in finance and operations apps.

**Resolution**

Ensure that the installation user exists in finance and operations apps and has the administrator role.
