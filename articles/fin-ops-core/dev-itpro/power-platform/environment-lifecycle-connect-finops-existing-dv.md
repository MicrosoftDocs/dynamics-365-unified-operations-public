---
# required metadata

title: Connect finance and operations apps with an existing Microsoft Dataverse instance
description: This article explains how to connect finance and operations apps with an existing Microsoft Dataverse instance.
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

Administrators in Microsoft Dynamics Lifecycle Services are finding that more capabilities require a connection to Dataverse via Power Platform Integration. However, if a Dataverse instance is already available from other Dynamics 365 apps, you might want to reuse it for this integration. This article explains how to connect your finance and operations apps environment with an existing Dataverse instance to combine them into one logical environment.

This article goes through the following steps.

1. Select **Setup** on the **Power Platform Integration** tab.
2. Set the **Use a different Power Platform environment** option.
3. Confirm that you want to proceed.
4. Wait for provisioning to be completed.

As an example of this scenario, a customer who has already gone live with the Dynamics 365 Field Service application in a Dataverse-based environment through Power Platform admin center wants to connect their new finance and operations apps environment to it. This operation unlocks popular features such as dual-write, virtual entities, and out-of-box business events between the back-office and front-office applications.

## Prerequisites

The following prerequisites must be in place before you set up the Microsoft Power Platform integration:

- Make sure that at least 1 gigabyte (GB) of Microsoft Power Platform database storage capacity space is available for your tenant. If this space isn't available, the setup will fail. To view your capacity, go to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/capacity).
- Validate the governance policy of your tenant in Power Platform admin center. To do this validation, you must have either the **Global administrator** role or the **Power Platform administrator** role.

    1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
    2. In the left navigation, select **Settings** to open the **Power Platform settings** page.

    :::image type="content" source="media/ppi-ppac-governance-environmentcreation.png" alt-text="Screenshot of the Power Platform settings page.":::

- For organizations that **don't allow everyone** to create Power Platform environments, the user who does the setup in Lifecycle Services must be added to one of the following roles in Azure Active Directory (Azure AD). To make this change, you must be assigned to the **Global administrator** role.

    - Dynamics 365 Service Admin
    - Power Platform Admin

- The user who does the setup in Lifecycle Services must be licensed. The Microsoft 365 admin center should be used to apply the **Dynamics 365 Unified Operations Plan** license, the **AX Enterprise** license, or an application-specific license, such as **Dynamics 365 Finance**.

## Step 1: Select Setup on the Power Platform Integration tab

In Lifecycle Services, go to your sandbox or production environment, and select the **Power Platform Integration** FastTab. If the **Setup** button is available on it, you can configure your connection to Dataverse.

:::image type="content" source="media/Scenario1_Step1.png" alt-text="Screenshot of the Power Platform Integration FastTab.":::

A Power Platform environment ID should already be listed on the **Power Platform Integration** FastTab. The specified environment is the "initial Power Platform environment," which is the free placeholder environment that's created in Power Platform admin center for every sandbox and production environment in Lifecycle Services. There's a one-to-one (1:1) relationship, and it will eventually be the migration path to Power Platform admin center.

In this scenario, you already have a Power Platform environment where Field Service is installed. The Initial Power Platform environment will be disconnected from finance and operations apps and can then be deleted if you want.

## Step 2: Set the Use a different Power Platform environment option

In this step, you connect finance and operations apps with your existing Dataverse instance. To enable this connection, be sure to set the **Use a different Power Platform Environment** option to **Yes** in the **Power Platform Integration Setup** dialog box.

:::image type="content" source="media/Scenario2_Step2.png" alt-text="Screenshot of the Power Platform Integration Setup dialog box.":::

### Validations

To bring your own Dataverse instance, you must pass several validations that Lifecycle Services performs:

- The Power Platform environment geography must be the same logical geography where your finance and operations apps are deployed. In this example, your finance and operations apps are deployed to the West US Azure region. This geography equates to the United States Power Platform geography.
- You must have System Administrator permissions in Dataverse.
- You must have an **Environment Manager** or **Project Owner** role in Lifecycle Services.
- You must be signed in by using an account from the customer tenant that owns the Lifecycle Services project.
- A valid **Dynamics 365 Finance**, **Dynamics 365 Supply Chain Management**, **Dynamics 365 Commerce**, **Dynamics 365 Project Operations**, **Dynamics 365 Human Resources**, **Dynamics 365 Unified Operations Plan**, or **AX Enterprise** license must be assigned to your account. To view which licenses you've assigned, go to [My Accounts](https://myaccount.microsoft.com/), and select the **Subscriptions** tab.

## Step 3: Confirm that you want to proceed

A dialog box appears and indicates that the action can't be reversed. The action of connecting finance and operations apps with Microsoft Power Platform and Dataverse is similar in nature to the action of applying a Microsoft platform update to your environment. After it's done, it can't be undone.

Enter your name in the dialog box to proceed with the setup activity.

:::image type="content" source="media/Scenario1_Step3.png" alt-text="Screenshot of the Setup Power Platform Integration - This cannot be reversed dialog box.":::

## Step 4: Wait for provisioning to be completed

There's a brief downtime in the finance and operations apps environment, so that the X++ runtime can detect its connection to Dataverse for various features. During this time, any finance and operations platform applications that are required, but that weren't previously installed, might be installed on your Dataverse instance.

## Recommendations

* Because you're using an existing Dataverse instance and linking with the finance and operations apps environment, it's important that you remember the disconnected Power Platform environment that was created while the finance and operations environment was created.
* If you plan to keep the Power Platform environment, note that there isn't a Dataverse instance on it, and you can't use Dataverse capabilities and features such as the Export to Data Lake Add-In, dual-write, and virtual tables.
