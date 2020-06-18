---
# required metadata

title: Initialize Commerce Scale Unit (cloud)
description: This topic explains how to initialize Commerce Scale Unit (cloud).
author: AamirAllaq
manager: AnnBe
ms.date: 06/15/2020
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


# Initialize Commerce Scale Unit (cloud)

[!include[banner](../includes/banner.md)]

If you're using a Tier-2 sandbox or production environment that has application version 8.1.2.x or later, you must initialize Commerce Scale Unit (cloud) before you can use retail channel functionality either for point of sale (POS) operations or for e-Commerce operations that use Retail Server in the cloud. Initialization will deploy a Commerce Scale Unit (cloud).

This topic describes the steps for initializing Commerce Scale Unit (cloud).

> [!IMPORTANT]
> For existing customers using retail channel functionality in the cloud, to ensure continued and uninterrupted support for your business, we require that you update your retail channels to use Commerce Scale Unit. New environments deployed without Commerce Scale Unit will no longer receive quality and service updates for cloud-hosted retail channel components. There is no action required for customers who exclusively use Commerce Scale Unit (self-hosted).  Contact your Microsoft FastTrack solution architect if you require an extension.

## Prerequisites

1. Deploy a Tier-2 sandbox or production environment that has application version 8.1.2.x or later.
2. If you require more than 1 RCSU per environment, in Microsoft Dynamics Lifecycle Services (LCS), create a support request, and enter **Access request for multiple Commerce Cloud Scale Units** and indicate the environment ID, number of CSUs, and corresponding datacenter regions. The request will be completed within five business days. If you do not require multiple CSUs per environment, you do not need to create a support request. 

## Region availability
Commerce Scale Unit is available for deployment in the following regions.

| Global location | Region              | Availability        |
|-----------------|---------------------|---------------------|
| AMERICAS        | East US             | Generally available |
| AMERICAS        | East US 2           | Generally available |
| AMERICAS        | North Central US    | Generally available |
| AMERICAS        | South Central US    | Generally available |
| AMERICAS        | Central US          | Generally available |
| AMERICAS        | West US             | Generally available |
| AMERICAS        | West US 2           | Generally available |
| AMERICAS        | Canada Central      | Limited capacity    |
| AMERICAS        | Canada East         | Limited capacity    |
| AMERICAS        | West Central US     | Limited capacity    |
| APAC            | Australia East      | Generally available |
| APAC            | Southeast Asia      | Generally available |
| APAC            | Japan East          | Generally available |
| APAC            | Japan West          | Generally available |
| APAC            | Australia Southeast | Limited capacity    |
| APAC            | East Asia           | Limited capacity    |
| APAC            | India South         | Limited capacity    |
| APAC            | India Central       | Limited capacity    |
| EMEA            | West Europe         | Generally available |
| EMEA            | North Europe        | Generally available |
| EMEA            | UK South            | Limited capacity    |
| EMEA            | UK West             | Limited capacity    |

Deployment capacity in Limited capacity regions are extremely constrained. Requests for deployment are evaluated on a case-by-case basis. If you have a compelling business need for deployment in Limited capacity regions, you can file a support request to be added to the waitlist.

![Map showing region availability](media/Commerce-Scale-Unit-Region-Availability.png "Map showing region availability")

## Initialize Commerce Scale Unit as part of a new environment deployment

Please make sure the headquarters is available. This is required to register the scale unit with the headquarters during the initialization process. It is not recommended to initialize a scale unit when the headquarters is under servicing, as it may become unavailable during its servicing process.

1. Make sure the headquarters environment is available and not in [Maintenance mode](../sysadmin/maintenance-mode.md).
2. In LCS, on the environment details page, select **Environment features \> Retail**.
3. On the Retail setup deployment page, select **Initialize**.
4. Select the version of the Commerce Scale Unit to initialize.
5. Select a region to initialize Commerce Scale Unit in.

## Configure retail channels to use Commerce Scale Unit

1. After Commerce Scale Unit has been deployed, in the head office client go to **Retail and commerce > Retail Headquarters > Retail Scheduler setup > Channel database** to ensure that your retail channels are configured to use the database for this Commerce Scale Unit.
2. Go to each retail channel and select the Channel Profile for the corresponding Commerce Scale Unit.

### Database refresh and Commerce Scale Units

Before you begin, make sure you are familiar with [Steps to complete after a database refresh for environments that use Commerce functionality](../database/database-refresh.md).

The scale unit channel database records (in the Channel Database form) cannot be moved across environments as part of database refresh. This is because the records represent environment specific configuration.

After database refresh and after the Retail Reprovisioning tool has been executed, you can regenerate the scale unit's channel database record by issuing a re-deployment of your scale unit in LCS. Any deployment or servicing operation in the scale unit will attempt to register the scale unit with the headquarters, if it detects that the registration is missing.

You can issue a re-deployment of the scale unit, without changing any components, by selecting to deploy the same version your scale unit is at already. This can be done in LCS by the following steps:

1. In LCS, on the environment details page, select **Environment features \> Retail**.
2. On the setup deployment page, select the scale unit you would like to redeploy.
3. On the scale unit's operation menu, select **Update**.
4. On the slider, on the drop-down for **Select version**, pick the option **Specify a version**.
5. On the text box under **Specify a version**, type in the version shown for your scale unit, shown besides the **Current version** label.
6. Click on **Update** button.

You do not need to select **Update extensions**, even if you have applied extensions previously, since the last extension package applied to the scale unit is automatically picked when updating a scale unit.

If you have multiple scale units, you need to perform the operation above for each scale unit. You may perform these operations in parallel, if desired.

## Deploy additional Commerce Scale Units (optional)

After you have initialized the first Commerce Scale Unit (CSU), if you require additional cloud scale units, enter a support request. In the support request, state the number of RCSUs needed, environment name, and desired regions.

For each additional RCSU that you deploy, it is also recommended that you create a separate channel database group for each RCSU. To do this, follow these steps:

1. In Commerce head office, go to **Retail and commerce > Retail Headquarters > Retail Scheduler setup > Channel database group**.
2. Create a new channel database group.
3. Go to the **Retail and commerce > Retail Headquarters > Retail Scheduler setup > Channel database** form and select the channel database that corresponds to the newly created RCSU.
4. Select **Edit** and select the new channel database group.
5. Select **Save**.
6. Select **Run Full data sync** for the selected channel database.

## Additional considerations if you initialize cloud-hosted Commerce channel components in an existing environment

If you're already using cloud-hosted Commerce channel components in an environment, initialization of Commerce Scale Unit will help reduce the downtime when those components are updated. Additional planning is required before initialization of Commerce Scale Unit.

When you initialize your first Commerce Scale Unit in an environment that uses cloud-hosted Commerce channel components, the initialization process will migrate your channels associated to the cloud-hosted channel components to the first scale unit. Channels associated with Store Scale units are unaffected.

The migration process is transparent to the channels. After the scale unit initialization starts, the following operations are automatically performed:

1. A new Commerce Scale Unit will be created and associated with the environment.
2. The Commerce Scale Unit will be registered as an available Channel Database in the headquarters.
3. All channels mapped to the **Default** channel database in the headquarters will be updated to map to the new Commerce Scale Unit.
4. A Commerce Data Exchange (CDX) full data sync will be performed to bring the channel data to the new scale unit.

**Planning and testing for Commerce Scale Unit initialization**
As a general rule, when initializing Commerce Scale Unit, you must plan for a five-hour downtime window for store operations as well as any e-commerce channel operations that use Retail Server or Cloud Point of Sale.

1. Perform a database refresh from your production environment to a sandbox UAT environment. 
2. Initialize Commerce Scale Unit in the sandbox UAT environment. 
3. Note the initialization time to complete for Commerce Scale Unit. This will be comparable to the time this operation takes in your production environment, during which store operations and e-commerce operations will be unavailable.

You must perform the following additional steps before initializing Commerce Scale Unit.

- **Close all POS shifts** - After migration, POS users will be unable to close any shifts that were active during the migration process.
- **Validate that all P-jobs have been successfully completed** - It is recommended that P-jobs to synchronize pending transactions have completed before CSU is initialized.
- **Sign out of all POS device** - POS operations are not supported during migration.
- **Recall and void all suspended transactions at POS** - Suspended transactions are not preserved as part of the initialization.

> [!IMPORTANT]
> As part of Commerce Scale Unit initialization, prior suspended transactions will be lost and cannot be recalled. 

Here is what occurs during the initialization period:

- Cloud-hosted Commerce channels won't work, unless you turn on POS offline capability.
- POS devices with offline capability turned on will have reduced functionality.
- Any e-Commerce clients that depend on Retail Server will be disrupted.
- Channels that are hosted on Commerce Scale Units (self-hosted) won't be affected.
- Head office functionality is not affected.

Here is what occurs after initialization is completed:

- The device activation state of all activated POS devices is preserved, which means that the devices won't have to be reactivated.
- Stand-alone hardware station instances will continue to work.
- POS channel–side reports will be reset and won't show data from before the initialization.
- Show journal operation will also be reset and won't show data from before the initialization.
