---
# required metadata

title: Setup Azure DevOps code sharing and build pipeline
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
# Setup Azure DevOps code sharing and build pipeline

[!include [banner](../includes/banner.md)]

This topic describes how to setup code sharing with Azure DevOps and a build pipeline for your Microsoft Dynamics 365 Commerce online extensibility code. 

## Overview
Leveraging [Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/user-guide/what-is-azure-devops?view=azure-devops) will allow your team to plan work, collaborate on code development, and automate the building of your Dynamics 365 Commerce e-Commerce deployment packages.

In this article we will guide you through the steps needed to:
* Create a GitHub repo for Dynamics 365 Commerce online SDK
* Configure a build pipeline to generate a Dynamics 365 Commerce online deployable package


##  Create an Azure DevOps Repo
1. You can create an Azure DevOps GitHub repo project from you existing Azure DevOps service subscription or a new Azure DevOps subscription.  For more detail see [Azure DevOps Service](https://azure.microsoft.com/en-us/pricing/details/devops/azure-devops-services/). To get started with a free trial account see the [Get started with Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/user-guide/sign-up-invite-teammates?view=azure-devops quickstart guide.

2. Once the Azure DevOps service is set up for your organization, create a new Azure DevOps project.

![Create new project](media/code-sharing-1.png)

3. Provide a project name and description.  Select private or enterprise visibility so that it's locked to your organization and developers.

![Provide project name](media/code-sharing-2.png)

4. Install Git. Git is a free and open source distributed version control system.  We’ll be using git to clone our SDK code. Navigate to https://git-scm.com/downloads followed by downloading and installing the latest build.  You should be able to accept all the default install values.

5. Install Visual Studio Code. Visual Studio Code is a lightweight source code editor which runs on your desktop and is available for Windows, macOS and Linux.  It comes with built in support for JavaScript, TypeScript and Node.js.
Navigate to https://code.visualstudio.com and download the latest stable build. Once downloaded launch the installer and you should be able to leave all values at their defaults during the install and accept the user license agreement.

6. Clone the Microsoft Dynamics 365 Commerce Online SDK/Starter kit. The SDK will give you everything you need to extend your e-Commerce site including the ability to create new modules, data actions and themes. 

The SDK configuration package is available through the following GitHub repository: https://github.com/microsoft/Msdyn365.Commerce.Online  

There are two ways to get the SDK configuration packages to your development machine.  

You can either directly download it from the GitHub repo or clone the repo. To clone, start off by launching a Command Prompt with Administrator privileges and create a directory to hold your e-Commerce site code, we’ll use “c:\repos” below. 

From the new directory perform a “git clone YOUR_GIT_REPO”. 

```console
md c:\repos
cd c:\repos
git clone https://github.com/microsoft/Msdyn365.Commerce.Online.git
cd Msdyn365.Commerce.Online
```

Since you’re only pulling from the git repository once, you can remove .git folder to unlink, which is a hidden directory under the root.

7. We'll now clone the Azure DevOps GitHub project repo. Select the "Files" tab under the **Repos** section on the left tab bar.  Select the "copy" icon to copy the URL.

![Clone Azure DevOps repo](media/code-sharing-3.png)

To clone, start off by launching a Command Prompt with Administrator privileges and go to the directory to hold your Azure DevOps repo code, we’ll use “c:\repos” below. 

From the new directory perform a “git clone YOUR_GIT_REPO”. 
```console
cd c:\repos
git clone https://xxxxxx.dev.azure.com/<DevOpsProjectName>/_git/< DevOpsProjectName>
```

A new folder with name of the Azure DevOps project will be created with no contents.

8. Copy all the contents of “C:\repos\Msdyn365.Commerce.Online” to “C:\repos\<DevOpsProjectName>”
Open Visual studio Code. Open folder “c:\repos\<DevOpsProjectName>”  (Note: Do not copy the hidden .git folder over)

9. Open Visual studio Code. Open folder “c:\repos\<DevOpsProjectName>”.  Visual studio code will show the new changes to be committed when you select the source control tab on the left hand side.  Commit all changes to Git by selecting the "Commit all" checkbox at the top.  Enter a check in description when prompted.

![Commit changes](media/code-sharing-4.png)

10. Select the "..." menu at the top and then "Push" to push the changes to the repo.  

![Push changes](media/code-sharing-5.png)

11. If you now go to the repo files in Azure DevOps, you can see the new files.

![New files in Azure DevOps](media/code-sharing-6.png)

## Create a new build pipeline
1. In Azure DevOps select **Pipelines** under the **Pipelines** tab on the left followed by the **Create Pipeline** button.

![Create a pipeline](media/code-sharing-7.png)

1. Select the **Use the classic editor** link.

![Select classic editor](media/code-sharing-8.png)

1. Select the repository <DevOpsProjectName> followed by the continue button.

![Select repository](media/code-sharing-9.png)

1. Choose an empty job template.

![Choose an empty job template](media/code-sharing-10.png)

1. Select the **+** button next to "Agent job 1" to add a new agent job.

![Add new agent job](media/code-sharing-11.png)

1. Search for the "PowerShell" task and select the "Add button".

![Add PowerShell task](media/code-sharing-12.png)

1. Select the new "PowerShell Script" item and copy the below script and set the **Type** to Inline.

  ```console
  yarn
  yarn msdyn365 pack
  ```
  
![Configure task](media/code-sharing-13.png)

1. Expand the **Advanced** sectin and change the working directory to **$(Build.SourcesDirectory)**

![Set working directory](media/code-sharing-14.png)

1. Add "Copy files" agent by selecting the **+** next to "Agent job 1" and searching for "copy" followed by selecting the "Add" button.

![Add copy files agent](media/code-sharing-15.png)

