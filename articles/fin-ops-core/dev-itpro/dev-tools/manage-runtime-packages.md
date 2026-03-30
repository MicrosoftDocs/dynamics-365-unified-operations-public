---
title: Manage third-party models and runtime packages by using source control
description: Learn about a recommended strategy for managing, distributing, and deploying third-party solutions, including models and packages from third parties.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 03/30/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Manage third-party models and runtime packages by using source control

[!include [banner](../includes/banner.md)]

When you work with solutions from third parties, you might receive different solution artifacts to use in your solution. Typically, these artifacts come as code (in the form of models) or binaries (in the form of deployable packages). In some cases, third parties provide some parts of their solution as code and other parts as a binary.

This article outlines a recommended strategy for managing, distributing, and deploying these third-party solutions.

## Models from third parties

Compile any source code that you receive from third parties into a binary and include it in a deployable package. Install models on a development virtual machine (VM) and add them to source control. From there, the build VM can pick up the source code, build it, and include it in a deployable package. Other developers can just synchronize the model from Microsoft Azure DevOps to their development VMs. They don't have to manually install it.

For information about how to install a model on a development VM, see [Export and import models](models-export-import.md).

After you install the model, follow these steps to add the new model to source control.

1. In Microsoft Visual Studio, on the **Dynamics 365** menu, click **Model Management** > **Refresh Models**.
1. Open Application Explorer by clicking **View** > **Application Explorer**.
1. Right-click the **AOT** root node, and then click **Model view**.
1. In the list of models, find the new model that you installed. Make a note of the name of the package that contains the model. The package name appears in parentheses after the model name. For example, in the following illustration, the **Tax Books**, **Tax Engine Configuration**, and **Tax Engine Interface** models all belong to the package that is named **TaxEngine**.

    :::image type="content" source="media/appexplorer_modelpackagename.png" alt-text="Screenshot of the package name for each model.":::

1. Open Source Control Explorer by selecting **View** > **Other Windows** > **Source Control Explorer**.
1. Navigate to the metadata folder that you mapped on this development VM, such as **MyProject/Trunk/Main/Metadata**.
1. In the metadata folder, find the folder for the package that contains the new model. Right-click the package folder, and then click **Add Items to Folder**.
1. In the **Add to Source Control** dialog box, select the **Descriptor** folder and the folder that has the name of the model. Some models might also contain referenced DLLs in the **bin** folder. If these DLLs exist, you need to also include the appropriate DLL files from the **bin** folder. When you select all files, click **Next**.
1. Review the items that you add, and then, when you're ready, click **Finish**.
1. Open the **Pending Changes** window from the **Team Explorer** pane or by selecting **View** > **Other Windows** > **Pending Changes**.
1. Review the changes, enter a check-in comment, and then select **Check In**.

## Deployable packages from third parties

Manually install deployable packages from third parties on a development VM. Add the installed artifacts to source control. By synchronizing their local workspace, other developers can receive the runtime package on their VMs without having to install the deployable package. The build process on the build VM ensures that the runtime packages for any extensions or other dependencies are available on the build VM. In Platform update 6 and later, these runtime packages are included in the final deployable package that is created from the build VM. For more information, see the [Deploying third-party code](#deploying-third-party-code) section later in this article.

For information about how to install a deployable package on a development VM, see [Install deployable packages from the command line](../deployment/install-deployable-package.md).

> [!NOTE]
> Don't install a software deployable package directly on the build VM. Use source control as described in this article. Only binary updates should be installed on build VMs.

After you install the deployable package on a development VM, follow these steps to add the runtime package to source control.

1. Open Source Control Explorer by selecting **View** > **Other Windows** > **Source Control Explorer**.
1. Navigate to the metadata folder that you mapped on this development VM, such as **MyProject/Trunk/Main/Metadata**.
1. Right-click the **Metadata** folder, and then select **Add Items to Folder**.
1. In **Add to Source Control**, double-click the folder that has the package name that you want to add to source control.
1. Select all the folders except **XppMetadata** and **Descriptor**, if they exist, and then select **Next**.
1. On the next page, on the **Excluded items** tab, select all files by selecting one of the files and then pressing Ctrl+A. At the bottom of the selection window, select **Include items**. When you're ready, select **Finish**.
1. Open the **Pending Changes** window from the **Team Explorer** pane or by selecting **View** > **Other Windows** > **Pending Changes**.
1. Review the changes, enter a check-in comment, and then select **Check In**.

## Including source-controlled third-party packages

After checking in the package binaries into source control as described in the previous section, include the binaries in deployable packages generated during build automation. Two options are available:

+ On a build virtual machine, the standard legacy pipeline automatically finds and includes the binaries into the deployable package it generates.
+ To use the [new pipeline](hosted-build-automation.md) or the new packaging task in the legacy pipeline, see the [create deployable packages](pipeline-create-deployable-package.md) documentation. The documentation has examples for including source-controlled binaries in deployable packages.

## Deploy third-party code

Because the models and runtime packages are in source control, other developers who use different development environments can synchronize the models and packages to their workspace by using the **Get latest** feature of source control.

Starting with Platform update 4, the automated build process also picks up the runtime packages. Therefore, dependencies in packages that the build process creates are resolved correctly. Through a hotfix, this feature is also available for Platform update 3 and Platform update 2.

In Platform update 6, the build process includes this runtime package in the final deployable package. This inclusion means customers can take the deployable package from the build and have one package to deploy to their environments. The one package includes both custom solutions and all the third-party solutions.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
