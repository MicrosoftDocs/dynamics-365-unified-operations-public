---
# required metadata

title: Uninstall a package
description: This topic provides information about how to remove a deployable package from your environment.
author: manado
manager: AnnBe
ms.date: 07/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 24211
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Uninstall a package

[!include [banner](../includes/banner.md)]

There are times where you might need to uninstall a deployable package. For example, you might be reorganizing your source code. Or, if could be that you no longer need an ISV product and you haven't renewed the license and therefore need to remove the package. 

## Remove a model
A model is a design-time concept that is a part of a package. When a model is not the only model in a module, you can simply remove it from the source code. No other steps are required because when you deploy the updated module, it will overwrite the old one. All overlayer models fall into this category. For more information, see [Deleting a model](./dev-tools/models.md#deleting-a-model).

 ## Required prerequisites

- Any models that reference the module to be removed must have the references removed. To find the references that must be removed, see [Viewing model dependencies](./dev-tools/models.md#viewing-package-dependencies).
- Build and deploy any modules that had references removed.
- All references to and from the modules must be removed before you begin to uninstall the module. Before you uninstall the module, remove all of it's references by adding to the model, a single class with no code and only a reference to the application platform.

## Uninstall a package

1. Create a file named ModuleToRemove.txt
2. Put the name of each module that you want to remove on a separate line in the file. Make sure that you have completed the required prerequisites for each module that you are removing.
3. Create a valid deployable package and put the ModuleToRemove.txt in the package\AOSService\Scripts folder.
4. Install the deployable package. For more information about how to do this, see [Apply updates to a cloud deployment](apply-deployable-package-system.md)
5. Validate that the package has uninstalled before you perform this on a production environment.
