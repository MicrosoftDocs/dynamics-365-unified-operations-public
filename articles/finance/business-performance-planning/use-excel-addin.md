---
title: Configure and use the Excel add-in for Business performance planning
description: Learn how to configure and use the Microsoft Excel add-in for Business performance planning and how to prepare your Excel files.
author: ShielaSogge
ms.author: twheeloc
ms.topic: how-to
ms.date: 06/22/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Configure and use the Excel add-in for Business performance planning

This article describes how to configure and use the Microsoft Excel add-in for Business performance planning.

The process of configuring and using the Excel add-in involves the following tasks:

1. Prepare your Excel file.
1. Connect to Dataverse, and load your data model into your Excel file.
1. Create a PivotTable that's based on your data model.
1. Begin planning in Excel.

## Prepare your Excel file

To prepare an Excel file to use the add-in, follow these steps:

1. Confirm that the Excel add-in is installed. For more information, see [Install the Excel add-in for business performance planning](install-excel-add.md).
1. In Business performance planning, go to the cube of your choice.
1. Select **Plan in Excel** to download the Excel file that sets the context for the cube.
1. Open the file, and select **Enable editing**.
1. On the Excel ribbon, notice that a **Planning** tab is added.

## Connect to Dataverse and load your data model

To connect to Dataverse and load a data model, follow these steps:

1. On the Excel ribbon, on the **Data** tab, select **Get data**.
1. Select **From database**, and then select **SQL server database**.
1. In the **Environment URL** field, enter your server. You can find this information in the **Details** section for the Power Platform environment.
1. Select **OK**.
1. Enter the same credentials that you use to sign in to the Business performance planning app, and then select **Connect**. After the connection is made, a **Navigator** window shows all the Dataverse tables in the environment.
1. Select the **Select multiple items** checkbox.
1. Search for and select your cube.
1. Select **Select related tables** to have the system automatically select all the dimensions.
1. Review the list of tables to be imported:
Power BI may also select system tables such as asyncoperation, processsession, or systemuser.
These tables aren't required for planning and should be unticked before loading.
To confirm what you import, select **Display Options** ▸ **Only selected items** in the **Navigator** panel.
Clear any text filters in the search bar to see all selected items.
1. Select **Load**. Your data model is loaded, and data is brought from Dataverse into your Excel workbook. The data load might take some time, depending on the volume of data in Dataverse.
1. Save your workbook.

## Create a PivotTable based on your data model

To create a PivotTable that's based on a data model, follow these steps:

1. On the Excel ribbon, on the **Insert** tab, select **Pivot table from data model**. Your cube and dimension tables appear.
1. Configure the PivotTable by bringing fact data, amounts, or values from your cube into the **Values** section.
1. Bring dimensions that describe the fact data in as rows, columns, and filters of your PivotTable. Examples of these dimensions include cost centers, scenarios, regions, or years.
1. Auto detect relationships between cube and dimension tables.

A message at the top of the PivotTable pane notifies you that there are no relationships between the tables. It prompts you to either auto detect the relationships or manually create them. Confirm that auto detect relationships accurately set up the relationships. The relationships are generally based on the primary key (ID field) in dimension tables. Occasionally, you might have to manually create the relationships.

## Begin planning

To begin planning by using a cube, follow these steps:

1. On the Excel ribbon, select the **Planning** tab if it isn't selected.
1. If you're in **Viewing** mode, switch to **Editing** mode. You're prompted to authenticate.
1. Based on your permissions and access, you can modify values in the PivotTable and then use the **Save** option to save your changes back to Dataverse.
1. Optional: You can modify the values at the top level (parent level) and/or the bottom level (child level) and apply allocations proportionately.
1. Optional: You can save the workbook locally and share it with coworkers to enable collaborative planning. Your coworkers must authenticate by using their credentials. They must also update the data from the **Data** tab of the Excel ribbon.
1. Optional: You can add comments to the cells that you're modifying the values for. These comments are workbook-specific and aren't stored on Dataverse. They aren't retained if a new workbook is downloaded or created from the Business performance planning app.

To begin planning by using dimensions, follow these steps:

1. On the Excel ribbon, on the **Planning** tab, select **Edit dimension**. A list of all the dimensions that you can view and edit is shown.
1. Select a dimension to open its contents on another worksheet.
1. Based on your permissions and access, you can modify the values, modify entire rows, add new rows, and delete rows. You can then save your changes back to Dataverse.
1. Optional: You can add comments to the cells that you're modifying the values for. These comments are workbook-specific and aren't stored in Dataverse. They aren't retained if a new workbook is downloaded or created from the Business performance planning app.
