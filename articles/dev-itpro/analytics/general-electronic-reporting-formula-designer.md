---
# required metadata

title: Provision Microsoft Dynamics 365 for Talent
description: This topic walks you through the process of provisioning a new environment for Microsoft Dynamics 365 for Talent. 
author: rschloma
manager: AnnBe
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: Talent
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

    1. Sign in to [PowerApps](https://preview.web.powerapps.com/home), and go to the environment that you created in step 2.
    2. Select **Entities**. On the right side of the page, select the ellipse (**…**) button, and then select **Clear all data**.
    3. Select **Delete data** to confirm that you want to remove the data. This action removes all the demo data that is included in the CDS by default. It also removes any other data that has been entered in the selected database.

You can now use your new environment.
