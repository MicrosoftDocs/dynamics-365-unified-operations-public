---
# required metadata

title: Models
description: This article describes the concept of models and packages. It also explains how to use the Development tools in Microsoft Visual Studio to create new models, how to update the parameters of existing models, and how to visualize dependencies between models.
author: RobinARH
manager: AnnBe
ms.date: 2016-04-27 23 - 07 - 28
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 83351
ms.assetid: 66a32ee2-8c4f-4ae5-b022-ad1bb4f97e59
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Models

This article describes the concept of models and packages. It also explains how to use the Development tools in Microsoft Visual Studio to create new models, how to update the parameters of existing models, and how to visualize dependencies between models.

To work with models in the model store, you use tools in Microsoft Visual Studio. You can create new models and change parameters for existing models.

## Conceptual overview
A model is a group of elements (metadata/source files) that typically constitute a distributable software solution (including customizations of an existing solution). A model is a design-time concept. For example: A warehouse management model, a project accounting model, …etc.). Follow [this](https://mix.office.com/watch/ies6lyit6773)Office Mix to learn about models and packages and how they relate to each other.

## Creating a new model
You use the **Create model** wizard to create new models. You can access this wizard from **Model Management** on the **Dynamics 365 **menu. You can create two types of models:

-   **A model that is deployed in its own package** – You can use this type of model to create new model elements, and extend the metadata and business logic of referenced models. The wizard lets you select the referenced models. This type of model is compiled into its own assembly and binaries, and will simplify and reduce the cost of upgrades, deployment, and application lifecycle management in general.
-   **A model that is a part of an existing package** – You can use this type of model to perform advanced customizations, such as overlayering source code and metadata.

When the **Create model** wizard is completed, if you chose to create a new project, you will be prompted to specify a name and location for it.

## Updating model parameters
If you must change the parameters for a model, you can use the **Update model parameters** dialog box.

1.  On the **Dynamics 365 **menu, point to **Model Management**, and then click **Update model parameters**.
2.  In the **Model name** field, select the model to update parameters for.
3.  Update the parameters as you require.
4.  Click **Next**.
5.  Update the dependency information for the current model, if changes are required.
6.  Click **Next**. The summary information for the model is displayed.
7.  Click **Finish**.

The updated model parameters become effective only after you restart Visual Studio.

## Viewing package dependencies
You can create a graphical representation that shows which packages (and their models) have dependencies on other packages. On the **Dynamics 365 **menu, point to **Model Management**, and then click **View package dependencies**. A Directed Graph Markup Language (DGML) diagram will be generated for the current packages and their models. This diagram is a collection of interdependent nodes, each of which represents a package. Each node lists all the models that belong to that package. Additional tools let you enhance or simplify the diagram. For example, you can add comments, move nodes around, or remove nodes. You can also view package dependencies of a single model by following these steps:

1.  Make sure the Application Explorer is in Model view: Right-click on the AOT node and select Model view.
2.  Right-click on any model and select **View package dependencies** &gt; **View outgoing references.**

This will generate a graph of all packages that the selected model depends on. [![viewdependencies2](./media/viewdependencies2.png)](./media/viewdependencies2.png) [![directorydependencies](./media/directorydependencies.png)](./media/directorydependencies.png)

See also
--------

[Development tools](development-tools.md)

[Developer home page](developer-home-page.md)

[Distribution of models: How to export and import model files](models-export-import.md)

