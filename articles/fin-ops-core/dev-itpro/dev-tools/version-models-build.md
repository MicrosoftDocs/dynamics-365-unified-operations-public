---
title: Update model versions in the automated build
description: The article explains how to update the models in a source package and deployable package of the build output with the version of the build that produced them.
author: gianugo
ms.date: 05/25/2017
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2017-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 
---

# Update model versions in the automated build

[!include [banner](../includes/banner.md)]

In Platform update 6, a new task in the automated build definition updates the models in the source package and deployable package of the build output with the version of the build that produced them.

Build definitions that were created before Platform update 6 must be manually updated to include this task. See the [Updating an existing build definition](#updating-an-existing-build-definition) section later in this article.

## Version numbers 
Even though models are compiled into one package, the metadata information of all models is retained inside the binary package. This information can be reviewed from Microsoft Dynamics Lifecycle Services (LCS) or from the client.

In LCS, follow these steps to find the version numbers of models that are installed in an environment.

1. On the **Full details** page for the environment, under **Environment Version Information**, click the **View detailed version information** link. 
1. On the **Installed updates** page, in the **Machine name** field, select an Application Object Server (AOS) computer. 
1. In the table list, find the **Publisher name** field of the model, and expand the list by clicking the arrow icon. A full list of all models from that publisher is shown. The version number is shown in the **Version** column.

In the client, follow these steps to find the version numbers of models that are installed in an environment.

1. Open the URL for the environment, and sign in. 
1. After the dashboard is loaded, click the gear symbol at the upper right of the page, and then click **About**. 
1. In the dialog box that appears, expand **Loaded Packages and their Models**. Find the package where the model resides, and expand the list by clicking the arrow icon. The list of models for the package is shown, together with the version number.

All version numbers are in .NET assembly format. They consist of four numbers that are separated by a dot (.), such as **1.2.3.4**.

## The purpose of model versioning
As code is updated, the build is used to produce new packages that can be deployed to environments. Microsoft Azure DevOps tracks the changes that have been included in each build since the previous build. When the version number of the build is included in the models that are produced, it provides end-to-end traceability of the code changes that are available in a specific environment. You can find the build number and then review the changes that are included in that build in Azure DevOps. For customers and partners that use builds on different branches, or that use different build definitions for nightly builds, gated check-in builds, or deployment builds, each build can have a different versioning scheme. This approach helps differentiate the model metadata in the deployable packages and tie them back to their originating build definition.

## Setting up versioning
For build definitions that are created by Platform update 6 or newer deployments, the task to include build version in models is automatically added and active. The default build number of a new build definition in Azure DevOps consists of the year, month, and day, and the incremental number of the build for that day. For more information about build numbers in Azure DevOps, and the options that are available, see [Build definition options](https://www.visualstudio.com/docs/build/define/options#Buildnumberformat) on the Microsoft Visual Studio docs site.

The automated build will apply the build version number to the models that are built.

## Preventing models from being updated
By default, the build task assigns versions only to models that are in layers above the ISP layer. Therefore, customers can consume code models from third-party vendors without overwriting the version numbers that are supplied in their models. However, you can also prevent other models from having their version numbers overwritten during the build, regardless of layer. When you edit the build definition, on the **Variables** tab, in the **ModelVersionExclusions** variable, supply a comma-separated list of model names to exclude.

## Updating models in lower layers
For third parties that develop solutions in the ISV or ISP layer, a manual change must be made to the build definition to automatically set model versions in those layers. 

1. Edit the build definition. On the **Tasks** tab, click the **Set Model Versions** task. 
1. In the **Arguments** field, add the following option at the end of the existing list of arguments: **-UpdateLayersAbove 7**

## Updating an existing build definition
For build definitions that were created before Platform update 6, a new task must be manually added to the build definition.

> [!NOTE]
> This feature can be added to a build definition only after the build virtual machine (VM) has been updated to Platform update 6 or later.

1. In Azure DevOps, on the **Build & Release** page, under **Builds**, on the **All Definitions** tab, find your build definition. 
1. Click the ellipsis (…), and then click **Edit**.

    ![Edit the build definition.](media/builddef_edit.png)

1. On the **Tasks** tab, click **+ Add Task** at the bottom of the page.
1. In the **Add tasks** pane on the right side of the page, on the **Utility** tab, scroll down to find the **PowerShell** task. 
1. Hover the mouse pointer over the task, and click the **Add** button that appears.

    ![Add a PowerShell task.](media/builddef_addpowershelltask.png)

1. In the list of tasks on the left side of the page, click to select the **PowerShell Script** task that is added.
1. On the right side of the page, change the **Display name**, **Script Path**, and **Arguments** properties to reflect the required settings.

    ![Set the properties for the Set Model Versions task.](media/builddef_setmodelversions_settings.png)

1. In the list of tasks on the left side of the page, drag the **Set Model Versions** task so that it's between the **Prepare for build** and **Build the solution** tasks.

    ![Set the order of the Set Model Versions task.](media/builddef_setmodelversions_order.png)

1. On the **Variables** tab, click **+ Add** at the bottom of the list of variables. In the first column, for the **Name** variable, enter **ModelVersionExclusions**.
1. Click **Save** to save the new task.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
