---
# required metadata

title: Connect Finance and Operations apps with an existing Microsoft Dataverse instance
description: Connect Finance and Operations apps with an existing Microsoft Dataverse instance 
ms.author: sakcuhha
author: saurabh-kuchhal
ms.date: 02/24/2023
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.search.region: Global
# ms.search.industry:
ms.search.validFrom: 2021-10-13
ms.dyn365.ops.version: 10.0.0
---
# Connect Finance and Operations apps with an existing Microsoft Dataverse instance

[!include[banner](../includes/banner.md)]

Administrators in Lifecycle Services are finding more and more capabilities require connection to Microsoft Dataverse via Power Platform Integration.  In some cases however, you may already have a Microsoft Dataverse instance available with other Dynamics 365 apps that you wish to re-use for this integration.  This scenario will walk you through connecting your Finance and Operations apps environment with an existing Microsoft Dataverse instance to combine them as one logical enviornment.

In this scenario, you will learn how to:

> [!div class="checklist"]
> * Step 1: Click setup from the Power Platform Integration tab
> * Step 2: Use a different Power Platform environment
> * Step 3: Confirm you wish to proceed
> * Step 4: Provisioning in progress

As an example of this scenario, a customer who has already gone live with Dynamics 365 Field Service application on a Microsoft Dataverse based environment Power Platform admin center (PPAC) wishes to now connect their new Finance and Operations apps environment to it.  This will unlock popular features such as Dual-write, Virtual entities, and Business events out of the box between the back-office and front-office applications.

## Preqrequisites
The following list describes the prerequisites for setting up the Microsoft Power Platform integration.

- Make sure that at least 1 GB of Microsoft Power Platform database storage capacity space is available for your tenant. If this space isn't available, the setup will fail. View your capacity in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/capacity). 

- Validate the governance policy of your tenant in Power Platform admin center. To do this validation, you must have either the **Global administrator** role or the **Power Platform administrator** role.

    1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
    2. Select **Settings** in the left navigation to open the **Power Platform settings** page.

        ![Screenshot of the Power Platform settings pane.](media/ppi-ppac-governance-environmentcreation.png)

- For organizations that **don't allow everyone** to create Microsoft Power Platform environments, the user who does the setup in Lifecycle Services must be added to one of the following roles in Azure Active Directory (Azure AD). To make this change, you must be assigned to the **Global administrator** role.

    - Dynamics 365 Service Admin
    - Power Platform Admin

-The user who does the setup in Lifecycle Services must be licensed. The Microsoft 365 admin center should be used to apply the **Dynamics 365 Unified Operations Plan** license, the **AX Enterprise** license, or an application-specific license, such as **Dynamics 365 Finance**.

## Step 1: Click setup from the Power Platform Integration tab
In Lifecycle Services, visit your sandbox or Production environment and locate the "Power Platform Integration" tab.  You should see that the **Setup** button is available which means that you can configure your connection to Microsoft Dataverse. 

<img src="media/Scenario1_Step1.png" width="600px" alt="Setup button for enablign Power Platform Integration" />

Note that there is already a Power Platform Environment Id listed here.  This is referred to as the "Initial Power Platform Environment" and is the free placeholder environment created in Power Platform admin center for every sandbox and Production environment in Lifecycle Services.  This is a one to one relationship, and will be the eventual migration path to Power Platform admin center in the future.

In this scenario, we already have a Power Platform environment with Dynamics 365 Field Service installed.  The Initial Power Platform environment shown above will be disconnected from Finance and Operations apps and will be able to be deleted if you so choose.

## Step 2: Use a different Power Platform environment
In this step, we will connect Finance and Operations apps with your existing Dataverse instance.  To do this, in the slider window be sure to select to **use a different Power Platform Environment**.  

### Validations
To bring your own Dataverse instance you will need to adhere to several validations that are performed by Lifecycle Services:
* The Power Platform environment geo must be the same logical geo as where Finance and Operations apps are deployed.  Example is that your Finance and Operations apps are deployed to West US Azure Region.  This equates to a Power Platform geography of United States.  
* You must have System Administrator permissions in Dataverse
* You must be an Environment Manager or a Project Owner role in Lifecycle Services
* You must be logged in as an account from the customer tenant who owns the Lifecycle Services project
* You must have a valid Finance, Supply Chain Management, Commerce, Project Operations, Human Resources, Unified Operations Plan, or AX Enterprise license assigned to your account.  To see which licenses you have assigned visit https://myaccount.microsoft.com/ and look at the Subscriptions tab. 

<img src="media/Scenario2_Step2.png" width="600px" alt="Setup button for enablign Power Platform Integration" />

## Step 3: Confirm you wish to proceed
You will now be presented with a dialog window indicating that this **action cannot be reversed**.  Connecting Finance and Operations apps with Power Platform and Microsoft Dataverse is similar in nature to applying a Microsoft Platform update on your enviornment.  Once it is applied, it cannot be unapplied.

Type your name in the dialog window to proceed with the setup activity:

<img src="media/Scenario1_Step3.png" width="600px" alt="Setup button for enablign Power Platform Integration" />

## Step 4: Provisioning in progress
There will be a brief downtime on the Finance and Operations apps environment so that the X++ runtime is made aware of its connection to Dataverse for various different features.

During this time, some platform applications may be installed on your Dataverse instance that are required by Finance and Operations apps, if they were not previously installed manually.  


## Recommendations

* Since you are using existing Dataverse instance and linking with the Finance and Operations environment, its important to not forget about the disconnected Power Platform environment which was created while the Finance and Operations environment was created.
* If you plan to keep Power Platform environment, please note that there is no Dataverse instance on this Environment, and cannot use Dataverse capabilities and features such as Export to Data Lake Add-In, dual-write, virtual tables.
