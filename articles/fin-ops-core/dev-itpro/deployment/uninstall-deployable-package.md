---
title: Uninstall a package
description: Learn how to remove a deployable package from your environment, including prerequisites and a step-by-step process of uninstalling packages.
author: laneswenka
ms.author: laswenka
ms.topic: article
ms.custom:
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0
---

# Uninstall a package

[!include [banner](../includes/banner.md)]

Occasionally, you might need to uninstall a deployable package. For example, you might be reorganizing your source code. Alternatively, you no longer require an independent software vendor (ISV) product and didn't renew the license. Therefore, you must remove the package.

## Remove a model

A model is a design-time concept that's part of a package. When a model isn't the only model in a module, you can remove it from the source code. No other steps are required, because when you deploy the updated module, the old module is overwritten. All overlayer models fall into this category. For more information, see [Deleting a model](../dev-tools/models.md#deleting-a-model).

## Prerequisites

- If any models reference the module that you want to remove, remove those references. For information about how to find the references that you must remove, see [Viewing model dependencies](../dev-tools/models.md#viewing-package-dependencies).
- Build and deploy any modules that you removed references from.
- Remove all references to and from the modules before you begin to uninstall the module. To remove all a module's references, add a single class to the model. This class should contain no code. It should contain only a reference to the application platform.
- You can't remove a Microsoft module. If you attempt this action, a validation error is shown on the package in Lifecycle Services.
- You can't remove a module if it's part of the AOT deployable package being installed. If you want to remove a module, ensure that it's not part of the package before adding the name to the **ModuleToRemove.txt** file.

## Uninstall a package

1. Create a file named **ModuleToRemove.txt**.
1. In the file, put the name of each module that you want to remove on a separate line. Make sure that you completed the prerequisites for each module that you're removing.
1. Create a valid deployable package, and put the **ModuleToRemove.txt** file in the **package\AOSService\Scripts** folder.
1. Upload the package to the Lifecycle Services asset library. Wait for the asset to finish validation, and review any warnings that are shown on the Asset Details panel on the right side of the page.
1. Install the deployable package. For more information about how to install deployable packages, see [Apply updates to cloud environments](apply-deployable-package-system.md).
1. Verify that the package was uninstalled before you complete this procedure in a production environment.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
