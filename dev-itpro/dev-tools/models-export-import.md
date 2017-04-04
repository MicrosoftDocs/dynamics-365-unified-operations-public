---
# required metadata

title: Export and import a model
description: Model files let you distribute models to customers and partners, and can be installed in development environments. They are key components of a Lifecycle Services (LCS) solution. Model files contain a model descriptor file, metadata, source code, and referenced .NET assemblies (when applicable). This article describes how to export a model into a model file, install a model file, and delete a model in a development environment.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
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
ms.custom: 20451
ms.assetid: 9eb3be56-6382-43df-a247-eae0dcaf46b8
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Export and import a model

Model files let you distribute models to customers and partners, and can be installed in development environments. They are key components of a Lifecycle Services (LCS) solution. Model files contain a model descriptor file, metadata, source code, and referenced .NET assemblies (when applicable). This article describes how to export a model into a model file, install a model file, and delete a model in a development environment.

Export a model into a model file for distribution
-------------------------------------------------

To export an existing model into a model file, use the ModelUtil.exe tool and the **-export** directive. This tool is located in the packages bin folder (typically, c:\\packages\\bin or i:\\AosService\\PackagesLocalDirectory\\bin).

    ModelUtil.exe -export -metadatastorepath=[path of the metadata store] -modelname=[name of the model to export] -outputpath=[path of the folder where the model file should be saved]

**Example**

    ModelUtil.exe -export -metadatastorepath=c:\packages -modelname="FleetManagement" -outputpath=c:\temp

The preceding example creates an .axmodel file under c:\\temp. Typically, you then upload the model file to the Asset Library of the customer project or the Microsoft Dynamics Lifecycle Services (LCS) solution project.

## Install a model in a development environment
To install a model file in a development environment, use the ModelUtil.exe tool and the **-import** directive.

    ModelUtil.exe -import -metadatastorepath=[path of the metadata store where model should be imported] -file=[full path of the file to import]

If the model already exists in your development environment, you must first delete it by using the **-delete** directive.

    ModelUtil.exe -delete -metadatastorepath=[path of the metadata store] -modelname=[name of the model to delete]

## Resolve conflicts
If you install a model on a development environment that contains customizations to that model (in a higher-layer), you may have to resolve code or metadata conflicts. You can use the development tools to create a project that groups all items that have conflicts.

1.  Under **Dynamics 365 **&gt; **AddIns**, click **Create Project from Conflicts**.
2.  In the dialog box, select the model to check for conflicts. This is the model that contains customizations to elements in the newly installed baseline model.
3.  Click **Create project**. A project is generated that contains only the elements in that model that have conflicts. [![AddUpdate\_MetaHotfix](./media/addupdate_metahotfix.png)](./media/addupdate_metahotfix.png)
4.  Open the designer for the conflicting element to view and resolve conflicts by using the tools that are provided. For an introduction to conflict resolution tools that are available in a Dynamics 365 for Operations development environment, see the [Resolve conflicts using Visual Studio tools](https://mix.office.com/watch/1rl75ei2cs6d7) Microsoft Office Mix.


