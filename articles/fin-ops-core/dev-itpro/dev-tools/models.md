---
title: Models and packages
description: Learn about the concept of models and packages, including outlines on how to create new models, update parameters, and visualize dependencies between models.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 03/30/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 66a32ee2-8c4f-4ae5-b022-ad1bb4f97e59
---

# Models and packages

[!include [banner](../includes/banner.md)]

This article describes the concept of models and packages. It also explains how to use the development tools in Microsoft Visual Studio to create new models, update the parameters of existing models, and visualize dependencies between models.

To work with models in the model store, use the tools in Microsoft Visual Studio. You can create new models and change parameters for existing models.

## Conceptual overview

A model is a group of elements, such as metadata and source files, that typically constitute a distributable software solution and include customizations of an existing solution. A model is a design-time concept, for example a warehouse management model or a project accounting model. A model always belongs to a package. A package is a deployment and compilation unit of one or more models. It includes model metadata, binaries, and other associated resources. You can package one or more packages into a deployable package. A deployable package is the vehicle used for deployment on runtime environments.

## Creating a new model

Use the **Create model** wizard to create new models. Access this wizard from **Model Management** on the **Dynamics 365** menu. You can create two types of models:

- **A model that you deploy in its own package** – Use this type of model to create new model elements, and extend the metadata and business logic of referenced models. The wizard lets you select the referenced models. This type of model is compiled into its own assembly and binaries. It simplifies and reduces the cost of upgrades, deployment, and application lifecycle management.
- **A model that is part of an existing package** – Use this type of model to temporarily use legacy features such as overlayering source code and metadata. This feature is considered legacy and is supported only to upgrade from legacy versions.

In the **Create model** wizard, select **usr** for the layer. This layer stores user customizations. If needed, you can patch your customizations by using the **usp** layer. If there are multiple versions of the same object in different layers, the top layer takes precedence and is used.

When you complete the **Create model** wizard, if you choose to create a new project, you're prompted to specify a name and location for it.

## Updating model parameters

If you need to change the parameters for a model, use the **Update model parameters** dialog box.

1. On the **Dynamics 365** menu, point to **Model Management**, and then select **Update model parameters**.
1. In the **Model name** field, select the model to update parameters for.
1. Update the parameters as needed.
1. Select **Next**.
1. Update the dependency information for the current model, if changes are required.
1. Select **Next**. The summary information for the model is displayed.
1. Select **Finish**.

The updated model parameters take effect only after you restart Visual Studio.

## Viewing package dependencies

You can create a graphical representation that shows which packages and their models have dependencies on other packages. On the **Dynamics 365** menu, point to **Model Management**, and then select **View package dependencies**. A Directed Graph Markup Language (DGML) diagram is generated for the current packages and their models. This diagram is a collection of interdependent nodes, each of which represents a package. Each node lists all the models that belong to that package. Use the additional tools to enhance or simplify the diagram. For example, you can add comments, move nodes around, or remove nodes. You can also view package dependencies of a single model by following these steps:

1. Make sure the Application Explorer is in Model view: Right-click the AOT node and select **Model view**.
1. Right-click on any model and select **View package dependencies** > **View outgoing references**.

This process generates a graph of all packages that the selected model depends on.

:::image type="content" source="./media/viewdependencies2.png" alt-text="Screenshot of the View dependencies diagram.":::

:::image type="content" source="./media/directorydependencies.png" alt-text="Screenshot of the Directory dependencies diagram.":::

## Deleting a model

In a development or test environment, follow these steps to delete a model.

The following steps assume the local model store folder is `C:\AOSService\PackagesLocalDirectory` and your model is named `MyModel1`.

If your model belongs to its own package, such as an extension package with no other models in the package:

1. Close all instances of Visual Studio.
1. Stop the following services: AOS web service and Batch Management service.
1. Delete the package folder `C:\AOSService\PackagesLocalDirectory\MyModel1`. On cloud-hosted environments, this folder might be located on another drive letter such as `K:`.
1. Restart the services that you stopped in step 2.
1. In Visual Studio, perform a full database synchronization (**Visual Studio > Dynamics 365 > Synchronize database**).

If your model belongs to a package with multiple models, such as when `MyModel1` overlays Application Suite:

1. Close all instances of Visual Studio.
1. Stop the following services: AOS web service and Batch Management service.
1. Delete the model folder `C:\AOSService\PackagesLocalDirectory\<PackageName>\MyModel1`. In this example, it's `PackageName=ApplicationSuite`. On cloud-hosted environments, this folder might be located on another drive letter such as `K:`.
1. Remove the descriptor file for the model in `C:\AOSService\PackagesLocalDirectory\<PackageName>\Descriptor\MyModel1.xml`. On cloud-hosted environments, this folder might be located on another drive letter such as `K:`.
1. Restart the services that you stopped in step 2.
1. In Visual Studio, build the package that the deleted models belonged to (**Visual Studio > Dynamics 365 > Build models**).
1. In Visual Studio, perform a full database synchronization (**Visual Studio > Dynamics 365 > Synchronize database**).

## Additional resources

[Development tools in Visual Studio](development-tools-overview.md)

[Develop and customize home page](developer-home-page.md)

[Export and import models](models-export-import.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
