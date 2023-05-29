---
# required metadata

title: Uninstall a package
description: This article explains how to remove a deployable package from your environment.
author: laneswenka
ms.date: 09/22/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Uninstall a package

[!include [banner](../includes/banner.md)]

Occasionally, you might have to uninstall a deployable package. For example, you might be reorganizing your source code. Alternatively, you no longer require an independent software vendor (ISV) product and haven't renewed the license. Therefore, you must remove the package.

## Remove a model

A model is a design-time concept that is part of a package. When a model isn't the only model in a module, you can just remove it from the source code. No other steps are required, because when you deploy the updated module, the old module is overwritten. All overlayer models fall into this category. For more information, see [Deleting a model](../dev-tools/models.md#deleting-a-model).

## Prerequisites

- If any models reference the module that will be removed, the references must be removed from them. For information about how to find the references that must be removed, see [Viewing model dependencies](../dev-tools/models.md#viewing-package-dependencies).
- Build and deploy any modules that references were removed from.
- All references to and from the modules must be removed before you begin to uninstall the module. To remove all a module's references, add a single class to the model. This class should contain no code. It should contain only a reference to the application platform.
- A Microsoft module cannot be removed.  If this is attempted, a validation error will be shown on the package in Lifecycle Services.
- A module cannot be removed if it is part of the AOT deployable package being installed.  If you want to remove a module, be sure that it is not part of the package before adding the name to the ModuleToRemove.txt file.

## Uninstall a package

1. Create a file that is named **ModuleToRemove.txt**.
2. In the file, put the name of each module that you want to remove on a separate line. Make sure that you've completed the prerequisites for each module that you're removing.
3. Create a valid deployable package, and put the ModuleToRemove.txt file in the **package\\AOSService\\Scripts** folder.
4. Upload the package to the Lifecycle Services asset library. Wait for the asset to finish validation, and review any warnings that are shown on the Asset Details panel on the right side of the page.
5. Install the deployable package. For more information about how to install deployable packages, see [Apply updates to cloud environments](apply-deployable-package-system.md).
6. Verify that the package was uninstalled before you complete this procedure in a production environment.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]