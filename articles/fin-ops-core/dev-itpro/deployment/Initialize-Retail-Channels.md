---
title: Initialize Commerce Scale Unit (cloud)
description: Learn about how to initialize Commerce Scale Unit (cloud) in Microsoft Dynamics 365 Commerce, including prerequisites.
author: aneesmsft
ms.author: aneesa
ms.topic: article
ms.date: 09/13/2024
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-04-30
---

# Initialize Commerce Scale Unit (cloud)

[!include[banner](../includes/banner.md)]

This article explains how to initialize Commerce Scale Unit (CSU) (cloud) in Microsoft Dynamics 365 Commerce.

If you're using a Tier-2 sandbox or production environment that has application version 8.1.2.x or later, you must initialize CSU (cloud) before you can use retail channel functionality either for point of sale (POS) operations or for e-commerce operations that use Retail Server in the cloud. Initialization deploys a CSU (cloud).

## Prerequisites

- Before deploying a CSU, ensure that you have one or more of the required licenses (for example, CSU, device, or e-commerce licenses). If you don't have one or more of the required licenses, you see the following message:

    "The current licenses do not allow for the deployment of this Commerce Scale Unit. Contact support or your sales associate for assistance."

    For more information about licenses, see [D365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544). You can also contact your [Microsoft account team](https://dynamics.microsoft.com/pricing/), your [Dynamics Certified Partner](https://dynamics.microsoft.com/partners/find-a-partner/), or a [Dynamics 365 sales expert](https://go.microsoft.com/fwlink/?LinkId=2240698).
- Deploy a Tier-2 sandbox or production environment using a [supported release](../get-started/public-preview-releases.md).
- If you have the required licenses, you can self-deploy up to two CSUs per environment. If you have licenses for more than two CSUs and want to deploy them in an environment, you must create a support request. To create a support request, sign in to Microsoft Dynamics Lifecycle Services (LCS), select **Request for additional Commerce Scale Unit**, and enter the environment ID, number of CSUs, and desired datacenter regions. The request will be completed within five business days. 
- You must have project owner permissions in LCS before you can initialize CSU.
- Ensure that Retail license configuration keys are enabled in your environment. For more information, see [License codes and configuration keys report](../sysadmin/license-codes-configuration-keys-report.md).
- You must have the following keys turned on to use CSU.

    - RetailBasic
    - RetaileCommerce - If you plan to use Dynamics 365 Commerce e-commerce.
    - RetailGiftCard - If you plan to use gift cards.
    - RetailInvent - If you plan to use inventory.
    - RetailModernPos - If you plan to use point of sale (POS).
    - RetailReplenishment - If you plan to use replenishments.
    - RetailScheduler
    - RetailStores - If you plan to use POS.

## Region availability
CSU is available for deployment in the following regions.

| Global location | Region                  | Availability                             |
|-----------------|-------------------------|------------------------------------------|
| AMERICAS        | East US                 | Generally available                      |
| AMERICAS        | East US 2               | Generally available                      |
| AMERICAS        | Central US              | Generally available                      |
| AMERICAS        | West US                 | No new deployments allowed<sup>[1]</sup> |
| AMERICAS        | West US 2               | Generally available                      |
| AMERICAS        | North Central US        | No new deployments allowed<sup>[1]</sup> |
| AMERICAS        | South Central US        | No new deployments allowed<sup>[1]</sup> |
| AMERICAS        | Canada East             | No new deployments allowed<sup>[1]</sup> |
| AMERICAS        | Canada Central          | Generally available                      |
| APAC            | Australia East          | Generally available                      |
| APAC            | Australia Southeast     | No new deployments allowed<sup>[1]</sup> |
| APAC            | Japan East              | Generally available                      |
| APAC            | Japan West              | No new deployments allowed<sup>[1]</sup> |
| APAC            | East Asia               | Generally available                      |
| APAC            | Southeast Asia          | Generally available                      |
| APAC            | Central India           | Generally available                      |
| APAC            | South India             | No new deployments allowed<sup>[1]</sup> |
| UAE             | UAE North<sup>[2]</sup> | Capacity restricted                      |
| EMEA            | West Europe             | Generally available                      |
| EMEA            | North Europe            | Generally available                      |
| EMEA            | UK West                 | No new deployments allowed<sup>[1]</sup> |
| EMEA            | UK South                | Generally available                      |

***NOTE:** <br/>
[1] No new deployments allowed due capacity limits and lack of availability zones.<br/>
[2] LCS UAE can be used to deploy CSU in UAE. CSUs in UAE only run in one region and don't have a business continuity and disaster recovery (BCDR) region to fail over to if there is Azure regional failure.<br/>*

## Initialize CSU as part of a new environment deployment

When you initialize CSU as part of a new environment deployment, headquarters must be available to register the CSU. Microsoft doesn't recommend that you initialize a CSU when headquarters is under servicing, because it may become unavailable during its servicing process.

To initialize CSU as part of a new environment deployment, follow these steps.

1. Ensure that the headquarters environment is available and not in [Maintenance mode](../sysadmin/maintenance-mode.md).
1. In LCS, on the environment details page, select **Environment features \> Commerce**.
1. On the Commerce setup deployment page, select **Initialize**.
1. Select the version of the CSU to initialize.
1. Select a region in which to initialize CSU.

## Configure channels to use CSU

After you deploy a CSU, you must ensure that your channels are configured to use the database for it. 

To configure your channels to use the CSU database, follow these steps.

1. In Commerce headquarters, go to **Retail and commerce \> Headquarters setup \> Commerce Scheduler \> Channel database**.
1. In the left pane, select a channel database.
1. On the **Retail channel** FastTab, select **Add**, and then select your retail channel in the drop-down list.
1. Go to **Retail and Commerce \> Retail and commerce IT \> Distribution schedule**, and run job 9999.

> [!NOTE] 
> Job 9999 syncs all new products and customers to the CSU. This process can take a long time. If the channel must be available just for e-commerce site builder configuration, you can run job 1070 instead of job 9999.

### Database refresh and CSUs

Before you begin, make sure you're familiar with [Steps to complete after a database refresh for environments that use Commerce functionality](../database/database-refresh.md).

The CSU channel database records listed on the **Channel Database** form can't be moved across environments as part of a database refresh because the records represent an environment-specific configuration.

After database refresh, you can regenerate the CSU's channel database record by issuing a redeployment of your CSU in LCS. Any deployment or servicing operation in the CSU attempts to register the CSU with headquarters if the registration is detected as missing.

You can issue a redeployment of the CSU, without changing any components, by selecting to deploy the same version of your CSU. 

To select the same version of your CSU to deploy, follow these steps.

1. In LCS, on the environment details page, select **Environment features \> Retail**.
2. On the setup deployment page, select the CSU you want to redeploy.
3. On the CSU's operation menu, select **Update**.
4. On the slider, on the drop-down menu for **Select version**, select **Specify a version**.
5. On the text box under **Specify a version**, type in the version shown for your CSU, shown beside the **Current version** label.
6. Select **Update**.

You don't need to select **Update extensions** (even if you previously applied extensions) because the last extension package applied to the CSU is automatically picked when updating a CSU.

If you have multiple CSUs, you must perform the procedure for each CSU. You can perform these operations in parallel.

## Deploy additional CSUs (optional)

After you initialize a CSU, you can self-deploy a second CSU if your license entitles you to do so. To deploy more than two CSUs, you must create a support request. In the support request, state the number of CSUs that you require, the environment name, and the desired regions. For more information about licensing, see [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409). 

For each additional CSU that you deploy, we recommend that you create a separate channel database group by following these steps.

1. In Commerce head office, go to **Retail and Commerce \> Retail Headquarters \> Retail Scheduler setup \> Channel database group**.
2. Create a new channel database group.
3. Go to the **Retail and Commerce \> Retail Headquarters \> Retail Scheduler setup \> Channel database**, and select the channel database that corresponds to the newly created CSU.
4. Select **Edit** and select the new channel database group.
5. Select **Save**.
6. Select **Run Full data sync** for the selected channel database.

## Additional considerations if you initialize cloud-hosted Commerce channel components in an existing environment

If you're already using cloud-hosted Commerce channel components in an environment, initialization of CSU helps reduce the downtime when those components are updated. Additional planning is required before initialization of CSU.

When you initialize your first CSU in an environment that uses cloud-hosted Commerce channel components, the initialization process migrates your channels associated to the cloud-hosted channel components to the first CSU. Channels associated with Store CSUs are unaffected.

The migration process is transparent to the channels. After the CSU initialization starts, the following operations are automatically performed:

- A new CSU is created and associated with the environment.
- The CSU is registered as an available channel database in headquarters.
- All channels mapped to the **Default** channel database in headquarters are updated to map to the new CSU.
- A Commerce Data Exchange (CDX) full data sync is performed to bring the channel data to the new CSU.

**Plan and test for CSU initialization**

When initializing a CSU, you must plan for a five-hour downtime window for store operations and any e-commerce channel operations that use Retail Server or Cloud Point of Sale.

You must perform the following additional steps before initializing CSU.

- **Close all POS shifts** - After migration, POS users are unable to close any shifts that were active during the migration process.
- **Validate that all P-jobs have been successfully completed** - Microsoft recommends that P-jobs to synchronize pending transactions are completed before CSU is initialized.
- **Sign out of all POS device** - POS operations aren't supported during migration.
- **Recall and void all suspended transactions at POS** - Suspended transactions aren't preserved as part of the initialization.

To initialize CSU in your sandbox UAT environment, follow these steps.

1. Perform a database refresh from your production environment to a sandbox user acceptance testing (UAT) environment. 
1. Initialize the CSU in the sandbox UAT environment. The initialization time to complete for CSU is comparable to the time the operation takes in your production environment, during which store operations and e-commerce operations are unavailable.

> [!IMPORTANT]
> As part of CSU initialization, prior suspended transactions are lost and can't be recalled. 

During the initialization period:

- Cloud-hosted Commerce channels don't work, unless you turn on POS offline capability.
- POS devices with offline capability turned on have reduced functionality.
- Any e-commerce clients that depend on Retail Server are disrupted.
- Channels that are hosted on CSUs (self-hosted) aren't affected.
- Headquarters functionality isn't affected.

After initialization is completed:

- The device activation state of all activated POS devices is preserved so that the devices don't have to be reactivated.
- Stand-alone hardware station instances continue to work.
- POS channel–side reports are reset and don't show data from before the initialization.
- Show journal operations are reset and don't show data from before the initialization.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
