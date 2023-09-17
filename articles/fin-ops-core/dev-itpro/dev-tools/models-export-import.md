---
title: Export and import models
description: This article describes how to export a model into a model file, install a model file, and delete a model in a development environment.
author: gianugo
ms.date: 10/01/2018
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9eb3be56-6382-43df-a247-eae0dcaf46b8
---

# Export and import models

[!include [banner](../includes/banner.md)]

Model files let you distribute models to customers and partners, and can be installed in development environments. They are key components of a Lifecycle Services (LCS) solution. Model files contain a model descriptor file, metadata, source code, and referenced .NET assemblies (when applicable). This article describes how to export a model into a model file, install a model file, and delete a model in a development environment.


## Export a model into a model file for distribution

To export an existing model into a model file, use the ModelUtil.exe tool and the **-export** directive. This tool is located in the packages bin folder (typically, c:\\packages\\bin or i:\\AosService\\PackagesLocalDirectory\\bin).

```Console
ModelUtil.exe -export -metadatastorepath=[path of the metadata store] -modelname=[name of the model to export] -outputpath=[path of the folder where the model file should be saved]
```

**Example**

```Console
ModelUtil.exe -export -metadatastorepath=c:\packages -modelname="FleetManagement" -outputpath=c:\temp
```

The preceding example creates an .axmodel file under c:\\temp. Typically, you then upload the model file to the Asset Library of the customer project or the Microsoft Dynamics Lifecycle Services (LCS) solution project.

## Install a model in a development environment
To install a model file in a development environment, use the ModelUtil.exe tool and the **-import** directive.

```Console
ModelUtil.exe -import -metadatastorepath=[path of the metadata store where model should be imported] -file=[full path of the file to import]
```

If the model already exists in your development environment, you must first delete it by using the **-delete** directive.

```Console
ModelUtil.exe -delete -metadatastorepath=[path of the metadata store] -modelname=[name of the model to delete]
```
    
> [!NOTE]
> If you're using an older version, you can use the -replace parameter to replace standard models (like Foundation) for overlayering.    

## Resolve conflicts
If you install a model on a development environment that contains customizations to that model (in a higher-layer), you may have to resolve code or metadata conflicts. You can use the development tools to create a project that groups all items that have conflicts.

1. Under <strong>Dynamics 365 &gt; AddIns</strong>, click <strong>Create Project from Conflicts</strong>.
2. In the dialog box, select the model to check for conflicts. This is the model that contains customizations to elements in the newly installed baseline model.
3. Click **Create project**. A project is generated that contains only the elements in that model that have conflicts. 

    [![AddUpdate\_MetaHotfix.](./media/addupdate_metahotfix.png)](./media/addupdate_metahotfix.png)

4. Open the designer for the conflicting element to view and resolve conflicts by using the tools that are provided. 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
