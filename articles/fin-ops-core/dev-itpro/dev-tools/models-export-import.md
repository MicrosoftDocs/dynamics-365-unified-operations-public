---
title: Export and import models
description: Learn about how to export a model into a model file, install a model file, and delete a model in a development environment.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 03/30/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9eb3be56-6382-43df-a247-eae0dcaf46b8
---

# Export and import models

[!include [banner](../includes/banner.md)]

Model files let you distribute models to customers and partners, and you can install them in development environments. They're key components of a Microsoft Dynamics Lifecycle Services solution. Model files contain a model descriptor file, metadata, source code, and referenced .NET assemblies (when applicable). This article describes how to export a model into a model file, install a model file, and delete a model in a development environment.

## Export a model into a model file for distribution

To export an existing model into a model file, use the ModelUtil.exe tool and the **-export** directive. This tool is located in the packages bin folder (typically, `c:\packages\bin` or `i:\AosService\PackagesLocalDirectory\bin`).

```Console
ModelUtil.exe -export -metadatastorepath=[path of the metadata store] -modelname=[name of the model to export] -outputpath=[path of the folder where the model file should be saved]
```

**Example**

```Console
ModelUtil.exe -export -metadatastorepath=c:\packages -modelname="FleetManagement" -outputpath=c:\temp
```

The preceding example creates an `.axmodel` file under `c:\temp`. Typically, you then upload the model file to the Asset Library of the customer project or the Microsoft Dynamics Lifecycle Services solution project.

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
> If you're using an older version, you can use the `-replace` parameter to replace standard models (like Foundation) for overlayering.

## Resolve conflicts

If you install a model on a development environment that contains customizations to that model (in a higher layer), you might need to resolve code or metadata conflicts. Use the development tools to create a project that groups all items that have conflicts.

1. Under <strong>Dynamics 365 &gt; AddIns</strong>, select <strong>Create Project from Conflicts</strong>.
1. In the dialog box, select the model to check for conflicts. This model contains customizations to elements in the newly installed baseline model.
1. Select **Create project**. The process generates a project that contains only the elements in that model that have conflicts.

    :::image type="content" source="./media/addupdate_metahotfix.png" alt-text="Screenshot of the AddUpdate MetaHotfix dialog.":::

1. Open the designer for the conflicting element to view and resolve conflicts by using the provided tools.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
