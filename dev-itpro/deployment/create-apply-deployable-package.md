---
# required metadata

title: Create a deployable package
description: This topic describes the workflow for creating and applying a deployable package.
author: robadawy
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 24211
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Create a deployable package of your models in order to apply it to a runtime environment

[!include[banner](../includes/banner.md)]

A Dynamics 365 for Operations package is a deployment and compilation unit of one or more models. It includes model metadata, binaries, reports and other associated resources. One or more packages can be packaged into a deployable package, which is the vehicle used for deployment of code (and customizations) on demo, sandbox and production environments. This article guides you through the process of creating and applying a deployable package. 

## Overview of the process

In order to deploy your code and customizations to a Dynamics 365 for Operations runtime environment (Demo, Sandbox or Production), you must create deployable packages of your solution or implementation. Deployable packages can be created using the **Visual Studio dev tools**, or by the **build automation process** that are available on Dynamics 365 for Operation build environments. These deployable packages are referred to as Application Deployable Packages or AOT Deployable Packages. The image below is an overview of the process. Once a deployable package is created, it must be uploaded to the LCS project's asset library. An administrator can then go to the LCS environment page and apply the package to a runtime environment using the **Maintain &gt; Apply updates** tool. 

![Create and apply a deployment package](./media/createandapplydeployablepackage.png)

> ![NOTE]
> Application Deployable Packages do not contain source code.

## Create a deployable package
After you have completed the development stage, follow these steps to create a deployable package from Visual Studio.

1.  In Microsoft Visual Studio, select **Dynamics 365** &gt; **Deploy** &gt; **Create Deployment Package**.
![Create deployment package](./media/createdeploymentpackage-986x1024.png)

2.  Select the packages that contain your models, and then select a location in which to create the deployable package. 
![Select a location](./media/pack4.png)

3.  After a deployable package is created, sign in to Microsoft Dynamics Lifecycle Services (LCS), and then, in your LCS project, click the **Asset Library** tile.

4.  Upload the deployable package that you created earlier.

## Apply a deployable package
To apply a deployable package to a Dynamics 365 for Operations environment, see the article [Apply a deployable package on a Microsoft Dynamics 365 for Operations system](apply-deployable-package-system.md).
