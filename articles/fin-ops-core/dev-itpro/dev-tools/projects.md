---
title: Finance and operations project type in Visual Studio
description: The finance and operations project type is part of the development tools. Learn about creating new projects and elements to a project.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 03/30/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: d0d12e0e-a417-41b1-b2eb-7c69eee5ac61
---

# Finance and operations project type in Visual Studio

[!include [banner](../includes/banner.md)]

The finance and operations project type is part of the development tools. This project type resembles other projects in Visual Studio. It helps you organize and manage the elements you're working with for a model. For example, the project can have folders that help you group the elements. A Visual Studio solution can contain multiple projects. One important constraint for a project is that it can contain elements from only one model. If you need to work with elements from different models, you must use multiple projects in your Visual Studio solution.

## Create a new project

To create a new, empty project, follow these steps:

1. On the **File** menu, point to **New**, and then select **Project**.
1. In the list of template types, expand the **Installed** node.
1. Expand the **Templates** node.
1. Select the **finance and operations** category.
1. Select the **Operations Project** template.
1. Enter the name and location for the new project.
1. Specify whether you want to create a new solution or add the project to the current solution.
1. Select **OK**.

Every project has several important properties. To set the properties for a project, right-click the project in **Solution Explorer**, and then select **Properties**. The following table describes these properties.

Property | Description
---|---
Startup Object type | The type of object that the project uses as the **Startup Object** when the project runs. The following types are available:<br>Form<br>Class<br>Output menu item
|Startup Object | The object that the project invokes when it runs.
|Company | The default company that the project uses when it runs.
|Partition | The partition that the project uses when it runs.
|Project File | The name of the file that contains information about the project.
|Project Folder | The location of the project.
|Model | The model that the project is associated with. All elements in the project must be in the selected model.
|Model Publisher | A read-only value that indicates the publisher of the model.
|Layer | A read-only value that indicates the application layer that the model is located in.
|Synchronize database on build | A value that indicates whether the synchronize operation for tables is performed when the build action is performed for the project.

Of these properties, the **Model** property is particularly important. You must specify which model the project is associated with. All the elements that you create or add to the project must be part of this model. The **Startup Object type** and **Startup Object** properties are useful when you test and debug your application. When you start your project (by pressing F5 for debugging or Ctrl+F5 for no debugging), the specified form loads, or the **main()** method from the specified class runs. The method must have the following signature: `public static void main(Args _args)`.

## Add elements to a project

You can add existing elements to a project in several ways. Here are the most common methods:

- Select the project in Solution Explorer. Find the element in Application Explorer, right-click it, and then select **Add to Project**. This method is the simplest.
- Use drag-and-drop operations to add an element from Application Explorer to a project.
- If you limit your search results to a single model, you can add the results of a filter in Application Explorer to a project.

After you add the elements, you might want to use Solution Explorer to group them into folders, so that they're easier to find. The location of the project file and the folders that you create in the project don't affect the location of the XML files that represent the model elements. The model elements are always stored in the appropriate folder in the model store. To organize elements into folders, select the **Organize projects by element type** option. On the **Dynamics 365** menu, select **Options**. Select the **Projects** category to see this option. When you select this option, elements that you add to a new or existing project (such as when you add search results in Application Explorer to a project) are grouped into folders, based on the element type name. To create a new element for a project, follow these steps:

1. In Solution Explorer, right-click the project, point to **Add**, and then select **New Item**.
1. In the **Operations Artifacts** list, select the category of element to create.
1. Select the specific element type.
1. Enter a name for the element.
1. Select **Add**. The element is added to the project. It's also added to the model in the model store that the project is associated with.

After you add the new element, you might want to use Solution Explorer to move it into a folder in the project, so that it's easier to find.

## Export a project as an .axpp file

To transfer elements to a different installation, use a project package file. Project package files have the .axpp file name extension. A project package contains all the elements from the project. To export a project, follow these steps:

1. In Solution Explorer, select the project to export.
1. On the **Project** menu, select **Export Project**. (The command on the menu contains the name of the selected project.)
1. Enter a name for the project package file, and select a location.
1. Select **Save**.

## Import an .axpp file

To use the contents of a project package file, import the .axpp file into an installation. The import process adds the elements from the project package file into the same model that you exported them from. If the model doesn't exist in the installation, the import process creates it. To import a project package file, follow these steps:

1. On the **Dynamics 365** menu, select **Import Project**.
1. In the **Import Project** dialog box, specify the location of the project package (.axpp) file to import.
1. If you want elements from the project package file to overwrite any existing elements, select **Overwrite Elements**.
1. Specify whether you want to open the project in the current selection, in a new solution, or not at all.
1. In the **Details** field, review the elements that the import process adds. You can clear the check box next to any elements that you don't want to import.

    :::image type="content" source="./media/17_devotoolsconcept.png" alt-text="Screenshot of the Import project dialog.":::

1. Select **OK** to complete the import process.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
