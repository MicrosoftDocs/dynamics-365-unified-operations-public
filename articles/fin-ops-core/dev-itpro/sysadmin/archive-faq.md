---
title: Finance and operations apps archive with Dataverse long term retention FAQ
description: Access answers to frequently asked questions about archiving data in finance and operations apps with Dataverse.
author: pnghub
ms.author: brijeshjoshi
ms.topic: faq
ms.date: 04/29/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Finance and operations apps archive with Dataverse long term retention FAQ

## Does testing archiving with Dataverse long-term retention require a sandbox environment?

Yes, it requires use of a Tier-2 or greater Sandbox instance. It doesn't work on Tier CHE.

## How long does my archival job take to complete?

Data archival jobs are assigned a lower priority by the application. The duration of an archival job is dependent upon the data volumes. A job can take around 7-14 days based on data volume.

## After data is archived, can I access the live data and the archived data from Dataverse long term retention?

Yes, you can use Microsoft Fabric (with the Power BI option) to query live and archived data. Dataverse makes it easy to set up Fabric.

## Can I view archived data from my finance and operations application?

Yes, an application-specific inquiry page is available so that you can view archived data. After data is permanently purged from history tables, it's no longer available for viewing. You can use Fabric (with the Power BI option) to query data from Dataverse long term retention.

## Can I restore data from Dataverse long term retention back to live tables?

No, data restore from Dataverse long term retention to live tables isn't supported.

## Do I save the maximum database capacity if I purge data from history tables?

For full savings, users can purge data from history tables.

## Are related tables archived by this feature?

No, only the data from the live application tables that are in the scenario is archived. Dependent transactions outside the supported archive scenario aren't archived. For example, archiving of the Inventory Transaction table doesn't archive its original transactions. Administrators must set up archiving of the SalesOrder table separately.

## I linked my finance and operations environment with a Dataverse environment and ran a successful archival job from my workspace. Can I make a change to relink the finance and operations environment to a new Power Apps/CE environment?

No, changes cause data loss and shouldn't be made.

## I ran a successful archival job from my archival workspace in finance and operations apps. When I refresh the finance and operations database with new production data, is my archived data refreshed with the same production Dataverse backup?

No, Currently, a refresh of the finance and operations database doesn't automatically refresh Dataverse. You must refresh Dataverse separately from production.

## There's no inventory closing for moving average transactions. Does this mean that we can't archive these transactions?

No, the inventory transaction archival scenario isn't limited for transactions. Moving average transactions and standard cost transactions can be archived if they have closed inventory.

## How can I meet the requirement of my auditors who need to view the transactional data archived with Dataverse long term retention?

You can [view archived data](archive-view.md) in Dataverse long term retention with Microsoft Fabric.

You can also view the archived data from within the finance and operations History table for all the different scenarios. [General Ledger example](archive-gl.md#view-historical-data-from-the-history-table).

## I export finance and operations application data to my own data lake. If I archive data from my live finance and operations application tables, will the archived data be removed from my own data lake?

Dataverse long-term retention isn't supported on Bring Your Own Database (BYOD), and data preservation in BYOD isn't guaranteed.

## I needs to perform periodic data refreshes from the Finance and Operations Production database to their sandbox environment. What guidance should we provide to customers using the Data Archive feature?

There are two scenarios in this situation as follows:

**Scenario 1: You have executed the Data Archive scenario in the production environment.**
- You need to restore the AXDB from LCS and copy the Dataverse environment from the Power Platform admin center to ensure both environments are identical at the time of the data refresh.

> Note: 
> Please ensure no archival jobs are running, as this could interfere with the execution of LTR jobs on the Sandbox.

**Scenario 2: You are testing the Data Archive scenario on the Sandbox environment (Data Archive is not enabled on Production environment).**
- You need to restore the AXDB from LCS and copy the Dataverse environment from the Power Platform admin center to ensure both environments are identical at the time of the data refresh.
- After restoring the AXDB and Dataverse environment, you need to repeat all the steps related to the Data Archive setup on the Sandbox. Once this is done, they will be ready to restart their data archive testing from scratch.

## What should I do if the installation or upgrade of the Dynamics 365 Archive with Dataverse long term retention app from Power Platform fails?

### Prerequisites before installation

- **Complete all prerequisite setup steps.**

    Ensure that all prerequisite setup steps are completed. Incorrect setup can lead to installation failure.

- **Check application activity.**

    You must have signed in to your finance and operations app within the last 30 days. If your organization is marked as dormant, installation might fail.

    If you're signing in after more than 30 days, your organization might take **up to 4 hours** to be marked as active.

## What can I do if archive job ends in an **Error** state in the workspace?

- When a data archive job ends in an **Error** state, the system automatically blocks users from scheduling new archive jobs for the same archive scenario. Any existing job in a **Scheduled** state for that scenario will remain in the queue.  
 This behavior is by design and helps prevent further disruptions or data inconsistencies within that specific data archive scenario.
- If you encounter this issue, please contact **Microsoft Support** for assistance in diagnosing and resolving the underlying cause.
- In the meantime, you can continue to run other data archive scenarios. For example, you can execute the **Tax Archive** job while the **General Ledger Archive** job remains in a failed state.

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

1. Refresh, and then repeat install **Dynamics 365 Archive with Dataverse long term retention** from the Power Platform admin center.

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
    > If custom fields were added to the backing table of the entity (for example, `GeneralJournalEntry`), ensure that all custom fields are added to the entity **before** you refresh it.

#### Case 4: Data source configuration issue

**Error message**

> Unable to establish connection using data source: 'Finance and Operations Virtual Data Source Configuration'. Failed to sync entity metadata.

**Cause**

The user who is performing the installation in the Power Platform admin center either **doesn't exist** or **isn't an administrator** in finance and operations apps.

**Resolution**

Ensure that the installation user exists in finance and operations apps and has the administrator role.
