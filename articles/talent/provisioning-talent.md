---
# required metadata

title: Provision Microsoft Dynamics 365 for Talent
description: This topic walks you through the process of provisioning a new environment for Microsoft Dynamics 365 for Talent. 
author: rschloma
manager: AnnBe
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 17271
ms.assetid: ba1ad49d-8232-400e-b11f-525423506a3f
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2017-11-20
ms.dyn365.ops.version: Talent July 2017 update

---
# Provision Microsoft Dynamics 365 for Talent
This topic walks you through the process of provisioning a new environment for Microsoft Dynamics 365 for Talent. This topic assumes that you've purchased Talent through a Cloud Solution Provider (CSP) or enterprise architecture (EA) agreement. If you have an existing Microsoft Dynamics 365 license that already includes the Talent service plan, and you can't complete the steps in this topic, contact Support.

To begin, the global administrator should sign in to [Microsoft Dynamics Lifecycle Services](http://lcs.dynamics.com) (LCS) and create a new Talent project. Unless a licensing issue prevents you from provisioning Talent, assistance from Support or Dynamics Service Engineering (DSE) representatives isn't required.

## Create an LCS project
To use LCS to manage your Talent environments, you must first create an LCS project.

1. Sign in to [LCS](https://lcs.dynamics.com/Logon/Index) by using the account that you used to subscribe to Talent.
2. Select the plus sign (**+**) to create a project.
3. Select **Microsoft Dynamics 365 for Talent** as the product name and product version.
4. Select the **Dynamics 365 for Talent** methodology.
5. Select **Create**.

For information about how to get started with Talent, see the **Talent** methodology that you created in your new project. After you've finished creating the project, complete the following procedure to provision your Talent environment.

## Provision a Talent project
After you've created an LCS project, you can provision Talent into an environment.

1. In your LCS project, select the **Talent App Management** tile.
2. Talent is always provisioned into a Microsoft PowerApps environment, to enable PowerApps integration and extensibility. If you don't already have a PowerApps environment, follow the steps in the "Create a new PowerApps environment (if required)" section of this topic before you continue.

    > [!NOTE]
    > To view existing environments or create new environments, the tenant admin who provisions Talent must be assigned to the PowerApps P2 license. If your organization doesn't have a PowerApps P2 license, you can get one from your CSP or from the [PowerApps pricing page](https://powerapps.microsoft.com/en-us/pricing/).

3. Select **Add**, and then select the environment to provision Talent into.
4. Select **Yes** to agree to the terms and begin deployment.

    Your new environment appears in the list of environments in the navigation pane on the left. However, you can't start to use the environment until the deployment status is updated to **Deployed**. This process typically takes just a few minutes. If provisioning fails, you must contact Support.

6. Select **Log on to Talent** to use your new environment.

> [!NOTE]
> If you haven't yet signed off on the final requirements, you can deploy a test instance of Talent in the project. You can then use this instance to test your solution until you sign off. If you use your new environment for testing, you must repeat this procedure to create a production environment.

## Create a new PowerApps environment (if required)

The vision behind Talent’s integration with PowerApps environments is to enable data integration and extensions flows through the use of PowerApps tools on top of Talent data. As a result, it is important to understand the purpose of PowerApps environments when choosing the environment to use for Talent. For more information about PowerApps environments, including environment scope, environment access, and creating and choosing an environment, see [Announcing PowerApps environments](https://powerapps.microsoft.com/en-us/blog/powerapps-environments/).  While each tenant is automatically provisioned in a Default PowerApps environment, it may not be the best environment to use for your Talent deployment. Data integration and testing strategies should be considered during this step, so we recommend that you consider the various implications for your deployment, since it is not easy to change later.

1. Select **Manage Environments** in LCS. You're taken to the [PowerApps Admin Center](https://preview.admin.powerapps.com/environments), where you can view existing environments and create new environments.
2. Select the (**+**) **New environment** button.
3. Enter a unique name for the environment, and select the location to deploy to.

    > [!NOTE]
    > Talent isn't available in all regions. Therefore, be sure to check for availability before you select the location for your environment.

4. When you're asked whether you want to create a database, select **Create database** to create the Common Data Service (CDS) database that must host part of your Talent data. By creating a database, you can also integrate PowerApps applications with Talent.
5. You're asked about the access level that you want to use for the database. We recommend that you select **Restrict access**, because this option prevents Talent users from directly accessing sensitive data by using a PowerApps application.
6. The CDS database that is created contains demo data. This demo data is useful, because you can use the demo data company for testing, or to create task recordings or task guides. However, the demo data adds inactive employees and fictitious addresses, among other information, to your production environment. To remove the demo data, follow these steps after you've finished creating the CDS database:

    > [!IMPORTANT]
    > If you previously created a CDS database and entered any of your company's production data into it, be aware that these steps remove **all** the data in the selected database, even your company's production data.

    1. Sign in to [PowerApps](https://preview.web.powerapps.com/home), and select the environment that you created in step 2 from the drop-down on the right side of the page.
    2. Expand the **Common Data Service** on the left navigation pane and choose **Entities**.
    3. On the right side of the page, select the ellipse (**…**) button, and then select **Clear all data**.
    4. Select **Delete data** to confirm that you want to remove the data. This action removes all the demo data that is included in the CDS by default. It also removes any other data that has been entered in the selected database.
    
You can now use your new environment.

## Granting access to the environment
The global administrator that created the environment will have access by default, but additional application users must be explicitly granted access. This can be done by [adding users](../dev-itpro/sysadmin/tasks/create-new-users.md) and [assigning them the appropriate roles](../dev-itpro/sysadmin/tasks/assign-users-security-roles.md) within the Core HR environment. In addition to this, it is also necessary to add those users to the PowerApps environment so they can access the Attract and Onboard applications.  The blog post, [Introducing the PowerApps admin center](https://powerapps.microsoft.com/en-us/blog/introducing-admin-center-for-powerapps/) might help you to complete those steps, which are outlined here:

> 1.	The global administrator that deployed the Talent environment should navigate to the [PowerApps Admin center](https://preview.admin.powerapps.com/environments).   
> 2.	Select the environment(s) in question.
> 3.	Under the Security tab, add the necessary users to the “Environment Maker” role.

Note that this final step of adding users to the PowerApps environment is temporary. We will eventually add functionality to enable this automatically when the user is added within Core HR.

