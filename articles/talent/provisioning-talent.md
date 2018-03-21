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
2. Talent is always provisioned into a Microsoft PowerApps environment, to enable PowerApps integration and extensibility. Read the “Selecting a PowerApps environment” section of this topic before you continue. 
3. If you don't already have a PowerApps environment, follow the steps in the "Create a new PowerApps environment (if required)" section of this topic before you continue.

    > [!NOTE]
    > To view existing environments or create new environments, the tenant admin who provisions Talent must be assigned to the PowerApps P2 license. If your organization doesn't have a PowerApps P2 license, you can get one from your CSP or from the [PowerApps pricing page](https://powerapps.microsoft.com/en-us/pricing/).

4. Select **Add**, and then select the environment to provision Talent into.
5. Select **Yes** to agree to the terms and begin deployment.

    Your new environment appears in the list of environments in the navigation pane on the left. However, you can't start to use the environment until the deployment status is updated to **Deployed**. This process typically takes just a few minutes. If the provisioning process is unsuccessful, you must contact Support.

6. Select **Log on to Talent** to use your new environment.

> [!NOTE]
> If you haven't yet signed off on the final requirements, you can deploy a test instance of Talent in the project. You can then use this instance to test your solution until you sign off. If you use your new environment for testing, you must repeat this procedure to create a production environment.

> [!NOTE]
> Talent environments that are provisioned through LCS don't contain demo data that is configured for Human resources (HR) tasks, or that is specific to Talent. If you require an environment that contains demo data, we recommend that you sign up for a free 60-day [Talent trial environment](https://dynamics.microsoft.com/en-us/talent/overview/). Although a trial environment is owned by the user who requested it, other users can be invited through the system administration experience for Core HR. Trial environments contain fictitious data that can be used to explore the program in a safe manner. They aren't intended to be used as production environments. Note that when the trial environment expires after 60 days, all the data in it is deleted and can't be recovered. You can sign up for a new trial environment after the existing environment expires.

## Select a PowerApps environment

The integration between Talent and the PowerApps environments lets you integrate and extend the use of Talent data using PowerApps tools. Understanding the purpose of PowerApps environments will not only help you build apps to extend Talent, but also can also help you select the correct environment when provisioning Talent. For information about PowerApps environments, including environment scope, environment access, and creating and choosing an environment, see [Announcing PowerApps environments](https://powerapps.microsoft.com/en-us/blog/powerapps-environments/). 

Use the following guidance when determining which PowerApps environment to deploy Talent into: 
 > 1.	In LCS, select Manage environments, or navigate directly to the PowerApps Admin center , where you can view existing environments and create new environments.
 > 2.	A single Talent environment is mapped to a single PowerApps environment.
 > 3.	A PowerApps environment “contains” the Talent application, along with the corresponding PowerApps, Flow, and CDS applications. If the PowerApps environment is deleted, so are the apps within it.
 > 4.	Data integration and testing strategies should be considered, for example: Sandbox, UAT, Production. Therefore, we recommend that you consider the various implications for your deployment, because it isn't easy to change which Talent environment is mapped to a PowerApps environment later.
 > 5.	The following PowerApps environments cannot be used for Talent and will be filtered from the selection list within LCS:
 
   a.	**CDS 2.0 Environments** - CDS 2.0 will be made publicly available on March 21, 2018; however, Talent does not yet support CDS 2.0. Though you can view and create CDS 2.0 databases in the PowerApps Admin center, they will not be usable in Talent. The option to use CDS 2.0 Environments in Talent deployments will be available at a later date.
   
 >[!Note]
 >You can't easily determine the difference between CDS 1.0 and CDS 2.0 environments in the administration portal. Environments with a created date on or after March 21, 2018 (3/21/2018) are likely CDS 2.0 environments.
 
   b.	**Default Power Apps environments** - Although each tenant is automatically provisioned with a default PowerApps environment, we don't recommend using them with Talent since all tenant users have access to the PowerApps environment and may unintentionally corrupt production data when testing and exploring with PowerApps or Flow integrations.
   
   c.	**Test Drive environments** - Environments with a name like ‘TestDrive – alias@domain’ are created with a 60-day expiration period and will expire after that time, causing your environment to be removed automatically.
   
   d.	**Unsupported regions** – Currently Talent is only supported in the following regions: United States, Europe, or Australia.
   
 > 6.	There is no specific action to take once you have determined the correct environment to use. Continue with the provisioning process.

## Create a new PowerApps environment (if required)

Run a PowerShell script to create a new PowerApps environment for Talent in the context of the tenant admin that has the PowerApps Plan 2 license. The script automates the following steps:

> + Creation of a PowerApps environment
> + Creation of a CDS 1.0 database
> + Clear all sample data in the CDS 1.0 database

Complete the following instructions to run the script:

> 1. Download the ProvisionCDSEnvironment.zip file from the following location: [ProvisionCDSEnvironment scripts](https://go.microsoft.com/fwlink/?linkid=870436)  
> 2. Unzip the entire contents of the ProvisionCDSEnviroinment.zip file into a folder.
> 3. Run the Windows PowerShell or Windows PowerShell ISE program as the administrator.

 > Visit the [Set Execution Policy](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6) topic to learn more about setting the execution policy so that scripts can be run.
 
> 4. Within PowerShell, navigate to the folder where you unzipped the file and run the following command, replacing values as directed in the note below:
  
  > .\ProvisionCDSEnvironment -EnvironmentName MyNewEnvironment -Location YourLocation [-Verbose]

Note the following when creating a new PowerApps environment: 
 
> **EnvironmentName** should be replaced with your environment name. This name will appear in LCS and will be visible when users select which Talent environment to use. 

> **YourLocation** should be replaced with one of the supported regions for Talent: unitedsates, europe, australia. 

> **-Verbose** is optional and will provide detailed information to send to support if problems are encountered.


> 5. Continue with the provisioning process. 
 


## Grant access to the environment
By default, the global administrator who created the environment has access to it. However, additional application users must be explicitly granted access. To grant access, you [add users](../dev-itpro/sysadmin/tasks/create-new-users.md) and [assign the appropriate roles to them](../dev-itpro/sysadmin/tasks/assign-users-security-roles.md) in the Core HR environment. You must also add those users to the PowerApps environment, so that they can access the Attract and Onboard applications. The procedure is outlined here. If you require help to complete the steps, see the [Introducing the PowerApps admin center](https://powerapps.microsoft.com/en-us/blog/introducing-admin-center-for-powerapps/) blog post.

This procedure is completed by the global administrator who deployed the Talent environment.

1. Open the [PowerApps Admin center](https://preview.admin.powerapps.com/environments).
2. Select the appropriate environments.
3. On the **Security** tab, add the required users to the **Environment Maker** role.

Note that this final step, where you manually add users to the PowerApps environment, is temporary. Eventually, it will be completed automatically when users are added in Core HR.
