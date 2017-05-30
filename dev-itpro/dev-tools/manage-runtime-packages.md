---
# required metadata

title: Manage third-party models and runtime packages using source control
description: This topic outlines a recommended strategy for managing, distributing, and deploying third-party solutions.
author: jorisdg
manager: AnnBe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 26731
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 2017-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Manage third-party models and runtime packages by using source control
Customers that work with solutions from third parties might receive different solution artifacts to use in their solution. Typically, these artifacts are distributed as code (in the form of models) or binaries (in the form of deployable packages). In some cases, third parties might provide some parts of their solution as code and other parts as a binary.

This topic outlines a recommended strategy for managing, distributing, and deploying these third-party solutions.

## Models from third parties
Any source code that is received from third parties must be compiled into a binary and included in a deployable package. Models should be installed on a development virtual machine (VM) and added to source control. From there, the build VM can pick up the source code, build it, and include it in a deployable package. Other developers can just synchronize the model from Microsoft Visual Studio Team Services (VSTS) to their development VMs. They don't have to manually install it.

For information about how to install a model on a development VM, see [Export and import a model](models-export-import.md).

After you install the model, follow these steps to add the new model to source control.

1. In Microsoft Visual Studio, on the **Dynamics 365** menu, click **Model Management** > **Refresh Models**.
2. Open Application Explorer by clicking **View** > **Application Explorer**.
3. Right-click the **AOT** root node, and then click **Model view**.
4. In the list of models, find the new model that you installed. Make a note of the name of the package that contains the model. The package name appears in parentheses after the model name. For example, in the following illustration, the **Tax Books**, **Tax Engine Configuration**, and **Tax Engine Interface** models all belong to the package that is named **TaxEngine**.

    ![Package name for each model](media/appexplorer_modelpackagename.png)

5. Open Source Control Explorer by clicking **View** > **Other Windows** > **Source Control Explorer**.
6. Navigate to the metadata folder that is mapped on this development VM, such as **MyProject/Trunk/Main/Metadata**.
7. In the metadata folder, find the folder for the package that contains the new model. Right-click the package folder, and then click **Add Items to Folder**.
9. In the **Add to Source Control** dialog box, select the **Descriptor** folder and the folder that has the name of the model, and then click **Next**.
10. Review the items that will be added, and then, when you're ready, click **Finish**.
11. Open the **Pending Changes** window from the **Team Explorer** pane or by clicking **View** > **Other Windows** > **Pending Changes**.
12. Review the changes, enter a check-in comment, and then click **Check In**.

## Deployable packages from third parties
Deployable packages from third parties can be manually installed on a development VM, and the installed artifacts can then be added to source control. Then, by synchronizing their local workspace, other developers can receive the runtime package on their VMs without having to install the deployable package. The build process on the build VM will help guarantee that the runtime packages for any extensions or other dependencies are available on the build VM. In Platform update 6 and later, by default, these runtime packages will be included in the final deployable package that is created from the build VM. For more information, see the  [Deploying third-party code](#deploying-third-party-code) section later in this topic.

For information about how to install a deployable package on a development VM, see [Install a deployable package](install-deployable-package.md).

> [!NOTE]
> Don't install a software deployable package directly on the build VM. Use source control as described in this topic. Only binary updates should be installed on build VMs.

After you install the deployable package on a development VM, follow these steps to add the runtime package to source control.

1. Open Source Control Explorer by clicking **View** > **Other Windows** > **Source Control Explorer**.
2. Navigate to the metadata folder that is mapped on this development VM, such as **MyProject/Trunk/Main/Metadata**.
3. Right-click the **Metadata** folder, and then click **Add Items to Folder**.
4. In the **Add to Source Control** dialog box, double-click the folder that has the package name that you want to add to source control.
5. Select all the folders except **XppMetadata** and **Descriptor**, if they exist, and then click **Next**.
6. On the next page, on the **Excluded items** tab, select all files by clicking one of the files and then pressing Ctrl+A. At the bottom of the selection window, click **Include item(s)**. When you're ready, click **Finish**.
7. Open the **Pending Changes** window from the **Team Explorer** pane or by clicking **View** > **Other Windows** > **Pending Changes**.
8. Review the changes, enter a check-in comment, and then click **Check In**.

## Deploying third-party code
Because the models and runtime packages are in source control, other developers who use other development environments can just synchronize the models and packages to their workspace by using the **Get latest** feature of source control.

The automated build process will also pick up the runtime packages that use Platform update 4 and later. Therefore, dependencies in packages that are built will be resolved correctly. This feature is also available for Platform update 3 and Platform update 2 through a hotfix.

In Platform update 6, the build process will include this runtime package in the final deployable package. Therefore, customers will be able to take the deployable package from the build. They must then deploy only one package to their environments, and this package includes both custom solutions and all the third-party solutions.
