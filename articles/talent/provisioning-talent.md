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

[!include[banner](includes/banner.md)]

[!include[banner](includes/banner.md)]

This topic walks you through the process of provisioning a new production environment for Microsoft Dynamics 365 for Talent. This topic assumes that you've purchased Talent through a Cloud Solution Provider (CSP) or enterprise architecture (EA) agreement. If you have an existing Microsoft Dynamics 365 license that already includes the Talent service plan, and you can't complete the steps in this topic, contact Support.

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

    Your new environment appears in the list of environments in the navigation pane on the left. However, you can't start to use the environment until the deployment status is updated to **Deployed**. This process typically takes just a few minutes. If the provisioning process is unsuccessful, you must contact Support.

6. Select **Log on to Talent** to use your new environment.

> [!NOTE]
> If you haven't yet signed off on the final requirements, you can deploy a test instance of Talent in the project. You can then use this instance to test your solution until you sign off. If you use your new environment for testing, you must repeat this procedure to create a production environment.

> [!NOTE]
> Talent environments that are provisioned through LCS don't contain demo data that is configured for Human resources (HR) tasks, or that is specific to Talent. If you require an environment that contains demo data, we recommend that you sign up for a free 60-day [Talent trial environment](https://dynamics.microsoft.com/en-us/talent/overview/). Although a trial environment is owned by the user who requested it, other users can be invited through the system administration experience for Core HR. Trial environments contain fictitious data that can be used to explore the program in a safe manner. They aren't intended to be used as production environments. Note that when the trial environment expires after 60 days, all the data in it is deleted and can't be recovered. You can sign up for a new trial environment after the existing environment expires.

## Create a new PowerApps environment (if required)
The integration between Talent and the PowerApps environments lets you integrate and extend the use of Talent data using PowerApps tools. Understanding the purpose of PowerApps environments will help you build apps that meet the needs you have for extending Talent. For information about PowerApps environments, including environment scope, environment access, and creating and choosing an environment, see [Announcing PowerApps environments](https://powerapps.microsoft.com/en-us/blog/powerapps-environments/). While each tenant is automatically provisioned a Default PowerApps environment, that may not be the best environment to use for your Talent deployment. Data integration and testing strategies should be considered during this step, so we recommend that you consider the implications that might impact your deployment as some decisions are not easy to change later. 

Although each tenant is automatically provisioned in a Default PowerApps environment, that environment might not be the best environment for your Talent deployment. Data integration and testing strategies should be considered during this step. Therefore, we recommend that you consider the various implications for your deployment, because it isn't easy to change the PowerApps environment later.

1. In LCS, select **Manage environments**. You're taken to the [PowerApps Admin center](https://preview.admin.powerapps.com/environments), where you can view existing environments and create new environments.
2. Select **New environment**.
3. Enter a unique name for the environment, and select the location to deploy to.

    > [!NOTE]
    > Talent isn't available in all regions. Therefore, be sure to check for availability before you select the location for your environment.

4. When you're asked whether you want to create a database, select **Create database** to create the Common Data Service (CDS) database that must host part of your Talent data. By creating a database, you can also integrate PowerApps applications with Talent.
5. You're asked about the access level to use for the database. We recommend that you select **Restrict access**, because this option prevents Talent users from directly accessing sensitive data by using a PowerApps application.
6. The CDS database that is created contains demo data that adds inactive employees and fictitious addresses, among other information, to your production environment. To remove the demo data, follow these steps after you've finished creating the CDS database:

    > [!IMPORTANT]
    > If you previously created a CDS database and entered any of your company's production data into it, these steps remove **all** the data in the selected database, even your company's production data.

    1. Sign in to [PowerApps](https://preview.web.powerapps.com/home).
    2. In the drop-down list in the upper right, select the environment that you created in step 2.
    3. In the navigation pane on the left, expand **Common Data Service**, and then select **Entities**.
    4. On the right side of the page, select the ellipse (**…**) button, and then select **Clear all data**.
    5. Select **Delete data** to confirm that you want to remove the data. This action removes all the demo data that is included in the CDS by default. It also removes any other data that has been entered in the selected database.

You can now use your new environment.

## Grant access to the environment
By default, the global administrator who created the environment has access to it. However, additional application users must be explicitly granted access. To grant access, you [add users](../dev-itpro/sysadmin/tasks/create-new-users.md) and [assign the appropriate roles to them](../dev-itpro/sysadmin/tasks/assign-users-security-roles.md) in the Core HR environment. You must also add those users to the PowerApps environment, so that they can access the Attract and Onboard applications. The procedure is outlined here. If you require help to complete the steps, see the [Introducing the PowerApps admin center](https://powerapps.microsoft.com/en-us/blog/introducing-admin-center-for-powerapps/) blog post.

This procedure is completed by the global administrator who deployed the Talent environment.

1. Open the [PowerApps Admin center](https://preview.admin.powerapps.com/environments).
2. Select the appropriate environments.
3. On the **Security** tab, add the required users to the **Environment Maker** role.

Note that this final step, where you manually add users to the PowerApps environment, is temporary. Eventually, it will be completed automatically when users are added in Core HR.
