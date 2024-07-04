---
title: Finance and operations apps archive with Dataverse long term retention FAQ
description: Access answers to frequently asked questions about archiving data in finance and operations apps with Dataverse.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 06/11/2024
ms.custom: 
  - bap-template
ms.reviewer: twheeloc
---

# Finance and operations apps archive with Dataverse long term retention FAQ

## Does testing archiving with Dataverse long-term retention require a sandbox environment?

Yes, it requires use of a Tier-2 or greater Sandbox instance. It won't work on Tier CHE. 

## How long will my archival job take to complete?

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

Application data copied to your own data lake using [Azure Synapse Link,](/power-apps/maker/data-platform/azure-synapse-link-select-fno-data) isn't deleted from your data lake when you archive with Dataverse long term retention.

Application data that's copied to your own data lake, based on non Azure Synapse Link tools like [Bring your own database-BYOD](../analytics/export-entities-to-your-own-database.md) or [Export to data lake](../data-entities/finance-data-azure-data-lake.md) are deleted from your data lake when you archive with Dataverse long term retention.

## What should I do if the installation or upgrade of the Dynamics 365 Archive with Dataverse long term retention app from Power Platform fails?

Please ensure that all the prerequisite setup steps are completed, as incorrect setup can lead to installation failure.

Please also ensure that you have logged into your finance and operations application in the last 30 days, as installation can fail if the organization has been tagged as dormant. If you are logging in for the first time after 30 days, it may take up to 4 hours for your organization to be flagged as active. 

If you encounter the following error messages during the install attempt, then wait for a few minutes and retry till it succeeds:
 - Status code 503 (Service unavailable)
 - Status code 500 (Solution operation failed due to another import blocking the operation)
 - Solution import progress has been stuck

If you encounter a **Cannot insert duplicate key exception when executing non-query** error when trying to upgrade the app, then please delete the solutions named **ArchiveServicePermissions_PROD** and **ArchiveService Anchor Solution** from the maker portal solutions page and then refresh and reattempt the install.

If you encounter the error **'MCR call center config key needs to be enabled under License Configuration in order to enable change tracking for MCRSalesTableBiEntity'**, then in Dynamics 365 Finance and Operations, go to **System administration \> License configuration** and confirm that the following checkboxes and sub-checkboxes are enabled before reattempting installation:
 - **Retail channels** - Call center



