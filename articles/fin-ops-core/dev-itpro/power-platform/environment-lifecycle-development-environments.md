---
title: Setup developer cloud-hosted environments with Power Platform Integration
description: This article explains how to setup finance and operations developer cloud hosted environments with Power Platform Integration
author: abunduc-ms
ms.author: abunduc
ms.date: 06/02/2023
ms.topic: article
---

# Setup developer cloud-hosted environments with Power Platform Integration

Finance and operations apps have a rich development experience, as described in [Develop and customize home page](/dynamics365/fin-ops-core/dev-itpro/dev-tools/developer-home-page). As part of this experience, cloud development environments can be provisioned in your Lifecycle Services (LCS) project. They are virtual machines to which a developer connects with Remote Desktop access to develop code through the Microsoft Visual Studio environment.

Article [Deploy and access development environments](/dynamics365/fin-ops-core/dev-itpro/dev-tools/access-instances) describes in detail the configuration steps for cloud hosted environments. This article highlights the steps to enable the Power Platform integration.

## Enable Power Platform integration

Because of the architecture differences between cloud-hosted development environments and the sandbox or production environments, Power Platform Integration can't be set up after the developer environment is created. Therefore, you can set up Power Platform Integration only during the deployment of your cloud-hosted environment. In addition, you can connect a new cloud-hosted environment only with a new Power Platform environment. You can't connect an existing environment of any type via Lifecycle Services.

> [!NOTE]
> LCS add-ins cannot be installed on cloud-hosted environments, they are applicable only to sandbox and production environments.

### Step 1: Access Advanced Settings

During deployment of a cloud-hosted environment, go to Advanced settings to access the Power Platform integration setup

:::image type="content" source="media/ppi-dev-advanced-settings.png" alt-text="Access Advanced settings for development environments." lightbox="media/ppi-dev-advanced-settings.png":::

### Step 2: Enable the Power Platform Integration

In Deployment settings window, navigate to **Power Platform Integration** tab and toggle the flag from *No* to *Yes* for **Configure Power Platform Environment**.

:::image type="content" source="media/ppi-dev-enable-ppi.png" alt-text="Enable Power Platform integration." lightbox="media/ppi-dev-enable-ppi.png":::

### Step 2: Configure the Power Platform Integration

Once the Power Platform Integration is enabled, choose the correct [template](environment-lifecycle-connect-finops-new-dv#step-2-configure-dataverse-by-using-a-template) and environment type and *Agree*.

:::image type="content" source="media/ppi-dev-configure-ppi.png" alt-text="Configure Power Platform integration." lightbox="media/ppi-dev-configure-ppi.png":::

### Step 4: Deploy the environment

After all the steps above are completed, when the cloud-hosted environment is created, a paired Dataverse environment will be deployed as well.

### Step 5: [Optional] Finalize the setup in LCS

Depending on your requirements (for example, if dual write is required), additional steps need needed to be done in LCS, in the environment page. <!--TODO add link to dual write>

## Recommendations

- If your cloud-hosted environment does not have the Power Platform integration enabled, but you are leveraging dual-write, you are working on an old setup that is not supported anymore. Deploy a new development environment with Power Platform integration enabled.
