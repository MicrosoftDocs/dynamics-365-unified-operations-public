---
# required metadata

title: Manage third-party models and runtime packages using source control
description: 
author: jorisdg
manager: AnnBe
ms.date: 05/15/2017
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

# Manage third-party models and runtime packages using source control
When working with solutions from third parties, customers may receive different solution artifacts to be used in their solution. Typically these are distributed as code (in the form of models) or binaries (in the form of deployable packages). In some cases, third parties may provide parts of their solution as code, and part of the solution as a binary.

In this article we will outline a recommended strategy for managing, distributing and deploying these third party solutions.

## Models from third parties
Any source code received from third parties will have to be compiled into a binary and included in a deployable package. Models should be installed on a development VM and added to source control. From there, the build VM can pick up the source code, build it and include it in a deployable package. Other developers can just synchronize the model from VSTS onto their development VMs without the need to manually install it as well.
To install a model on a development VM, refer to the [Export and import a model](models-export-import.md) article.

After installing the model, follow these steps to add the new model to source control:

1. From the **Dynamics 365** menu in Visual Studio, click **Model Management > Refresh Models**
2. Open the Application Explorer by selecting **View > Application Explorer** from the Visual Studio menu
3. Right-click the **AOT** root node and select **Model view**
4. From the list of models, find the installed model. In parenthesis after the name, the name of the package containing the model will be listed. For example, the models **Tax Books**, **Tax Engine Configuration**, **Tax Engine Interface** all belong to the package named **TaxEngine**.

![Package name for each model](media/appexplorer_modelpackagename.png)

5. Now that we know the name of the package, open the source control explorer from **View > Other Windows > Source Control Explorer**
6. Navigate to the metadata folder mapped on this development VM, for example "MyProject/Trunk/Main/Metadata"
7. In the metadata folder, find the folder for the package containing the new model
8. Right-click on the package folder, and click **Add Items to Folder**…
9. From the **Add to Source Control** dialog, select the **Descriptor** folder and the folder with the name of the model, and click **Next**
10. Review the items to be added, and click **Finish** when ready
11. Open the **Pending Changes** window from the **Team Explorer** pane, or by opening it from the menu under **View > Other Windows > Pending Changes**
12. Review the changes, provide and check-in comment and click **Check In**

## Deployable packages from third parties
Deployable packages from third parties can be manually installed on a development VM, and the installed artifacts added to source control. Other developers on other VMs can subsequently synchronize their local workspace to also receive the runtime package on their VMs without the need to install the deployable package. The build VM's build process will ensure the runtime packages are available on the build VM for any extensions or other dependencies. On platform update 6 and newer, by default these runtime packages will be included in the final deployable package created from the build VM. See [Deploying Third Party Code](#deploying-third-party-code).

For instructions on how to install a deployable package on a development VM, refer to the article [Install a deployable package](install-deployable-package.md)

> [!NOTE]
> Do not install a software deployable package directly on the build VM. Use source control as described in this article. Only binary updates should be installed on build VMs.

After installing the deployable package on a development VM, follow these steps to add the runtime package to source control:

1. Open the source control explorer from **View > Other Windows > Source Control Explorer**
2. Navigate to the metadata folder mapped on this development VM, for example "MyProject/Trunk/Main/Metadata"
3. Right-click on the **Metadata** folder, and click **Add Items to Folder…**
4. From the **Add to Source Control** dialog, double click on the folder that has the package name which you wish to add to source control
5. Select all the folders (**bin**, **Resources**, **Webcontent**, **Reports**, etc.), but exclude **XppMetadata** and **Descriptor**, if they exist, and click **Next**
6. On the next page, click the **Excluded items** tab page, select all files by clicking on one of the files and pressing CTRL+A. At the bottom of the selection window, click **Include item(s)** and click **Finish** when ready
7. Open the **Pending Changes** window from the **Team Explorer** pane, or by opening it from the menu under **View > Other Windows > Pending Changes**
8. Review the changes, provide a check-in comment and click **Check In**

## Deploying third party code
Since the models and runtime packages are in source control, other developers using other development environments can just synchronize the models and packages to their workspace using the **Get latest** feature of source control.
The automated build process will also pick up the runtime packages with platform update 4 and above, so dependencies in packages being built resolve correctly. This feature is also available for platform update 3 and platform update 2 through a hotfix.

With platform update 6, the build process will include this runtime package in the final deployable package. This allows customers to take the deployable package from the build and have one package to deploy to their environments, which includes both custom solutions and all the third party solutions.
