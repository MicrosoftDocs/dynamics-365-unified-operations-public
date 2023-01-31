---
# required metadata

title: Provision Human Resources
description: This article explains the process of provisioning a new production environment for Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 01/07/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SystemAdministrationWorkspaceForm
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Provision Human Resources

_**Applies To:** Human Resources on the stand-alone infrastructure_ 

> [!NOTE]
> Starting June 2022, Human Resources environments can be deployed only on the finance and operations app infrastructure. For more information, see [Provision Human Resources in the finance and operations infrastructure](hr-admin-setup-provision-fo.md).

This article explains the process of provisioning a new production environment for Microsoft Dynamics 365 Human Resources. 

## Prerequisites

Before you begin provisioning a new production environment, the following prerequisites must be in place:

- You have purchased Human Resources through a Cloud Solution Provider (CSP) or enterprise architecture (EA) agreement. If you have an existing Microsoft Dynamics 365 license that already includes the Human Resources service plan, and you can't complete the steps in this article, contact Support.

- The global administrator has signed in to [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com) (LCS) and created a new Human Resources project. 

## Provision a Human Resources trial environment

>[!NOTE]
> Starting April 2022, the Human Resources trial environments will not be available on the stand-alone application. Potential customers who are interested in evaluating the Human Resources capabilities within finance and operations apps, can do so using the free 30-day trial along with the demo data. Dynamics 365 Finance will include the Human Resources capabilities brought to the Finance infrastructure through the merge of the stand-alone application. For more information, see [Merging of HR offerings brings capabilities together for customers](https://cloudblogs.microsoft.com/dynamics365/it/2021/09/15/merging-of-hr-offerings-brings-capabilities-together-for-customers). For more information about Dynamics 365 Finance trials, see the step-by-step [guide](../fin-ops-core/fin-ops/get-started/before-you-buy.md). 


Prior to provisioning your first sandbox or production environment, you may want to provision a [Human Resources trial environment](https://go.microsoft.com/fwlink/p/?LinkId=2115962) to validate Human Resources functionality. Trial environments contain fictitious data that can be used to explore the program in a safe manner. Although a trial environment is owned by the user who requested it, other users can be invited through the system administration experience for Human Resources. 

Trial environments help evaluate human resources functionality for individuals who do not already have access to a Human Resources environment. If you are provisioning a trial environment and the authenticated user already has access to one or more existing Human Resources environments, the user will be redirected to the existing environment or list of environments.

Trial environments aren't intended to be used as production environments. They are limited to a 30-day trial period. When the trial period expires, the environment and all the data that's in it will be deleted and can't be recovered. The environment can't be converted to a sandbox or production environment. You can sign up for a new trial environment after the existing environment expires.

When creating a Human Resources trial environment, a Power Apps trial environment is also created on the tenant and linked to the Human Resources environment. The Power Apps environment, named "TestDrive", has the same trial period as the Human Resources environment.

> [!NOTE]
> Provisioning a Human Resources trial environment will fail if the authenticated user does not have permission to create Power Apps trial environments. The user must be included in the user group who can create trial environments in the Power Platform admin center. For more information, see [Control who can create and manage environments in the Power Platform admin center](/power-platform/admin/control-environment-creation).

## Plan Human Resources environments

Before you create your first Human Resources environment, you should carefully plan the environment needs for your project. A base subscription to Human Resources includes two environments: a production environment and a sandbox environment. Depending on the complexity of your project, additional sandbox environments may need to be purchased to support project activities. 

Considerations for additional environments:

- **Data migration**: Data migration activities to allow your sandbox environment to be used for testing purposes throughout the project. Having an additional environment allows data migrations activities to continue while testing and configuration activities occur simultaneously in a different environment.
- **Integration**: Configure and test integrations, which could include native integrations, such as Ceridian Dayforce, or custom integrations.
- **Training**: You may need a separate environment that is configured with a set of training data in order to train your employees on the use of the new system. 
- **Multi-phase project**: Support configuration, data migration, testing, or other activities in a project phase that is planned after the initial go-live of the project.

 > [!IMPORTANT]
 > As you consider your environment, we recommend the following:
 > - Use your production environment throughout your project as your GOLD configuration environment. This is important, because you can't copy a sandbox environment to a production environment. Therefore, when you go-live, your GOLD environment is your production environment, and you will complete your cutover activities in this environment.</br></br>
 > - Use your sandbox or another environment to perform a mock cutover prior to your go-live. You can do this by refreshing the production environment with your GOLD configuration into your sandbox environment.</br></br>
 > - Keep a detailed cutover checklist that includes each of the data packages required to migrate the final data into the production environment during the go-live cutover.</br></br>
 > - Use your sandbox environment throughout your project as your TEST environment. If you need additional environments, your organization can purchase them for an additional cost.</br></br>

## Create an LCS project

To use LCS to manage your Human Resources environments, you must first create an LCS project.

1. Sign in to [LCS](https://lcs.dynamics.com/Logon/Index) by using the account that you used to subscribe to Human Resources.

   > [!NOTE]
   > To ensure successful provisioning, the account you use to provision the Human Resources environment must be assigned to either the **System Administrator** or **System Customizer** role in the Power Apps environment associated with the Human Resources environment. For more information about assigning security roles to users in the Power Platform, see [Configure user security to resources](/power-platform/admin/database-security).

2. Select the plus sign (**+**) to create a project.

3. Select **Microsoft Dynamics 365 Human Resources** as the product name and product version.

4. Select the **Dynamics 365 Human Resources** methodology.

5. Select **Create**.

For information about how to get started with Human Resources, see the **Human Resources** methodology that you created in your new project. After you've finished creating the project, complete the following procedure to provision your Human Resources environment.

## Provision a Human Resources project

After you've created an LCS project, you can provision Human Resources into an environment.

1. In your LCS project, select the **Human Resources App Management** tile.

2. Indicate whether this environment is a Sandbox or Production instance of Human Resources. Early preview features may be available in Sandbox instances to allow for early feedback and testing.
   
    > [!NOTE]
    > The Human Resources instance type can't be changed once set. Verify the correct instance type is selected before continuing.</br></br>
    > The Human Resources instance type is separate from the instance type of the Microsoft Power Apps environment, which you set in the Power Apps Admin center.
    
3. Select the **Include Demo Data** option if you want your environment to include the same demo data set used in the Human Resources Trial environment. Demo data is beneficial for long-term demo or training environments, and should never be used for production environments. You must choose this option upon initial deployment. You can't update an existing deployment later.

4. Human Resources is always provisioned into a Microsoft Power Apps environment to enable Power Apps integration and extensibility. Read the “Selecting a Power Apps environment” section of this article before you continue. If you don't already have a Power Apps environment, select Manage environments in LCS or navigate to the Power Apps Admin center. Then follow the steps to [Create a Power Apps environment](/powerapps/administrator/create-environment).

5. Select the environment to provision Human Resources into.

6. Select **Yes** to agree to the terms and begin deployment.

   Your new environment appears in the list of environments in the navigation pane on the left. However, you can't start to use the environment until the deployment status is **Deployed**. This process typically takes a few minutes. If the provisioning process is unsuccessful, contact Support.

7. Select **Log on to Human Resources** to use your new environment.

    > [!NOTE]
    > If you haven't yet signed off on the final requirements, you can deploy a test instance of Human Resources in the project. You can then use this instance to test your solution until you sign off. If you use your new environment for testing, you must repeat this procedure to create a production environment.

## Select a Power Apps environment

You can integrate and extend the use of Human Resources data using Power Apps tools. For information about Power Apps environments, including environment scope, environment access, and creating and choosing an environment, see [Announcing Power Apps environments](https://powerapps.microsoft.com/blog/powerapps-environments/). 

Use the following guidance when determining which Power Apps environment to deploy Human Resources into: 

1. In LCS, select **Manage environments**. You can also go directly to the Power Apps Admin center, where you can view existing environments and create new ones.

2. A single Human Resources environment is mapped to a single Power Apps environment.

3. A Power Apps environment contains Human Resources, along with the corresponding Power Apps, Power Automate, and Dataverse applications. If the Power Apps environment is deleted, so are the apps within it. When provisioning a Human Resources environment, you can provision either a **Trial** or **Production** environment. Choose the type of environment based on how the environment will be used. 

4. Data integration and testing strategies should be considered, such as Sandbox, UAT, or Production. Carefully consider the implications for your deployment, because it's not easy to change which Human Resources environment is mapped to a Power Apps environment.

5. The following Power Apps environments can't be used for Human Resources. They're filtered from the selection list within LCS:
 
    - **Default Power Apps environments** - While each tenant is automatically provisioned with a default Power Apps environment, we don't recommend using them with Human Resources. All tenant users can access the Power Apps environment and could unintentionally corrupt production data when testing and exploring with Power Apps or Power Automate integrations. 
   
    - **Trial environments** - These environments are created with an expiration date. Upon expiration, your environment and any Human Resources instances contained within it will be removed automatically.
   
    - **Unsupported geographies** - The environment must be in a supported geography. For more information, see [Supported geographies](hr-admin-setup-provision.md#supported-geographies).
    
    - **Environments without a database** – The environment must have a Microsoft Dataverse database attached. An environment with a database can be created or a database can be attached to an existing environment without a database. For more information, see [Add a Microsoft Dataverse database](/power-platform/admin/create-database) and [Create an environment with a database](/power-platform/admin/create-environment#create-an-environment-with-a-database).

6. Dual-write capabilities for integrating Human Resources data with the Power Apps environment can only be used if the **Enable Dynamics 365 apps** option is selected for the environment. For more information, see [Dual-write home page](../fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-home-page.md).

    > [!NOTE]
    > The **Enable Dynamics 365 apps** option must be selected at the time the Power Apps environment is created. If the option is not selected at the time of provisioning, you won't be able to use Dual-write to integrate data between Dynamics 365 Human Resources and the Power Apps environment, or install Dynamics 365 apps such as Dynamics 365 Sales and Field Service on the environment. This option is not reversible. 
    > -  Human Resources does not support changing the linked Dataverse instance once Human Resources has been deployed into it. </br></br>
    > For more information, see [Some important considerations when creating a new environment](/power-platform/admin/create-environment#some-important-considerations-when-creating-a-new-environment) on the Power Platform documentation site.  

7. After you've determined the correct environment to use, you can continue with the provisioning process. 

### Supported geographies

Human Resources currently supports the following geographies:

- United States
- Europe
- United Kingdom
- Australia
- Canada
- Asia 

When you create a Human Resources environment, you select a Power Apps environment to associate with the Human Resources environment. The Human Resources environment is then provisioned in the same Azure geography as the selected Power Apps environment. You can select where the Human Resources environment and database physically reside by selecting the geography when creating the Power Apps environment that will be associated with the Human Resources environment.

You can select the Azure *geography* in which the environment is provisioned, but you can't select the specific Azure *region*. Automation determines the specific region within the geography in which the environment is created to optimize load balancing and performance. You can find information on Azure geographies and regions in the documentation on [Azure geographies](https://azure.microsoft.com/global-infrastructure/geographies).

The data for the Human Resources environment will always be contained within the Azure geography in which it is created. However, it won't always be contained within the same Azure region. For disaster recovery purposes, the data will be replicated in both the primary Azure region and a secondary failover region within the geography.

 > [!NOTE]
 > Migrating a Human Resources environment from one Azure region to another isn't supported.

## Grant access to the environment

By default, the global administrator who created the environment has access to it. You must explicitly grant access to additional application users. You must add users and assign the appropriate roles to them in the Human Resources environment. For more information, see [Create new users](/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/create-new-users) and [Assign users to security roles](/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/assign-users-security-roles). 


[!INCLUDE[footer-include](../includes/footer-banner.md)]

