---
title: Exclude test packages from build output
description: This article explains how to prevent specific packages from being included in the package in the build output that the automated build process generates.
author: gianugo
ms.date: 05/15/2017
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2017-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 
---

# Exclude test packages from build output

[!include [banner](../includes/banner.md)]

In Platform update 4, the automated build process lets you prevent specific packages from being included in the deployable package in the build output. This capability can be important for customers that use automated testing. These customers might want to build and run their tests, but prevent them from being added to the deployable package that the build generates as output.

When customers that have an existing build definition from Platform update 3 or earlier upgrade, they won't see the build definition automatically updated. To use the new feature, these customers must make a few manual edits to the build definition (see below for details). 

The new feature exposes a new optional parameter for the package creation step in the build process. Because this parameter is managed by a build variable, you can easily adjust it.

1. In Microsoft Azure DevOps, on the **Build & Release** page, under **Builds**, on the **All Definitions** tab, find your build definition. Click the ellipsis (…), and then click **Edit**.

    ![Edit the build definition.](media/builddef_edit.png)

1. On the **Variables** tab, notice that the new build definition has a variable that is named **PackagingExclusions**.

    ![PackagingExclusions variable.](media/builddef_packexclvariable.png)

1. In the **PackagingExclusions** variable, specify a comma-separated list of the names of packages that should not be packaged into the deployable package.

    > [!NOTE]
    > The name of a package isn't necessarily the name of the model. Instead, the package name is typically the name of the folder where the model resides. Alternatively, you can copy and paste the package name from the descriptor file of one of the package's models. (In the XML, you can find the package name in the **ModelModule** field.)

    For example, you have one package that is named MyCompanysAwesomeTests and another package that is named ContosoTaskRecordingTests, and you want to exclude both these packages from the deployable package. In this case, the value for the **PackagingExclusions** variable will look like this.

    ![PackagingExclusions example.](media/builddef_packexclexample.png)

    After you complete this setup, the build process will still build the code and run any tests that the packages contain. However, the deployable package that the build creates won't include those packages.

## Update an existing build definition after upgrade to Platform update 4 or later

To use the new feature, you must manually update any existing build definitions that you deployed before Platform update 4.

> [!NOTE]
> The feature can be added to a build definition only after you update the build virtual machine (VM) to Platform update 4 or later.

1. On the **Variables** tab, click **+ Add** at the bottom of the page.
1. In the **Name** column, enter **PackagingExclusions**. In the last column, select the **Settable at queue time** check box.
1. On the **Tasks** tab, find the **Generate Packages** task. Click to select it.
1. On the right side of the page, find the **Arguments** parameter. Click in the text box, and then press the End key or scroll to the end of the text box. The new build definition will have a new argument that passes the **PackagingExclusions** variable that you defined earlier. However, for an existing build definition, add a space and then the following text to the end of the parameter: **-ExclusionList "$(PackagingExclusions)"**

    The **Arguments** text box should now look like this.

    ![Generate Packages task.](media/builddef_generatepack.png)

1. Click **Save**.

You can now use the new feature as described.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
