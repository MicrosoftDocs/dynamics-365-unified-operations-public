---
title: Create deployable packages of models
description: This article describes the workflow for creating and applying a deployable package.
author: gianugo
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Create deployable packages of models

[!include [banner](../includes/banner.md)]

An AOT package is a deployment and compilation unit of one or more models that can be applied to an environment. It includes model metadata, binaries, reports and other associated resources. One or more AOT packages can be packaged into a deployable package, which is the vehicle used for deployment of code (and customizations) on demo, sandbox, and production environments. This article guides you through the process of creating and applying a deployable package. 

## Overview of the process

In order to deploy your code and customizations to a runtime environment (demo, sandbox, or production), you must create deployable packages of your solution or implementation. Deployable packages can be created by using **Visual Studio dev tools** or by using the **build automation process** that is available on build environments. These deployable packages are referred to as Application Deployable Packages or AOT Deployable Packages. The following image shows an overview of the process. After a deployable package is created, it must be uploaded to the Lifecycle Services (LCS) project's asset library. An administrator can then go to the LCS environment page and apply the package to a runtime environment using the **Maintain &gt; Apply updates** tool. 

> [!NOTE]
> Custom payment connector for Commerce needs to be packaged using a combined AOT deployable package. For more information, see [Create payment packaging for Application Explorer in Service Fabric deployments](../../../commerce/dev-itpro/payment-connector-package.md).

![Create and apply a deployment package.](./media/createandapplydeployablepackage.png)

> [!NOTE]
> Application Deployable Packages do not contain source code.

> It is always recommended to use a build environment to create deployable packages that are intended to go to production.

## Create a deployable package
We recommend using a build environment to create deployable packages. You can also create a deployable package on a development environment. 

On a development environment, after you have completed development and testing, follow these steps to create a deployable package in Visual Studio.

1.  In Microsoft Visual Studio, select **Dynamics 365** &gt; **Deploy** &gt; **Create Deployment Package**.
![Create deployment package.](./media/createdeploymentpackage-986x1024.png)

2.  Select the packages that contain your models, and then select a location in which to create the deployable package. 
![Select a location.](./media/pack4.png)

3.  After a deployable package is created, sign in to Lifecycle Services, and then, in your LCS project, click the **Asset Library** tile.

4.  Upload the deployable package that you created earlier.

## Apply a deployable package
To apply a deployable package to an environment, see [Apply updates to cloud environments](apply-deployable-package-system.md).

## Remove a deployable package
To uninstall or remove a deployable package from an environment, see [Uninstall a package](uninstall-deployable-package.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
