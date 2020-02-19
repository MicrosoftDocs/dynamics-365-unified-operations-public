---
# required metadata

title: Setup code sharing and build pipeline
description: This topic describes how to setup code sharing with Azure DevOps and a build pipeline for your Microsoft Dynamics 365 Commerce online extensibility code. 
author: samjarawan
manager: annbe
ms.date: 02/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Add module configuration fields

[!include [banner](../includes/banner.md)]

This topic describes how to setup code sharing with Azure DevOps and a build pipeline for your Microsoft Dynamics 365 Commerce online extensibility code. 

## Overview
Leveraging [Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/user-guide/what-is-azure-devops?view=azure-devops) will allow your team to plan work, collaborate on code development, and automate the building of your Dynamics 365 Commerce e-Commerce deployment packages.

In this article we will guide you through the steps needed to:
* Create a GitHub repo for Dynamics 365 Commerce online SDK
* Configure a build pipeline to generate a Dynamics 365 Commerce online deployable package


##  Create an Azure DevOps Rep
* You can create an Azure DevOps GitHub repo project from you existing Azure DevOps service subscription or a new Azure DevOps subscription.  

For more detail see [Azure DevOps Service](https://azure.microsoft.com/en-us/pricing/details/devops/azure-devops-services/). To get started with a free trial account see the [Get started with Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/user-guide/sign-up-invite-teammates?view=azure-devops quickstart guide.

* Once the Azure DevOps service is set up for your organization, create a new Azure DevOps project.
![Create new project](media/code-sharing-1.png)

* Provide a project name and description.  Select private or enterprise visibility so that it's locked to your organization and developers.

![New project created](media/code-sharing-2.png)

* Install Git. Git is a free and open source distributed version control system.  We’ll be using git to clone our SDK code. Navigate to https://git-scm.com/downloads followed by downloading and installing the latest build.  You should be able to accept all the default install values.

* Install Visual Studio Code. Visual Studio Code is a lightweight source code editor which runs on your desktop and is available for Windows, macOS and Linux.  It comes with built in support for JavaScript, TypeScript and Node.js.
Navigate to https://code.visualstudio.com and download the latest stable build. Once downloaded launch the installer and you should be able to leave all values at their defaults during the install and accept the user license agreement.




