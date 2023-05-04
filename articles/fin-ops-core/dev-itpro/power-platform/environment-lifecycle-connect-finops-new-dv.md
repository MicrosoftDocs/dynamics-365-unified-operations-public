---
# required metadata

title: Connect Finance and Operations apps with a new Microsoft Dataverse instance
description: This article explains how to connect finance and operations apps with a new Microsoft Dataverse instance 
ms.author: laswenka
author: laneswenka
ms.date: 05/02/2023
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: johnmichalak
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.search.region: Global
# ms.search.industry:
ms.search.validFrom: 2021-10-13
ms.dyn365.ops.version: 10.0.0
---
# Connect finance and operations apps with a new Microsoft Dataverse instance

[!include[banner](../includes/banner.md)]

Administrators in Microsoft Lifecycle Services are finding more capabilities require connection to Microsoft Dataverse via Power Platform Integration. Customers who don't already use Microsoft Dataverse for low code or with other Microsoft Dynamics 365 apps can quickly get one setup and connected. This article shows you how to connect your finance and operations apps environment with a new Dataverse instance to combine them as one logical environment.

You'll learn how to:

* Step 1: From the **Power Platform Integration** tab, select **Setup**.
* Step 2: Use a different Power Platform environment.
* Step 3: Confirm you wish to proceed.
* Step 4: Provisioning in progress.

As an example of this scenario, a customer who has a finance and operations apps environment deployed wants to connect it to a new Microsoft Dataverse environment. This operation unlocks popular features such as Add-ins, Dual-write, Virtual entities, and Business events out of the box so that the rich finance and operations apps data can be made available for low code applications and services.

## Preqrequisites

The following list describes the prerequisites for setting up the Power Platform integration.

- Make sure that at least 1 GB of Microsoft Power Platform database storage capacity space is available for your tenant. If this space isn't available, the setup will fail. To view your capacity, see the [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/capacity). 
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

There is already a Power Platform Environment Id listed here. This is the "Initial Power Platform Environment," and it's the free placeholder environment that's created in Power Platform admin center for every sandbox and Production environment in Lifecycle Services. There is a one-to-one relationship and it will be the eventual migration path to Power Platform admin center in the future.

In this scenario, we already have a Power Platform environment with Dynamics 365 Field Service installed. The Initial Power Platform environment shown above will be disconnected from finance and operations apps and will be able to be deleted if you choose.

## Step 2: Use a different Power Platform environment

In this step, we'll connect finance and operations apps with your existing Dataverse instance. To enable this connection, in the slider window be sure to select to **use a different Power Platform Environment**.  

## Step 1: From the Power Platform Integration tab, select Setup

In Lifecycle Services, visit your sandbox or Production environment and locate the "Power Platform Integration" tab. You should see that the **Setup** button is available, which means that you can configure your connection to Microsoft Dataverse. 

:::image type="content" source="media/Scenario1_Step1.png" alt-text="A screenshot of the Power Platform Integration page."::: 

There's already a Power Platform Environment Id listed here. This is the "Initial Power Platform Environment," and it's the free placeholder environment that's created in Power Platform admin center for every sandbox and Production environment in Lifecycle Services. This is a one-to-one relationship and will be the eventual migration path to Power Platform admin center in the future.

## Step 2: Configure Microsoft Dataverse using a template

In this step, we will add Microsoft Dataverse to your initial Power Platform environment. To do this, in the slider window **don't** select to use an existing Power Platform Environment. If you already have Microsoft Dataverse deployed with other Dynamics 365 applications and want to connect to it, see [Connect Finance and Operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md).

Select an available template, which will create Microsoft Dataverse with several applications pre-installed based on your requirements.

:::image type="content" source="media/Scenario1_Step2.png" alt-text="Setup button for enabling Power Platform Integration."::: 

The available templates include:

* Dynamics 365 standard - this template enables Add-ins, Virtual entities, Business events, and Dual-write platform components but does not contain any Dual-write application maps.  This is the most common template.
* Dynamics 365 standard with Dual-write - this template enables everything from the standard template and installs application maps for Dual-write.
* Project Operations - this is a special template for customers with the Microsoft Dynamics 365 Project Operations license. This pre-installs solutions required for it to run as well on top of the Dynamics 365 standard with Dual-write template.

After selecting your template, select the **Agree** checkbox and then select the **Setup** button.

## Step 3: Confirm you wish to proceed

You'll now be presented with a dialog box indicating that this **action cannot be reversed**. Connecting finance and operations apps with Power Platform and Microsoft Dataverse is similar in nature to applying a Microsoft Platform update on your environment. Once it's applied, it can't be unapplied.

Type your name in the dialog window to proceed with the setup activity.

:::image type="content" source="media/Scenario1_Step3.png" alt-text="A screenshot of the Setup Power Platform Integration - This cannot be reversed dialog box."::: 

## Step 4: Provisioning in progress
Provisioning a new Dataverse instance only takes a few minutes. There's a brief downtime on the finance and operations apps environment so that the X++ runtime is made aware of its connection to Dataverse for various different features.

During this time, the environment in Power Platform admin center shows in a **Preparing** state while Dataverse is added.  

## Recommendations

* Because this action is irreversible, if you already have a Dataverse instance which you would like to link with finance and operations environment, then mark **Yes** to **Use a different Power Platform Environment** and see [Connect finance and operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md).
* As you perform Environment lifecycle operations such as Restore data, consider finance and operations environment and Power Platform Environment as one, and maintain the 1:1 mapping.
