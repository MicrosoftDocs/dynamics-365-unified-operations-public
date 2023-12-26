---
# required metadata

title: Connect finance and operations apps with a new Microsoft Dataverse instance
description: This article explains how to connect finance and operations apps with a new Microsoft Dataverse instance.
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
ms.collection: get-started
ms.search.region: Global
# ms.search.industry:
ms.search.validFrom: 2021-10-13
ms.dyn365.ops.version: 10.0.0
---
# Connect finance and operations apps with a new Microsoft Dataverse instance

[!include[banner](../includes/banner.md)]

Administrators in Microsoft Dynamics Lifecycle Services are finding that more capabilities require connection to Dataverse via Power Platform Integration. Customers who don't already use Dataverse for low-code applications and services, or with other Dynamics 365 apps, can quickly set up and connect an instance. This article explains how to connect your finance and operations apps environment with a new Dataverse instance to combine them into one logical environment.

This article goes through the following steps.

1. Select **Setup** on the **Power Platform Integration** tab.
2. Configure Dataverse by using a template.
3. Confirm that you want to proceed.
4. Wait for provisioning to be completed.

As an example of this scenario, a customer who has deployed a finance and operations apps environment wants to connect it to a new Dataverse environment. This operation unlocks popular features such as add-ins, dual-write, virtual entities, and out-of-box business events, so that the rich finance and operations apps data can be made available for low-code applications and services.

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

## Step 2: Configure Dataverse by using a template

In this step, you add Dataverse to your initial Power Platform environment. To enable this connection, leave the **Use a different Power Platform Environment** option set to **No** in the **Power Platform Integration Setup** dialog box. If you've already deployed a Dataverse instance with other Dynamics 365 applications, and you want to connect to it, see [Connect finance and operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md).

Select an available template. A Dataverse instance will be created, and several applications will be preinstalled, based on your requirements.

The following templates are available:

* **Dynamics 365 standard** – This template enables add-ins, virtual entities, business events, and dual-write platform components, but it doesn't contain any application maps for dual-write. This template is the one that's most often used.
* **Dynamics 365 standard with Dual-write** – This template enables everything from the standard template and installs application maps for dual-write.
* **Project Operations** – This template is a special template for customers who have the **Dynamics 365 Project Operations** license. It preinstalls solutions that are required for Project Operations to run, in addition to enabling and installing everything from the Dynamics 365 standard with Dual-write template.

After you select a template, select the **Agree** checkbox, and then select **Setup**.

## Step 3: Confirm that you want to proceed

A dialog box appears and indicates that the action can't be reversed. The action of connecting finance and operations apps with Microsoft Power Platform and Dataverse is similar in nature to the action of applying a Microsoft platform update to your environment. After it's done, it can't be undone.

Enter your name in the dialog box to proceed with the setup activity.

:::image type="content" source="media/Scenario1_Step3.png" alt-text="Screenshot of the Setup Power Platform Integration - This cannot be reversed dialog box.":::

## Step 4: Wait for provisioning to be completed

Provisioning a new Dataverse instance takes only a few minutes. There's a brief downtime in the finance and operations apps environment, so that the X++ runtime can detect its connection to Dataverse for various features. During this time, the environment in Power Platform admin center appears in a **Preparing** state while Dataverse is added.

## Recommendations

* Because this action can't be reversed, if you already have a Dataverse instance that you want to link with the finance and operations environment, set the **Use a different Power Platform Environment** option to **Yes** in step 2, and see [Connect finance and operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md).
* As you perform environment lifecycle operations such as restoring data, consider the finance and operations environment and Power Platform environment one environment, and maintain the 1:1 mapping.
