---
# required metadata

title: Develop and deploy custom models to on-premise environments
description: This topic describes the process of developing and deploying customizations and extensions to an on-premise environment. 
author: kfend
manager: AnnBe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: kfend
ms.search.scope: Operations, Platform, AX Platform
# ms.tgt_pltfrm: 
ms.custom: 107013
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 8

---

# Develop and deploy custom models to on-premise environments
This topic describes how to develop and deploy customizations and extensions to an on-premise environment. On-premise environments are also referred to as Local Business Data (LBD) environments. This topic focuses on the difference in the LBD environment development and deployment process when compared to a cloud environment.

The key steps of the process are:
1.	Deploy your development and build environments.
2.	Create a deployable package of your code and customizations.
3.	Upload the deployable package to your Dynamics Lifecycle Services (LCS) project.
4.	Configure and deploy an on-premise runtime environment, either Sandbox or Production, that includes your deployable package.

The following sections provide more information about this process.

## Development tools and platform
Whether you are developing, extending, or customizing cloud or on-premise applications, the development platform, tools, and environments (VMs) are the same. Your custom code is developed on the same development VMs whether your target runtime environments are in a cloud or on-premise environment.
For detailed information about development, see the [Developer home page](../dev-tools/developer-home-page.md). For extensibility and customization, see the [Extensibility home page](../extensibility/extensibility-home-page.md). For build, test, and continuous delivery topics, see the [Continuous delivery homepage](../dev-tools/continuous-delivery-home-page.md).

## Deploy development and build environments
You can use an on-premise LCS project to deploy Build and Development environments on Microsoft Azure by using your own Azure subscription, or download a VHD for local development.
To deploy a development or build environment in your Azure subscription or to download a development VHD, in LCS, go to the **Cloud-hosted environments** page.

 [![Cloud-hosted environment menu item](./media/alm-flow-01.png)](./media/alm-flow-01.png)
    

1. Click **Add**. 
  
  [![Cloud-hosted environment Add button](./media/alm-flow-02.png)](./media/alm-flow-02.png)
  
2. Select **Azure** or **Locally**. If you select **Locally**, you can find and download a development VHD. If you select **Azure**, you will be prompted to select one of three topologies: **Build and Test**, **Demo**, or **Development**.
3.	Complete the deployment steps and deploy a VM in your Azure subscription.

For more information about how to configure a Local development VHD, refer to the [Acess instances](./dev-itpro/dev-tools/access-instances#vm-that-is-running-onpremises) topic.
**Note**: To deploy environments in your own Microsoft Azure subscription, you must set up at least one Azure Connector. To do this, in LCS, go to **Project settings**, and select the **Azure connectors** tab. Follow the instructions to add an Azure connector. To complete these steps, you must be the tenant administrator of the organization.

[![Project settings menu item](./media/alm-flow-03.png)](./media/alm-flow-03.png)

## Create and upload a deployable package to the LCS Asset Library
When you complete a phase of development and you are ready to deploy your code to a sandbox or production on-premise environment, you must create an Application Deployable package from your models. This process does not differ from cloud environments.
If you are using automated builds (Build environment), the build process creates an Application Deployable package for you. You can also create an Application Deployable package directly from Visual Studio in your development environment. For more information on how to create an Application Deployable package on your development environment, see [Create and apply a deployable package](../deployment/create-apply-deployable-package.md).
When your deployable package is ready, upload it to your LCS project’s **Asset library**.
1.	Go to the **Asset library**.

[![Asset library menu item](./media/alm-flow-04.png)](./media/alm-flow-04.png)

2. Select the **Software deployable package** tab.

[![Software deployable package files](./media/alm-flow-05.png)](./media/alm-flow-05.png)

3. Click on **+** to upload the deployable package. 

## Configure a run-time environment on-premise with your code
As of the July 2017 release of Finance and Operations Enterprise Edition on-premise, you can apply your customizations and extensions only during the deployment of a sandbox or production environment.
1.	In your LCS project, click **Configure** to deploy your environment.

[![Sandbox Configure button](./media/alm-flow-06.png)](./media/alm-flow-06.png)

2. In the deployment tool, when you need to enter the environment name, click **Advanced settings**.

[![On premise topology Advanced settings](./media/alm-flow-07.png)](./media/alm-flow-07.png)

3. Select the **Customize Solution Assets** tab. 

[![Deployment settings](./media/alm-flow-08.png)](./media/alm-flow-08.png)

4.	In the **Select AOT package** drop-down, select the Application (AOT) Deployable package that contains your customizations. The drop-down will include all AOT packages in your **Asset library**.
5.	Click **Done** to close the **Deployment settings** window then continue with the environment deployment process.

