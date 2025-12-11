---
title: Create, edit, and browse Business process modeler (BPM) libraries
description: Learn about how to create or edit a BPM library and how to browse an existing library and import a section of another library.
author: johnmichalak
ms.author: johnmichalak
ms.topic: article
ms.date: 11/11/2025
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.dyn365.ops.version: 2012
---

# Create, edit, and browse Business process modeler (BPM) libraries

[!include [banner](../includes/banner.md)]

This article explains how to create, edit, and browse Business process modeler (BPM) libraries. You can browse a BPM library that is a global library or a corporate library. However, before you can edit and work with a BPM library, you must add it to your project in Microsoft Dynamics Lifecycle Services. Microsoft distributes libraries that appear under **Global libraries**, and your organization publishes libraries that appear under **Corporate libraries**.

  > [!NOTE]
  > BPM localization isn't supported. If you edit in the new BPM client in any language other than EN-US, your changes only display when you view the BPM in the language in which you made the changes. To view any changes made in EN-US, you must synchronize with Visual Studio Team Server before the changes display.

## Create a BPM library
You can create a BPM library in several ways. You can build one from scratch directly in the client or by importing an Excel template. You can also copy an existing library. This section describes each of these methods.

### Use the BPM client 

1. On the **Business process libraries** page, select **New library**.
     :::image type="content" source="./media/Select_new_library.PNG" alt-text="Screenshot of New library.":::
1. Enter a name for the new library, then select **Create**.
     :::image type="content" source="./media/Create_new_library.PNG" alt-text="Screenshot of Create new library.":::
    
### Use Excel Import

1. On the **Business process libraries** page, select **Import from Excel**.
     :::image type="content" source="./media/Import_from_Excel.PNG" alt-text="Screenshot of Import from Excel.":::
1. Select **Download template** from the pane. When the template downloads, open the file.
1. The template has several columns, most importantly **Id, and **Parent Id**. Assign each line a new ID number. If you want to make a line a child item, add the ID of the line you'd like it to fall under in the **Parent Id** column. 
1. When you're done, save the template and return to BPM.
1. In the import pane, select **Browse** to upload the updated template. Enter a name for the new library, then select **Import**. 
    :::image type="content" source="./media/Download_template.PNG" alt-text="Screenshot of Download template.":::
 
### Copy a library 

1. Open the **Business process libraries** page. 
1. On the tile for the library that you want to copy, select the ellipsis button (…), and then select **Copy**.
    :::image type="content" source="./media/Copy_a_library.PNG" alt-text="Screenshot of Copy library.":::
1. Enter a name for the library, and then select **Create**.
    :::image type="content" source="./media/Create_a_copied_library.PNG" alt-text="Screenshot of Create copied library.":::


## Import a section of another library
1. Open the **Business process libraries** page, and then open the library you want to edit. 
1. Navigate to the line you would like to import to and select **Import**.
     :::image type="content" source="./media/Select_import.PNG" alt-text="Screenshot of Select import.":::
1. Select **As child** or **As sibling**.
     :::image type="content" source="./media/Select_child_or_sibling.PNG" alt-text="Screenshot of Select child or sibling.":::
1. In the pane, choose the library you would like to import from and select **Import**.
     :::image type="content" source="./media/Choose_library.PNG" alt-text="Screenshot of Choose library.":::


## Add a new process

1. In the BPM library, select an existing process.
1. Select **Add process**. You can select to add the process as a child or a sibling of the selected process node. In this way, you can create a semantic hierarchy of business processes.

    :::image type="content" source="./media/NEWBPM_BlogPost06.png" alt-text="Screenshot of Adding a process.":::

## Edit the properties of a process

1. In the BPM library, select the process node to edit.
1. In the right pane, on the **Overview** tab, select **Edit mode**.
1. Enter a name and description for the process node.
1. Select the industries and the countries or regions that the process applies to. You can also add keywords and links. Keywords let you define categories, work streams, or other metadata. Links (URLs) let you reference external sites or documentation.

    :::image type="content" source="./media/NEWBPM_BlogPost08-194x300.png" alt-text="Screenshot of Process properties.":::

1. When you finish editing the properties, select **Save**.

## Move a process

You can move a process node or assign it to another parent node in the BPM hierarchy.

1. Select the process node to move, and then select **Move process**. You can select to move the process up or down, or you can select **Move** to see more options.

    :::image type="content" source="./media/NEWBPM_BlogPost09.png" alt-text="Screenshot of Moving a process.":::

1. If you selected **Move**, you can browse the hierarchy, select a node to move the process to, and then select **Move as child** or **Move as sibling**. To cancel the move operation, select **Cancel**.

## Delete a process

To delete a business process, select the process to delete, and then select **Delete**.

## Copy a global or corporate library to your project

You can browse a BPM library that is a global library or a corporate library. However, before you can edit and work with a BPM library, it must be part of your project in Microsoft Dynamics Lifecycle Services. Libraries that are distributed by Microsoft appear under **Global libraries**, whereas libraries that are published by your organization appear under **Corporate libraries**.

## Browse a BPM library

1. On the **Business process libraries** page, double-click the tile for the library that you want to browse.
1. In the BPM library, select a process to view its substeps.

    :::image type="content" source="./media/2.PNG" alt-text="Screenshot of Process and its substeps.":::

1. Use the buttons on the toolbar to add, delete, or import processes as a child or a sibling. You can also select **Collapse all** to view only parent processes. 

    :::image type="content" source="./media/3.PNG" alt-text="Screenshot of Toolbar.":::

## Search a BPM library

You can search for words or phrases in your BPM library. The search functionality searches the names and descriptions of business processes.

- To search for a _word_, enter the search word in the search box, and then press Enter.
- To search for a _phrase_, put double quotation marks around the search phrase.

    For example, enter **technology** (word) or **"information technology"** (phrase) in the search box.

- You can also search for Application Object Tree (AOT) elements that are part of the task recordings that are in your library. Typically, these AOT elements are the names of pages or menu items. When you search for an AOT element, prefix it with a dollar sign ($). For example, enter **$CustTable** in the search box.

:::image type="content" source="./media/searching.png" alt-text="Screenshot of Search box.":::
