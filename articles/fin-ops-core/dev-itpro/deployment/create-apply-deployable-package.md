---
title: Create deployable packages of models
description: Learn about the workflow for creating and applying a deployable package, including an overview of deployable package creation process.
author: josaw
ms.author: josaw
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Create deployable packages of models

[!include [banner](../includes/banner.md)]

An AOT package is a deployment and compilation unit of one or more models that you can apply to an environment. It includes model metadata, binaries, reports, and other associated resources. You can package one or more AOT packages into a deployable package. Use the deployable package to deploy code and customizations to demo, sandbox, and production environments. This article guides you through the process of creating and applying a deployable package.

## Overview of the process

To deploy your code and customizations to a runtime environment (demo, sandbox, or production), create deployable packages of your solution or implementation. You can create deployable packages by using **Visual Studio dev tools** or by using the **build automation process** that is available on build environments. These deployable packages are referred to as Application Deployable Packages or AOT Deployable Packages. The following image shows an overview of the process. After you create a deployable package, upload it to the Lifecycle Services project's asset library. An administrator can then go to the Lifecycle Services environment page and apply the package to a runtime environment by using the **Maintain &gt; Apply updates** tool.

> [!NOTE]
> You need to package custom payment connector for Commerce by using a combined AOT deployable package. For more information, see [Create payment packaging for Application Explorer in Service Fabric deployments](../../../commerce/dev-itpro/payment-connector-package.md).

:::image type="content" source="./media/createandapplydeployablepackage.png" alt-text="Screenshot of the create and apply a deployment package overview.":::

> [!NOTE]
> Application Deployable Packages don't contain source code.

> [!IMPORTANT]
> Always use a build environment to create deployable packages that you intend to go to production.

## Create a deployable package

Use a build environment to create deployable packages. You can also create a deployable package on a development environment.

On a development environment, after you complete development and testing, follow these steps to create a deployable package in Visual Studio.

1. In Microsoft Visual Studio, select **Dynamics 365** &gt; **Deploy** &gt; **Create Deployment Package**.

   :::image type="content" source="./media/createdeploymentpackage-986x1024.png" alt-text="Screenshot of the Create Deployment Package dialog in Visual Studio.":::

1. Select the packages that contain your models, and then select a location in which to create the deployable package.

   :::image type="content" source="./media/pack4.png" alt-text="Screenshot of the Select a location dialog for creating a deployable package.":::

1. After you create a deployable package, sign in to Lifecycle Services. In your Lifecycle Services project, select the **Asset Library** tile.

1. Upload the deployable package that you created earlier.

## Apply a deployable package

To apply a deployable package to an environment, see [Apply updates to cloud environments](apply-deployable-package-system.md).

## Remove a deployable package

To uninstall or remove a deployable package from an environment, see [Uninstall a package](uninstall-deployable-package.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
