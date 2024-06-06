---
title: Set up developer cloud-hosted environments by using Power Platform Integration
description: Learna bout how to setup finance and operations developer cloud-hosted environments by using Microsoft Power Platform Integration.
author: abunduc-ms
ms.author: abunduc
ms.topic: conceptual
ms.date: 06/02/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Set up developer cloud-hosted environments by using Power Platform Integration

Finance and operations apps have a rich development experience, as described in [Develop and customize home page](/dynamics365/fin-ops-core/dev-itpro/dev-tools/developer-home-page). As part of this experience, cloud development environments can be provisioned in your Microsoft Dynamics Lifecycle Services project. Cloud development environments are virtual machines (VMs) that a developer connects to by using Remote Desktop access. The developer can then develop code through the Microsoft Visual Studio environment.

This article highlights the steps to enable Power Platform Integration. For information about the configuration steps for cloud-hosted environments, see [Deploy and access development environments](/dynamics365/fin-ops-core/dev-itpro/dev-tools/access-instances).

## Enable Power Platform Integration

Because of the architecture differences between cloud-hosted development environments and the sandbox or production environments, Power Platform Integration can't be set up after the developer environment is created. Therefore, you can set up Power Platform Integration only during the deployment of your cloud-hosted environment. In addition, you can connect a new cloud-hosted environment only with a new Microsoft Power Platform environment. You can't connect an existing environment of any type via Lifecycle Services.

> [!NOTE]
> Lifecycle Services add-ins can't be installed on cloud-hosted environments. They're applicable only to sandbox and production environments.

To enable Power Platform integration, follow these steps.

1. During deployment of a cloud-hosted environment, select **Advanced settings** to access the Power Platform Integration setup.
   :::image type="content" source="media/ppi-dev-advanced-settings.png" alt-text="Screenshot that shows the button used to access advanced settings for development environments." lightbox="media/ppi-dev-advanced-settings.png":::
1. On the **Deployment settings** page, on the **Power Platform Integration** tab, change the setting of the **Configure Power Platform Environment** option from *No* to *Yes*.
   :::image type="content" source="media/ppi-dev-enable-ppi.png" alt-text="Screenshot that shows the option used to enable Power Platform Integration." lightbox="media/ppi-dev-enable-ppi.png":::
1. After Power Platform Integration is enabled, select the correct [template](environment-lifecycle-connect-finops-new-dv.md#step-2-configure-dataverse-by-using-a-template) and environment type, and then select the *Agree* checkbox.
   :::image type="content" source="media/ppi-dev-configure-ppi.png" alt-text="Screenshot that shows the fields used to configure Power Platform Integration." lightbox="media/ppi-dev-configure-ppi.png":::
1. After the previous steps are completed, and the cloud-hosted environment is created, a paired Dataverse environment is deployed.
1. (Optional): Finalize the setup in Lifecycle Services. Depending on your requirements (for example, if dual-write is required), you must follow more steps on the environment page in Lifecycle Services. For more information, see [Dual-write setup from Lifecycle Services](../data-entities/dual-write/lcs-setup.md).

## Recommendations

- If Power Platform Integration isn't enabled in your cloud-hosted environment, and you're using dual-write instead, you're working on an old setup that's no longer supported. Deploy a new development environment where Power Platform Integration is enabled.
