---
# required metadata

title: Initialize Retail Cloud Scale Unit
description: This topic explains how to initialize Retail Cloud Scale Unit.
author: AamirAllaq
manager: AnnBe
ms.date: 04/24/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang:
ms.reviewer: sericks
ms.search.scope: Retail, Operations
# ms.tgt_pltfrm:
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: retail
ms.author: aamiral
ms.search.validFrom: 2018-4-30
ms.dyn365.ops.version: 8.0
---


# Initialize Retail Cloud Scale Unit

[!include[banner](../includes/banner.md)]

If you're using a Tier-2 sandbox or production environment that has application version 8.1.2.x or later, you must initialize Retail Cloud Scale Unit (RCSU) before you can use retail channel functionality either for point of sale (POS) operations or for e-Commerce operations that use Retail Server in the cloud. Initialization will deploy a Retail Cloud Scale Unit.

This topic describes the steps for initializing Retail Cloud Scale Unit.

> [!IMPORTANT]
> For existing customers using Retail channel functionality in the cloud, to ensure continued and uninterrupted support for your business, we require that you update your retail channels to use Cloud Scale Unit. New environments deployed without Cloud Scale Unit will no longer recieve quality and service updates for cloud-hosted retail channel components. There is no action required for customers who exclusively use Store Scale Unit.  Contact your Microsoft FastTrack solution architect if you require an extension.

## Prerequisites

1. Deploy a Tier-2 sandbox or production environment that has application version 8.1.2.x or later.
2. If you require more than 1 RCSU per environment, in Microsoft Dynamics Lifecycle Services (LCS), create a support request, and enter **Access request for multiple Retail Cloud Scale Units** and indicate the environment ID, number of RCSUs, and corresponding datacenter regions. The request will be completed within five business days. If you do not require multiple RCSUs per environment, you do not need to create a support request. 

## Initialize Retail Cloud Scale Unit as part of a new environment deployment

Please make sure the headquarters is available. This is required to register the scale unit with the headquarters during the initialization process. It is not recommended to initialize a scale unit when the headquarters is under servicing, as it may become unavailable during its servicing process.

1. Make sure the headquarters environment is available and not in [Maintenance mode](../sysadmin/maintenance-mode.md).
2. In LCS, on the environment details page, select **Environment features \> Retail**.
3. On the Retail setup deployment page, select **Initialize**.
4. Select the version of the Retail Cloud Scale Unit to initialize.
5. Select a region to initialize Retail Cloud Scale Unit in.

## Configure retail channels to use Retail Cloud Scale Unit

1. After Retail Cloud Scale Unit has been deployed, in the head office client go to **Retail and commerce > Retail Headquarters > Retail Scheduler setup > Channel database** to ensure that your retail channels are configured to use the database for this Retail Cloud Scale Unit.
2. Go to each retail channel and select the Channel Profile for the corresponding Retail Cloud Scale Unit.

### Database refresh and Cloud Scale Units

Before you begin, make sure you are familiar with [Steps to complete after a database refresh for environments that use Commerce functionality](../database/database-refresh.md).

The scale unit channel database records (in the Channel Database form) cannot be moved across environments as part of database refresh. This is because the records represent environment specific configuration.

After database refresh and after the Retail Reprovisioning tool has been executed, you can regenerate the scale unit's channel database record by issuing a re-deployment of your scale unit in LCS. Any deployment or servicing operation in the scale unit will attempt to register the scale unit with the headquarters, if it detects that the registration is missing.

You can issue a re-deployment of the scale unit, without changing any components, by selecting to deploy the same version your scale unit is at already. This can be done in LCS by the following steps:

1. In LCS, on the environment details page, select **Environment features \> Retail**.
2. On the setup deployment page, select the scale unit you would like to redeploy.
3. On the scale unit's operation menu, select **Update**
4. On the slider, on the drop-down for **Select version**, pick the option **Specify a version**
5. On the text box under **Specify a version**, type in the version shown for your scale unit, shown besides the **Current version** label
6. Click on **Update** button

You do not need to select **Update extensions**, even if you have applied extensions previously, since the last extension package applied to the scale unit is automatically picked when updating a scale unit.

If you have multiple scale units, you need to perform the operation above for each scale unit. You may perform these operations in parallel, if desired.

## Deploy additional Retail Cloud Scale Units (optional)

After you have initialized the first Retail Cloud Scale Unit (RCSU), if you require additional cloud scale units, enter a support request. In the support request, state the number of RCSUs needed, environment name, and desired regions.

For each additional RCSU that you deploy, it is also recommended that you create a separate channel database group for each RCSU. To do this, follow these steps:

1. In Commerce head office, go to **Retail and commerce > Retail Headquarters > Retail Scheduler setup > Channel database group**.
2. Create a new channel database group.
3. Go to the **Retail and commerce > Retail Headquarters > Retail Scheduler setup > Channel database** form and select the channel database that corresponds to the newly created RCSU.
4. Select **Edit** and select the new channel database group.
5. Select **Save**.
6. Select **Run Full data sync** for the selected channel database.

## Additional considerations if you initialize cloud-hosted Commerce channel components in an existing environment

If you're already using cloud-hosted Commerce channel components in an environment, initialization of Retail Cloud Scale Unit will help reduce the downtime when those components are updated. Additional planning is required before initialization of Retail Cloud Scale Unit.

When you initialize your first Cloud Scale Unit in an environment that uses cloud-hosted Commerce channel components, the initialization process will migrate your channels associated to the cloud-hosted channel components to the first scale unit. Channels associated with Store Scale units are unaffected.

The migration process is transparent to the channels. After the scale unit initialization starts, the following operations are automatically performed:

1. A new Cloud Scale Unit will be created and associated with the environment.
2. The Cloud Scale Unit will be registered as an available Channel Database in the headquarters.
3. All channels mapped to the **Default** channel database in the headquarters will be updated to map to the new Cloud Scale Unit.
4. A Commerce Data Exchange (CDX) full data sync will be performed to bring the channel data to the new scale unit.

You should plan for a five-hour downtime window for store and any online channel operations that use Retail Server or Cloud Point of Sale.

This process should be first performed in a sandbox environment after a database refresh with production data is performed. This will allow for business validations and will provide guidance on the amount of time the migration process will take.

Because the Cloud Scale Unit provides dedicated and isolated compute and storage resources from other components, it has its own channel database. This means the following precautions should be taken before migration:

1. **Make sure that all shifts at the POS are closed.** After migration, you won't be able to close any shifts that were active during the migration process
2. **Make sure that all P-jobs have been successfully completed.** While the previous channel database is maintained and any transactional data will still be synced back to the headquarters, it is recommended that you run P-JOBs before you start.
3. **Sign out of all POS devices.** POS operations are not supported during migration

Here is what occurs during the initialization period:

- Cloud-hosted Commerce channels won't work, unless you turn on POS offline capability.
- POS devices with offline capability turned on will have reduced functionality.
- Any e-Commerce clients that depend on Retail Server will be disrupted.
- Channels that are hosted on Retail Store Scale Units won't be affected.
- Head office functionality is not affected.

Here is what occurs after initialization is completed:

- The device activation state of all activated POS devices is preserved, which means that the devices won't have to be reactivated.
- Stand-alone hardware station instances will continue to work.
- POS channel–side reports will be reset and won't show data from before the initialization.
- Show journal operation will also be reset and won't show data from before the initialization.
