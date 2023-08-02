---

# required metadata

title: Dynamics 365 Human Resources customer migration to the finance and operations infrastructure
description: This article describes customer migration of Microsoft Dynamics 365 Human Resources to the finance and operations infrastructure.
author: twheeloc
ms.date: 08/02/2023
ms.topic: conceptual
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-10-13
ms.dyn365.ops.version: Human Resources

---

# Dynamics 365 Human Resources customer migration

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]


Customer migration is a "lift-and-shift migration" (movement) of a customer database to the finance and operations infrastructure. Automated migration tooling is used for it. The result is a new finance and operations environment that uses the customer's Human Resources database.


#### Human Resources migration office hours
 
As has been announced, the infrastructure for the standalone Human Resources application is scheduled to be discontinued after December 31, 2023. Customers might have questions about Human Resources migration. We invite you to office hours to discuss any questions. If you're interested in joining office hours, email <dyn365hrmigration@microsoft.com>.

#### Human Resources migration TechTalk
 
To learn more about migration tooling, prerequisites, migration steps, and considerations, see this TechTalk: [Microsoft Dynamics 365 Human Resources Infrastructure Merge](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/dynamics-365-human-resources-infrastructure-merge-november-9-2022).


## Prerequisites

### User access and permissions

- The Microsoft Dynamics Lifecycle Services user should have the **Organization admin** role.
- The user should be able to [create Azure DevOps projects](/azure/devops/organizations/projects/create-project) or use an existing Azure DevOps project.
- The user should have access to [create an Azure DevOps Personal Access Security Token](/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate), or should have a token that is available to use.

### Dataverse environment backup (Sandbox)

 - Optional but recommended: Refresh the existing Human Resources sandbox environment by using a copy of the Human Resources production environment.
 - Create a new Dataverse environment by using the Power Platform admin center.
 - Copy the existing Dataverse environment, which is linked to the standalone Human Resources, to the environment that you created in the previous step.

> [!NOTE]
> When you add a database, ensure that the **Enable Dynamics 365 apps** option is set to **Yes**. For detailed information, see [Prepare a Power Platform environment](hr-cust-migration.md#prepare-a-power-platform-environment).

### Dataverse capacity

1. Use the **Summary** page in the Power Platform admin center to verify that [Dataverse storage](/power-platform/admin/finance-operations-storage-capacity) has enough available capacity for the environment copy.
2. If there isn't enough available capacity, use the [guidance for freeing up storage space](/power-platform/admin/free-storage-space) to reduce the overall consumption. Customers can also [add additional storage capacity](/power-platform/admin/add-storage).

## Customer migration process

### Create a Lifecycle Services project for Human Resources migration

The first step is to create a new finance and operations Implementation project in Lifecycle Services. The customer will have an existing Human Resources Lifecycle Services project. The existing Human Resources environments will be migrated to the new finance and operations implementation project.

To create a new project, follow these steps.

1. Sign in to Lifecycle Services as the global administrator or the designated service account user.
2. On the Lifecycle Services home page, select **Create/new (+)**.
3. Select finance and operations apps as the product.
4. In the **Project purpose** field, select **Implementation**.
5. Enter a project name and description.
6. In the **Project custom type** field, select **Microsoft Dynamics 365 Human Resources migration**.
7. Select the checkbox to agree to the terms and conditions.
8. Select **Create**.

After you've created a new Lifecycle Services project, follow these steps to set up and configure the project.

1. Select **Project onboarding** to complete the project onboarding. For more information, see [Project onboarding](../fin-ops-core/dev-itpro/lifecycle-services/project-onboarding.md).

    - Select the same region as your current environments. This selection won't affect migration.
    - For legacy systems, select **Other**.

2. Complete the project settings. As part of this step, you should configure the SharePoint Online library, Azure DevOps, and Azure connections if they are required. For more information, see [Lifecycle Services (LCS) user guide](../dev-itpro/lifecycle-services/lcs-user-guide.md).

> [!NOTE]
> Customers can use an existing Azure DevOps Project and the associated Personal Access Security Token. If an existing project is used, the configurations that are related to the project are automatically available and can be reviewed for accuracy.

### Migrate a Human Resources sandbox environment

#### Prepare to migrate the sandbox environment

After a new Lifecycle Services project has been created, and the project onboarding process has been completed, you're ready to migrate your first environment. Before you start this process, we recommend that you refresh the sandbox environment that you want to migrate from your production environment on the standalone infrastructure.

#### Prepare a Power Platform environment

> [!NOTE]
> This step is applicable only to sandbox environment migration. When you migrate the production environment, the existing Power Platform admin center environment that is attached to the production environment will be carried forward. When you add a database, ensure that the **Enable Dynamics 365 apps** button is set to **Yes**. 

- In the Power platform admin center, [create an environment with a database](/power-platform/admin/create-environment#create-an-environment-with-a-database) to use for sandbox migration, or select an existing environment.
- [Copy an environment](/power-platform/admin/copy-environment) to refresh the Power Platform environment that is used for mapping.

#### Migrate the sandbox environment

1. Sign in to Lifecycle Services as the global administrator or the designated service account user.

    > [!NOTE]
    > We recommend that you use a named user account. The signed-in user should have the **Project owner** or **Environment manager** security role in the standalone Human Resources Lifecycle Services project.

2. Open the newly created Human Resources migration project.
3. Review and complete the appropriate phases of the migration methodology and the project onboarding.
4. On the project dashboard, in the **Default: Standard acceptance test** pane, select **Migrate HR**.
5. In the **Select environment to migrate** pane, select appropriate Lifecycle Services project and the originating Human Resources environment (from your source standalone Human Resources application).
6. Enable **Map to new Power Platform environment**, and select the appropriate Power Platform environment. Then select **Next**.
7. Complete the **Deployment settings (finance and operations – sandbox)** wizard to confirm details and customer sign-off, and then select **Deploy**.

The environment state will show the progress. The state will be changed from **Loading** to **Deploying** to **Deployed**.

> [!NOTE]
> The production pane will be unavailable until the go-live project readiness checklist is completed. For more information, see [Prepare for go-live](../fin-ops-core/fin-ops/imp-lifecycle/prepare-go-live.md).

#### Considerations and assumptions

A Human Resources sandbox environment exists in a Lifecycle Services project on the tenant that has the following characteristics:

- The Human Resources sandbox environment isn't linked to an existing merged environment. Only one migration at a time can be in progress for a given Human Resources environment.
- The number of sandbox environments that are allowed at a time is based on Human Resources licensing. If enough licensing has been purchased for the tenant, additional sandbox environments will be listed in the **Environments** pane of the project.
- Migrations must be done to environments of the same type. In other words, only sandbox-to-sandbox or production-to-production migrations can be done.

    > [!NOTE]
    > Only Human Resources environment types are considered when the production or sandbox status is determined. If the environments are incorrectly categorized (that is, a production environment is marked as a sandbox environment, or a sandbox environment is marked as a production environment), contact Support.

- If the migration isn't successful, a failure error message will be shown, and a **Delete** button will become available. Use this button to delete the failed migration. You can then remigrate the environment.

#### Validate the sandbox migration

After the sandbox migration process is successfully completed, create a detailed testing plan to verify and sign off on all business processes.

Before you begin testing, validate the following details:

- Confirm that the migrated environment is accessible at the URL that is generated.
- Confirm that users can access the migrated sandbox.
- Confirm that the Dataverse environment that is associated with the migrated sandbox environment is accessible.
- Spot-check different data to confirm that the most up-to-date data is available.
- Complete the critical business processes for validation.
- Confirm that your security policies are applicable.
- Confirm that batch jobs are triggered as expected.

You won't have Remote Desktop access to the migrated sandbox. You can use self-service capabilities and tools to perform the following actions for your Tier 2+ sandbox environments:

- Access the [Azure SQL database](../fin-ops-core/dev-itpro/deployment/deploymentfaq.md#access-the-azure-sql-database).
- Access [log files](../fin-ops-core/dev-itpro/deployment/deploymentfaq.md#access-log-files).
- Use [perfmon tools](../fin-ops-core/dev-itpro/deployment/deploymentfaq.md#use-perfmon-tools).
- Turn [Maintenance mode on/off](../fin-ops-core/dev-itpro/deployment/deploymentfaq.md#access-self-service-logs).
- Restart [services](../fin-ops-core/dev-itpro/deployment/deploymentfaq.md#restart-services).
- Configure the [Regression suite automation tool](../fin-ops-core/dev-itpro/deployment/deploymentfaq.md#configure-the-regression-suite-automation-tool).

For more information, see [FAQ for self-service deployment](../fin-ops-core/dev-itpro/deployment/deploymentfaq.md).

### Migrate a Human Resources production environment

After you've finished migrating and validating a sandbox environment, follow these steps to migrate the production environment.

#### Prerequisites

- The Subscription estimator should be completed.
- The Go-live [readiness assessment](../fin-ops-core/fin-ops/imp-lifecycle/prepare-go-live.md) should be completed.
- The user initiating the Production migration in Lifecycle services should have a System administrator role on the Power Platform. 

#### Migrate the production environment

1. Sign in to Lifecycle Services as the global administrator or the designated service account user.

    > [!NOTE]
    > We recommend that you use a named user account. The signed-in user should have the **Project owner** or **Environment manager** security role in the Lifecycle Services project.

2. Open the new Human resources migration project.
3. Review and complete the appropriate phases of the migration methodology and project onboarding.
4. On the project dashboard, in the **Production** pane, select **Migrate HR**.
5. In the **Select environment to migrate** pane, select the appropriate Lifecycle Services project and the originating Human Resources environment (from your source standalone Human Resources application). Then select **Next**.
6. Complete the **Deployment settings (finance and operations – sandbox)** wizard to confirm details and customer sign-off, and then select **Deploy**.

The environment state will show the deployment progress. The state will be changed from **Loading** to **Deploying** to **Deployed**.

#### Post-migration considerations

- Apply the latest [quality updates](/fin-ops-core/fin-ops/get-started/quality-updates) to your environments.
- If you're using [virtual tables](hr-admin-integration-common-data-service-virtual-entities.md), reconfigure the endpoints.
- Reconfigure dual-write integration. Evaluate which entities must be enabled.
- Consider using virtual tables to replace dual-write for integration.
- All remaining standalone Human Resources environments will automatically be deleted ten days after successful migration of the production environment to the finance and operations infrastructure. 

#### Dual-write integration

##### Set up Microsoft Power Platform dual-write integration

1. Go to the Power Platform admin center, and select **Environments** in the left navigation.
2. Select the previously copied/refreshed environment, and confirm that the state is **Ready**.
3. Go to Lifecycle Services, and confirm that the status of the migration project is **Deployed**.
4. Under the migrated environment, select **Full details** to review additional details and [set up a dual-write application](../fin-ops-core/dev-itpro/data-entities/dual-write/lcs-setup.md#set-up-dual-write-for-new-or-existing-dataverse-environments).
5. In the **Dual-write application configuration** pane, select the checkbox to agree to map and sync data between databases, and then select **Configure**.
6. When a message box notifies you of successful dual-write configuration, select **OK**.
7. You can monitor the progress of the configuration in the details.
8. When the configuration is completed, select **Link to Power Platform environment** to sync the available data entities.
9. When the status indicates that the environments have been successfully linked, go to the Power Platform admin center to review and select the appropriate data entities.
10. In the left pane, select **Dynamics 365 apps \> Resources**.
11. Confirm that the status of the dual-write Human Resources app is **Enabled**.
12. Select the dual-write Human Resources app, and then select **Install**.
13. In the **Install dual-write Dynamics 365 Human Resources app** pane, select the appropriate environment to install the package in.
14. Select the checkbox to agree to the terms of service, and then select **Install**.
15. In the Dynamics 365 app environment, the status will be **Installing** while the installation is in progress. It will be updated to **Installed** when the installation is completed.

##### Review and apply a dual-write solution

1. In the new finance and operations environment, go to **Data management \> Dual-write**.
2. Select **Apply solution**.
3. In the pane, select **Dynamics installed solutions**, **Dual-write applications core entity maps**, and **Dynamics 365 Human Resources maps**. Then select **Apply**. A message confirms that the solution is being applied. After the solution is successfully applied, all the available table maps will be shown.
4. Review the available table maps to select and run the integration by using dual-write.
5. When you run the dual-write integration for the first time for table maps, select the **Initial sync** checkbox. If there's an existing integration from the source Human Resources environment, you don't have to select the **Initial sync** checkbox when you run the integration for table maps.

#### Recommended practices

This section outlines recommendations for migrating from the standalone infrastructure to the finance and operations infrastructure.

- We highly recommend that you work with your Microsoft Dynamics partner to get help with your Human Resources environment migration.
- Plan appropriate time to do full user acceptance testing (UAT) on the sandbox migrated environment.
- Plan and document the detailed steps to migrate integrations to the migrated environment.
- Create a detailed checklist to outline the cutover process for your migration.
- Plan an appropriate amount of downtime for your business while you do the migration.
- We highly recommend that FastTrack-qualified customers work with their FastTrack solution architect to get help overseeing the migration process.
- We highly recommend that you refresh your sandbox environment in the standalone infrastructure before you do the first migration. This refresh should include your Dataverse environment that is connected to the sandbox environment that you plan to migrate to.
- We highly recommend that you use a service account when you deploy, migrate, and create your Lifecycle Services project.
- Plan to upgrade the sandbox environment for UAT validation on the latest general availability (GA) release. For more information, see [considerations](hr-infrastructure-merge.md#considerations).

