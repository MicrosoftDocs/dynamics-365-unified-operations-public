---
# required metadata

title: Develop and deploy custom models to on-premise environments
description: This topic describes the process of developing and deploying customizations and extensions to an on-premise environment. 
author: kfend
manager: AnnBe
ms.date: 04/22/2017
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
This topic describes the process of developing and deploying customizations and extensions to a Dynamics 365 for Finance and Operations on-premises environment. One-premises environment are also referred to as Local Business Data environments. This topic focus on the difference in the process when compared to cloud environments.
The key steps of the process are:
1.	Deploy your development and build environments.
2.	When development is complete, create a deployable package of your code and customizations.
3.	Upload the deployable package to your Dynamics Lifecycle Services (LCS) project.
4.	Configure/deploy an on-premises runtime environment (Sandbox or Production) that includes your deployable package.
The following sections detail this process.

## Development tools and platform
Whether you are developing, extending or customizing cloud or on-premises applications of Dynamics 365 for Finance and Operations, the development platform, tools, and environments (VMs) are the same. Your custom code is the same and is developed on the same development VMs whether your target runtime environments are cloud or on-premises environment.
For detailed information on development, go to the Developer home page. For extensibility and customization, go the Extensibility home page. For build, test, and continuous delivery topics, refer to the continuous delivery homepage.

## Deploy development and build environments
An LCS project for Dynamics 365 for Finance and Operations on-premises enables you to deploy Build and Development environments on Microsoft Azure (using your own Azure subscription), or download a VHD for local development.
To deploy a development or build environment in your Azure subscription or to download a development VHD, go to Cloud-hosted environments.

GRAPHIC

1. Click **Add**. 
GRAPHIC
2. Select Azure or Locally. If you select Locally*, this will take you to a download page where you can find and download a development VHD. If you select Azure**, you will then be prompted to select one of 3 topologies: Build and Test, Demo or Development.
3.	Go through the deployment steps. This will deploy a VM in your Azure subscription.

*For more information on how to configure a local development VHD, refer to this article.
**To deploy environments in your own Microsoft Azure subscription, you need to setup at least one Azure Connector. Go to Project settings and select the Azure connectors tab to add an Azure connector (Follow the instructions on the page). You need to be the tenant administrator of the organization.

GRAPHIC

## Create a deployable package then upload to the LCS Asset Library
When you complete a phase of development and you are ready to deploy your code to a sandbox or production environment of Finance and Operations on-premises, you must create an Application Deployable package out of your models. This process does not differ from the cloud version of Finance and Operations.
If you are using automated builds (Build environment), the build process creates an Application Deployable package for you. You can also create an Application Deployable package directly from Visual Studio on your development environment. For more information on how to create an Application Deployable package on your development environment, go to this topic.
When your deployable package is ready, upload it to your LCS project’s asset library.
1.	Go to the Asset library.

GRAPHIC

2. Select the **Software deployable package** tab.

GRAPHIC

3. Click on **+** to upload a deployable package. 

## Configure a runtime environment on-premises with your code
As of the July 2017 release of Finance and Operations on-premises, you can apply your customizations and extensions only during the deployment of a sandbox or production environment.
1.	In your LCS project, click Configure to start deployment of your environment.

GRAPHIC

2. Go through the deployment tool, when you reach the page where you need to enter the environment name, click **Advanced settings**.

GRAPHIC

3. Select the **Customize Solution Assets** tab. 

GRAPHIC

4.	In the Select AOT package drop down menu, select the Application (AOT) Deployable package that contains your customizations. The dropdown menu will include all AOT packages in your Asset library.
5.	Click Done to close the Deployment settings window then proceed with the environment deployment process.

