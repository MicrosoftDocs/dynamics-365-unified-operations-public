---
title: Setup developer cloud-hosted environments with Power Platform Integration
description: This article explains how to setup finance and operations developer cloud hosted environments with Power Platform Integration
author: abunduc-ms
ms.author: abunduc
ms.date: 06/02/2023
ms.topic: conceptual
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Setup developer cloud-hosted environments with Power Platform Integration

Finance and operations apps have a rich development experience, as described in [Develop and customize home page](/dynamics365/fin-ops-core/dev-itpro/dev-tools/developer-home-page). As part of this experience, cloud development environments can be provisioned in your Lifecycle Services project. They're virtual machines to which a developer connects with Remote Desktop access to develop code through the Microsoft Visual Studio environment.

This article highlights the steps to enable the Power Platform integration. For information about the configuration steps for cloud hosted environments, see [Deploy and access development environments](/dynamics365/fin-ops-core/dev-itpro/dev-tools/access-instances). 

## Enable Power Platform integration

Because of the architecture differences between cloud-hosted development environments and the sandbox or production environments, Microsoft Power Platform Integration can't be set up after the developer environment is created. Therefore, you can set up Power Platform Integration only during the deployment of your cloud-hosted environment. In addition, you can connect a new cloud-hosted environment only with a new Power Platform environment. You can't connect an existing environment of any type via Lifecycle Services.

> [!NOTE]
> Lifecycle Services add-ins can't be installed on cloud-hosted environments. They're applicable only to sandbox and production environments.

### Step 1: Access Advanced Settings

During deployment of a cloud-hosted environment, go to **Advanced settings** to access the Power Platform Integration setup.

:::image type="content" source="media/ppi-dev-advanced-settings.png" alt-text="Screenshot of Access Advanced settings for development environments." lightbox="media/ppi-dev-advanced-settings.png":::

### Step 2: Enable the Power Platform Integration

On Deployment settings, navigate to the **Power Platform Integration** tab. On **Configure Power Platform Environment**, toggle the flag from *No* to *Yes*.

:::image type="content" source="media/ppi-dev-enable-ppi.png" alt-text="Screenshot of Enable Power Platform integration." lightbox="media/ppi-dev-enable-ppi.png":::

### Step 3: Configure the Power Platform Integration

Once the Power Platform Integration is enabled, choose the correct [template](environment-lifecycle-connect-finops-new-dv.md#step-2-configure-dataverse-by-using-a-template) and environment type, and then check *Agree*.

:::image type="content" source="media/ppi-dev-configure-ppi.png" alt-text="Screenshot of Configure Power Platform integration." lightbox="media/ppi-dev-configure-ppi.png":::

### Step 4: Deploy the environment

After all the steps are completed, when the cloud-hosted environment is created, a paired Dataverse environment is deployed.

### Step 5: [Optional] Finalize the setup in Lifecycle Services

Depending on your requirements (for example, if dual write is required), more steps have to be followed in Lifecycle Services, in the environment page. <!--TODO add link to dual write-->

## Recommendations

- If your cloud-hosted environment doesn't have Power Platform integration enabled, but you're using dual-write, you're working on an old setup that isn't supported anymore. Deploy a new development environment with Power Platform integration enabled.
