---
title: Connect finance and operations apps with an existing Microsoft Dataverse instance
description: Learn about how to connect finance and operations apps with an existing Microsoft Dataverse instance, including prerequisites.
author: saurabh-kuchhal
ms.author: sakuchha
ms.topic: how-to
ms.date: 03/16/2026
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-10-13
ms.search.form:
ms.dyn365.ops.version: 10.0.0
ms.custom: sfi-image-nochange
---

# Connect finance and operations apps with an existing Microsoft Dataverse instance

[!include[banner](../includes/banner.md)]

Administrators in Microsoft Dynamics Lifecycle Services find that more capabilities require a connection to Dataverse through Power Platform Integration. However, if you already have a Dataverse instance from other Dynamics 365 apps, you might want to reuse it for this integration. This article explains how to connect your finance and operations apps environment with an existing Dataverse instance to combine them into one logical environment.

This article goes through the following steps:

1. Select **Setup** on the **Power Platform Integration** tab.
1. Set the **Use a different Power Platform environment** option.
1. Confirm that you want to proceed.
1. Wait for provisioning to be completed.

As an example of this scenario, a customer who's live with the Dynamics 365 Field Service application in a Dataverse-based environment through Power Platform admin center wants to connect their new finance and operations apps environment to it. This operation unlocks popular features such as dual-write, virtual entities, and out-of-box business events between the back-office and front-office applications.

## Power Platform connection isn't reversible

Connecting, or linking as it's also referred, a finance and operations apps environment to a Microsoft Dataverse instance isn't reversible.  The integration between the two systems uses the infrastructure, and disconnecting them results in data loss. If you wish to delete the Microsoft Dataverse instance, follow the guidance in [Delete environments when Power Platform Integration is enabled](./environment-lifecycle-delete-env.md).

## Prerequisites

Before you set up the Microsoft Power Platform integration, make sure you have the following prerequisites in place:

- Make sure that at least 1 gigabyte (GB) of Microsoft Power Platform database storage capacity space is available for your tenant. If this space isn't available, the setup fails. To view your capacity, go to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/capacity).
- Validate the governance policy of your tenant in Power Platform admin center. To do this validation, you must have either the **Tenant administrator** role or the **Power Platform administrator** role.

    1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
    1. In the left navigation, select **Settings** to open the **Power Platform settings** page.

    :::image type="content" source="media/ppi-ppac-governance-environmentcreation.png" alt-text="Screenshot of the Power Platform settings page.":::

- For organizations that **don't allow everyone** to create Power Platform environments, the user who sets up the integration in Lifecycle Services must be added to one of the following roles in Microsoft Entra ID. To make this change, you must be assigned to the **Tenant administrator** role.

  - Dynamics 365 Service Admin
  - Power Platform Admin

- The user who sets up the integration in Lifecycle Services must be licensed. Use the Microsoft 365 admin center to apply the **Dynamics 365 Unified Operations Plan** license, the **AX Enterprise** license, or an application-specific license, such as **Dynamics 365 Finance**.

## Step 1: Select Setup on the Power Platform Integration tab

In Lifecycle Services, go to your sandbox or production environment, and select the **Power Platform Integration** FastTab. If the **Setup** button is available on it, you can configure your connection to Dataverse.

:::image type="content" source="media/Scenario1_Step1.png" alt-text="Screenshot of the Power Platform Integration FastTab.":::

A Power Platform environment ID should already be listed on the **Power Platform Integration** FastTab. The specified environment is the "initial Power Platform environment" that's the free placeholder environment created in Power Platform admin center for every sandbox and production environment in Lifecycle Services. There's a one-to-one (1:1) relationship, and it's eventually the migration path to Power Platform admin center.

In this scenario, you already have a Power Platform environment where Field Service is installed. The initial Power Platform environment is disconnected from finance and operations apps and can then be deleted if you want.

## Step 2: Set the Use a different Power Platform environment option

In this step, you connect finance and operations apps with your existing Dataverse instance. To enable this connection, set the **Use a different Power Platform Environment** option to **Yes** in the **Power Platform Integration Setup** dialog box.

:::image type="content" source="media/Scenario2_Step2.png" alt-text="Screenshot of the Power Platform Integration Setup dialog box.":::

### Validations

To bring your own Dataverse instance, Lifecycle Services must perform several validations and confirm that:

- The Power Platform environment geography is the same logical geography where you deployed your finance and operations apps. In this example, you deployed your finance and operations apps to the West US Azure region. This geography equates to the United States Power Platform geography.
- You have System Administrator permissions in Dataverse.
- You have an **Environment Manager** or **Project Owner** role in Lifecycle Services.
- You sign in by using an account from the customer tenant that owns the Lifecycle Services project.
- You have a valid **Dynamics 365 Finance**, **Dynamics 365 Supply Chain Management**, **Dynamics 365 Commerce**, **Dynamics 365 Project Operations**, **Dynamics 365 Human Resources**, **Dynamics 365 Unified Operations Plan**, or **AX Enterprise** license assigned to your account. To view which licenses you assigned, go to [My Accounts](https://myaccount.microsoft.com/), and select the **Subscriptions** tab.

## Step 3: Confirm that you want to proceed

A dialog box appears and indicates that you can't reverse this action. Connecting finance and operations apps with Microsoft Power Platform and Dataverse is similar to applying a Microsoft platform update to your environment. After you connect it, you can't undo it.

Enter your name in the dialog box to proceed with the setup activity.

:::image type="content" source="media/Scenario1_Step3.png" alt-text="Screenshot of the Setup Power Platform Integration - This can't be reversed dialog box.":::

## Step 4: Wait for provisioning to be completed

There's a brief downtime in the finance and operations apps environment, so that the X++ runtime can detect its connection to Dataverse for various features. During this time, the system might install any required finance and operations platform applications that weren't previously installed on your Dataverse instance.

## Recommendations

- When you use an existing Dataverse instance and link it to the finance and operations apps environment, don't delete the disconnected Power Platform environment that the system creates during the finance and operations environment creation process. You need to delete the disconnected Power Platform environment manually.
- If you keep the Power Platform environment, remember that it doesn't have a Dataverse instance. You can't use Dataverse capabilities and features such as the Export to Data Lake add-in, dual-write, and virtual tables.
