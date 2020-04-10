---
# required metadata

title: Provision Human Resources
description: This article walks you through the process of provisioning a new production environment for Microsoft Dynamics 365 Human Resources.
author: andreabichsel
manager: AnnBe
ms.date: 02/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Provision Human Resources

This article walks you through the process of provisioning a new production environment for Microsoft Dynamics 365 Human Resources. This article assumes that you've purchased Human Resources through a Cloud Solution Provider (CSP) or enterprise architecture (EA) agreement. If you have an existing Microsoft Dynamics 365 license that already includes the Human Resources service plan, and you can't complete the steps in this article, contact Support.

To begin, the global administrator should sign in to [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com) (LCS) and create a new Human Resources project. Unless a licensing issue prevents you from provisioning Human Resource, assistance from Support or Dynamics Service Engineering (DSE) representatives isn't required.

## Create an LCS project

To use LCS to manage your Human Resources environments, you must first create an LCS project.

1. Sign in to [LCS](https://lcs.dynamics.com/Logon/Index) by using the account that you used to subscribe to Human Resources.

2. Select the plus sign (**+**) to create a project.

3. Select **Microsoft Dynamics 365 Human Resources** as the product name and product version.

4. Select the **Dynamics 365 Human Resources** methodology.

5. Select **Create**.

For information about how to get started with Human Resources, see the **Human Resources** methodology that you created in your new project. After you've finished creating the project, complete the following procedure to provision your Human Resources environment.

## Provision a Human Resources project

After you've created an LCS project, you can provision Human Resources into an environment.

1. In your LCS project, select the **Human Resources App Management** tile.

2. Indicate whether this is a Sandbox or Production instance of Human Resources. Early preview features may be available in Sandbox instances to allow for early feedback and testing.
   
    > [!NOTE]
    > The Human Resources instance type cannot be changed once set. Verify the correct instance type is selected before continuing.</br></br>
    > The Human Resources instance type is separate from the instance type of the Microsoft Power Apps environment, which you set in the Power Apps Admin center.
    
3. Select the **Include Demo Data** option if you want your environment to include the same demo data set used in the Human Resources Test Drive experience. This is beneficial for long-term demo or training environments, and should never be used for production environments.  Note that you must choose this option upon initial deployment. You cannot update an existing deployment later.

4. Human Resources is always provisioned into a Microsoft Power Apps environment to enable Power Apps integration and extensibility. Read the “Selecting a Power Apps environment” section of this article before you continue. If you don't already have a Power Apps environment, select Manage environments in LCS or navigate to the Power Apps Admin center. Then follow the steps to [Create a Power Apps environment](https://docs.microsoft.com/powerapps/administrator/create-environment).

5. Select the environment to provision Human Resources into.

6. Select **Yes** to agree to the terms and begin deployment.

   Your new environment appears in the list of environments in the navigation pane on the left. However, you can't start to use the environment until the deployment status is updated to **Deployed**. This process typically takes a few minutes. If the provisioning process is unsuccessful, you must contact Support.

7. Select **Log on to Human Resource** to use your new environment.

    > [!NOTE]
    > If you haven't yet signed off on the final requirements, you can deploy a test instance of Human Resources in the project. You can then use this instance to test your solution until you sign off. If you use your new environment for testing, you must repeat this procedure to create a production environment.

    > You might consider leveraging a free 60-day [Human Resources trial environment](https://dynamics.microsoft.com/talent/overview/). Although a trial environment is owned by the user who requested it, other users can be invited through the system administration experience for Human Resources. Trial environments contain fictitious data that can be used to explore the program in a safe manner. They aren't intended to be used as production environments. Note that when a trial environment expires after 60 days, all the data that's in it is deleted and can't be recovered. You can sign up for a new trial environment after the existing environment expires.

## Select a Power Apps environment

The integration between Human Resources and the Power Apps environments lets you integrate and extend the use of Human Resources data using Power Apps tools. Understanding the purpose of Power Apps environments will not only help you build apps to extend Human Resource, but will also help you select the correct environment when provisioning Human Resource. For information about Power Apps environments, including environment scope, environment access, and creating and choosing an environment, see [Announcing Power Apps environments](https://powerapps.microsoft.com/blog/powerapps-environments/). 

Use the following guidance when determining which Power Apps environment to deploy Human Resources into: 

1. In LCS, select **Manage environments**, or go directly to the Power Apps Admin center where you can view existing environments and create new environments.

2. A single Human Resources environment is mapped to a single Power Apps environment.

3. A Power Apps environment contains Human Resources, along with the corresponding Power Apps, Power Automate, and Common Data Service applications. If the Power Apps environment is deleted, so are the apps within it. When provisioning a Human Resources environment, you can provision either a **Trial** or **Production** environment. Choose the type of environment based on how the environment will be used. 

4. Data integration and testing strategies should be considered, such as Sandbox, UAT, or Production. We recommend that you consider the various implications for your deployment, because it isn't easy to later change which Human Resources environment is mapped to a Power Apps environment.

5. The following Power Apps environments cannot be used for Human Resources and will be filtered from the selection list within LCS:
 
    - **Default Power Apps environments** - Although each tenant is automatically provisioned with a default Power Apps environment, we don't recommend using them with Human Resources because all tenant users have access to the Power Apps environment and could unintentionally corrupt production data when testing and exploring with Power Apps or Power Automate integrations.
   
    - **Trial environments** - These environments are created with an expiration date and will expire after that time, causing your environment and any Human Resources instances contained within to be removed automatically.
   
    - **Unsupported regions** - Currently Human Resources is only supported in the following regions: United States, Europe, United Kingdom, Australia, Canada and Asia.

    > [!NOTE]
    > The Human Resources environment is provisioned in the same region in which the Power Apps environment is provisioned. Migrating a Human Resources environment to another region is not supported.

6. After you have determined the correct environment to use, you can continue with the provisioning process. 
 
## Grant access to the environment

By default, the global administrator who created the environment has access to it. However, additional application users must be explicitly granted access. To grant access, you need to add users and assign the appropriate roles to them in the Human Resources environment. The global administrator that deployed Human Resources must also launch both Attract and Onboard to complete the initialization and enable access for other tenant users.  Until this happens, other users will not be able to access Attract and Onboard and will get access violation errors. For more information, see [Create new users](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/create-new-users) and [Assign users to security roles](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/assign-users-security-roles). 
