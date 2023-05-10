---
# required metadata

title: Connect finance and operations apps with an existing Microsoft Dataverse instance
description: This article explains how to connect finance and operations apps with an existing Microsoft Dataverse instance 
ms.author: sakuchha
author: saurabh-kuchhal
ms.date: 05/02/2023
ms.topic: how-to
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.search.region: Global
# ms.search.industry:
ms.search.validFrom: 2021-10-13
ms.dyn365.ops.version: 10.0.0
---
# Connect finance and operations apps with an existing Microsoft Dataverse instance

[!include[banner](../includes/banner.md)]

Administrators in Microsoft Lifecycle Services are finding that more capabilities require connection to Microsoft Dataverse via Microsoft Power Platform Integration.  However, if you already have a Dataverse instance available from other Microsoft Dynamics 365 apps, you may want to reuse it for this integration. This article shows you how to connect your finance and operations apps environment with an existing Dataverse instance to combine them as one logical environment.

You'll learn how to:

* Step 1: From the **Power Platform Integration** tab, select **Setup**.
* Step 2: Use a different Power Platform environment.
* Step 3: Confirm you wish to proceed.
* Step 4: Provisioning in progress.

As an example of this scenario, a customer who has already gone live with the Microsoft Dynamics 365 Field Service application on a Microsoft Dataverse-based environment Power Platform admin center (PPAC) wants to connect their new finance and operations apps environment to it. This operation unlocks popular features, such as, Dual-write, Virtual entities, and Business events out of the box between the back-office and front-office applications.

## Prerequisites

The following list describes the prerequisites for setting up the Power Platform integration.

- Make sure that at least 1 GB of Microsoft Power Platform database storage capacity space is available for your tenant. If this space isn't available, the setup fails. To view your capacity, see the [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/capacity). 
- Validate the governance policy of your tenant in Power Platform admin center. To do this validation, you must have either the **Global administrator** role or the **Power Platform administrator** role.
    1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
    2. From the left navigation, select **Settings** to open the **Power Platform settings** page.
    
       :::image type="content" source="media/ppi-ppac-governance-environmentcreation.png" alt-text="Screenshot of the Power Platform settings pane."::: 

- For organizations that **don't allow everyone** to create Microsoft Power Platform environments, the user who does the setup in Lifecycle Services must be added to one of the following roles in Microsoft Azure Active Directory (Azure AD). To make this change, you must be assigned to the **Global administrator** role.

    - Dynamics 365 Service Admin
    - Power Platform Admin

- The user who does the setup in Lifecycle Services must be licensed. The Microsoft 365 admin center should be used to apply the **Dynamics 365 Unified Operations Plan** license, the **AX Enterprise** license, or an application-specific license, such as **Dynamics 365 Finance**.

## Step 1: From the Power Platform Integration tab, select Setup

In Lifecycle Services, visit your sandbox or Production environment and locate the "Power Platform Integration" tab. You should see that the **Setup** button is available, which means that you can configure your connection to Microsoft Dataverse. 

:::image type="content" source="media/Scenario1_Step1.png" alt-text="A screenshot of the Power Platform Integration page."::: 

There's already a Power Platform Environment ID listed here. This is the "Initial Power Platform Environment," and it's the free placeholder environment that's created in Power Platform admin center for every sandbox and Production environment in Lifecycle Services. There's a one-to-one relationship and it will be the eventual migration path to Power Platform admin center in the future.

In this scenario, we already have a Power Platform environment with Dynamics 365 Field Service installed. The Initial Power Platform environment shown above will be disconnected from finance and operations apps and will be able to be deleted if you choose.

## Step 2: Use a different Power Platform environment

In this step, we connect finance and operations apps with your existing Dataverse instance. To enable this connection, in the slider window be sure to select to **use a different Power Platform Environment**.  

### Validations

To bring your own Dataverse instance you need to adhere to several validations that are performed by Lifecycle Services:

- The Power Platform environment geography must be the same logical geography where your finance and operations apps are deployed. In this example, your finance and operations apps are deployed to West US Azure Region. This geography equates to the Power Platform geography of the United States.  
- You must have System Administrator permissions in Dataverse.
- You must have an Environment Manager or a Project Owner role in Lifecycle Services.
- You must be logged in with an account from the customer tenant who owns the Lifecycle Services project.
- You must have a valid Finance, Supply Chain Management, Commerce, Project Operations, Human Resources, Unified Operations Plan, or AX Enterprise license assigned to your account. To see which licenses you have assigned, see [My Accounts](https://myaccount.microsoft.com/), and select the **Subscriptions** tab. 

:::image type="content" source="media/Scenario2_Step2.png" alt-text="A screenshot of the Power Platform Integration Setup page."::: 

## Step 3: Confirm you wish to proceed

You are presented with a dialog box indicating that this **action cannot be reversed**. Connecting finance and operations apps with Power Platform and Microsoft Dataverse is similar in nature to applying a Microsoft Platform update on your environment. Once it's applied, it can't be unapplied.

Type your name in the dialog window to proceed with the setup activity.

:::image type="content" source="media/Scenario1_Step3.png" alt-text="A screenshot of the Setup Power Platform Integration - This cannot be reversed dialog box."::: 

## Step 4: Provisioning in progress

There's a brief downtime on the finance and operations apps environment so that the X++ runtime is made aware of its connection to Dataverse for various features.

During this time, any finance and operations platform applications that are required, but weren't previously installed, may be installed on your Dataverse instance.  

## Recommendations

* Because you're using existing Dataverse instance and linking with the finance and operations environment, it's important to not forget about the disconnected Power Platform environment, which was created while the finance and operations environment was created.
* If you plan to keep Power Platform environment, please note that there isn't a Dataverse instance on this Environment, and can't use Dataverse capabilities and features such as Export to Data Lake Add-In, dual-write, virtual tables.
