---
# required metadata

title: Exclude test packages from the build output
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

# Exclude test packages from the build output
With the release of Platform Update 4 for Dynamics 365 for Operations, the automated build process supports excluding certain packages from being included in the deployable package in the build output. This can be important for customers using automated testing who wish to build and execute their tests, but exclude them from being added in the build's deployable package output.

Customers with an existing build definition from Platform Update 3 or prior who are upgrading will not automatically see their build definitions updated, and will have to perform a few manual edits to the build definition if they wish to use this new capability. See [Update an existing build definition to exclude test packages from the build output](update-build-exclude-test.md) for instructions how to add this capability to an existing build definition.

The new feature exposes a new optional parameter to the package creation step in the build process. The parameter is managed by a build variable so it can be adjusted easily.

In Visual Studio Team Services (VSTS), open the **Build & Release** page. Under **Builds** and **All Definitions** find your build definition. Click on the ellipsis (…) and select **Edit**.

![Edit Build Definition](media/builddef_edit.png)

Under the **Variables** tab, the new build definition has a variable named **PackagingExclusions**.

![Package Exclusions Variable](media/builddef_packexclvariable.png)

To use this new feature, specify a comma separated list of the names of packages you wish to exclude from packaging into the deployable package. For example, if you have a package named "MyCompanysAwesomeTests" as well as a package named "ContosoTaskRecordingTests" the value for your exclusion variable should look as follows:

![Packaging Exclusions Example](media/builddef_packexclexample.png)

Note that the name of the package is not necessarily the name of the model, but typically is the name of the folder it resides in. Alternatively, you can copy/paste the package name from one of its models' descriptor files (found in the **ModelModule** field in the XML).

Once set, the build process will still build the code and still execute any tests contained in those packages. However, the deployable package created by the build will not include these packages.