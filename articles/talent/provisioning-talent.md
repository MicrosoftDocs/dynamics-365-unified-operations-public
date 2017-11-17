---
# required metadata

title: Provisioning Microsoft Dynamics 365 for Talent
description: This topic provides information about how to adapt the user interface to your preferences, as well as connect to the Help resources that are available within the product, and on the docs.microsoft.com site. 
author: rschloma
manager: AnnBe
ms.date: 10/26/2017
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
ms.search.scope: Core, Talent
# ms.tgt_pltfrm: 
ms.custom: 17271
ms.assetid: ba1ad49d-8232-400e-b11f-525423506a3f
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Talent July 2017 update

---
# Provisioning Microsoft Dynamics 365 for Talent
This topic walks through the steps for provisioning a new Microsoft Dynamics 365 for Talent environment. This procedure assumes that you’ve purchased Talent through a Cloud Solution Provider (CSP) or enterprise architecture (EA) agreement. If you own an existing Dynamics 365 license that already includes the Dynamics 365 for Talent service plan and you can’t proceed with the steps below, contact support.
To begin, the global administrator should log into Lifecycle services (LCS) (http://lcs.dynamics.com) and create a new Dynamics 365 for Talent project. Unless a licensing issue prevents you from doing so, provisioning Dynamics 365 for Talent does not require assistance from support or DSE representatives.

## Create an LCS project
To use LCS to manage your Talent environments, you must first create an LCS project. Complete the following steps to create a project.

> 1.	Sign in to https://lcs.dynamics.com/Logon/Index using the account you used to subscribe to Dynamics 365 for Talent.
> 2.	Select the plus sign (+) to create a new project.
> 3.	When choosing the Product name and Product version, select Microsoft Dynamics 365 for Talent.
> 4.	Select the Dynamics 365 for Talent methodology.
> 5.	When finished, click Create.

Refer to the Talent Methodology created within your new project for information on getting started with Dynamics 365 for Talent. After creating the project, follow the next steps to provision your Talent environment.

## Provision a Talent project 
After an LCS project has been created, you can provision Talent into an environment. 

1.	Select Talent App Management tile from your LCS project.
2.	Talent is always provisioned into a PowerApps Environment to enable PowerApps integration and extensibility. If you don’t already have a PowerApps Environment, follow the steps outlined in the section “Creating a new PowerApps Environment” before proceeding with the next step.

>	[!Note]
>The tenant admin provisioning Talent must be assigned to the PowerApps P2 license to view existing environments or create new ones. If your organization does not have a PowerApps P2 license you can acquire one from your CSP or this link: https://powerapps.microsoft.com/en-us/pricing/.

3.	Click Add and select the Environment where you would like to provision Talent.
4.	Click Yes to confirm deployment if you agree to the terms stated.
5.	Your new environment will now appear in the list of environments in the navigation pane on the left, but it is not yet ready to use until the Deployment status changes to Deployed.  This generally takes just a few minutes.  If the provision fails, you need to contact support.
6.	Click Log on to Talent to use your new environment.
 > [!Note]
 > You can deploy a test instance of Talent into this project to use for testing your solution until you’ve signed off on the final requirements. If you use this environment for testing, you will need to repeat this procedure to create a production environment. 

## Creating a new PowerApps Environment (if required)
> 1.	When clicking Manage Environments from LCS, you are taken to the PowerApps Admin Center: https://preview.admin.powerapps.com/environments.  This will allow you to view existing environments and create new ones.
> 2.	Click the (+) New environment button.
> 3.	Enter a unique environment name and choose the location to deploy to. 

 > [!Note]
 > Talent is not available in all regions, so be sure to check for availability before choosing the location of your environment.

> 4.	The message Do you want to create a database will display.  Select Create database to create the Common Data Service (CDS) database that is required to host a portion of your Talent data.  It also provides the ability for PowerApps integrations with Talent.
> 5.	You will be asked about the access level you would like to use for this database. Restrict access is the recommended option to prevent Talent users from direct access to sensitive data via PowerApps.
> 6.	Note that the CDS database contains demo data. While you can use the demo data company for testing, or creating task recordings or task guides, the demo data will add inactive employees and fictitious addresses, among other things, to your production environment. Complete the following steps to remove the demo data. 

 > [!Important]
 > If you created a CDS database previously and have entered any your company’s production data into that database, be aware that the following steps remove all of the data in the selected database, including your company’s production data.
 
> -	After you’ve created the CDS database, log into PowerApps (https://preview.web.powerapps.com/home) and go to the environment that you created in step 3.
> -	Click Entities. On the right side of the page click the ellipse (…) button and select Clear all data. 
> -	Click Delete data to confirm your intention to remove the data. This action removes the demo data that’s included in the CDS by default, as well as any other data that’s been entered in the selected database.
> 7.	Now your environment is ready for use.

