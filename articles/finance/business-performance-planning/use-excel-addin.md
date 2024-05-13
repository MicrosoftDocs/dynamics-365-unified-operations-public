---
title: Configure and use the Excel add-in for business performance planning
description: Learn how to configure and use the Microsoft Excel add-in for business performance planning and how to prepare your Excel files.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 04/23/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Configure and use the Excel add-in for business performance planning

This article describes how to configure and use the Microsoft Excel add-in for business performance planning.

The process of configuring and using the Excel add-in involves the following tasks:

1. Prepare your Excel file.
2. Connect to Dataverse, and load your data model into your Excel file.
3. Create a PivotTable that's based on your data model.
4. Begin planning in Excel.

## Prepare your Excel file

To prepare an Excel file to use the add-in, follow these steps.

1. Confirm that the Excel add-in is installed. For more information, see [Install the Excel add-in for business performance planning](install-excel-add.md).
2. In business performance planning, go to the cube of your choice.
3. Select **Plan in Excel** to download the Excel file that sets the context for the cube.
4. Open the file, and select **Enable editing**.
5. On the Excel ribbon, notice that a **Planning** tab has been added.

## Connect to Dataverse and load your data model

To connect to Dataverse and load a data model, follow these steps.

1. On the Excel ribbon, on the **Data** tab, select **Get data**.
2. Select **From database**, and then select **SQL server database**.
3. In the **Environment URL** field, enter your server. You can find this information in the **Details** section for the Power Platform environment.
4. Select **OK**.
5. Enter the same credentials that you use to sign in to the business performance planning app, and then select **Connect**. After the connection is made, a **Navigator** window shows all the Dataverse tables in the environment.
6. Select the **Select multiple items** checkbox.
7. Search for and select your cube.
8. Select **Select related tables** to have the system automatically select all the dimensions.
9. Select **Load**. Your data model is loaded, and data is brought from Dataverse into your Excel workbook. The data load might take some time, depending on the volume of data in Dataverse.
10. We recommend that you save your workbook at this point.

## Create a PivotTable based on your data model

To create a PivotTable that's based on a data model, follow these steps.

1. On the Excel ribbon, on the **Insert** tab, select **Pivot table from data model**. Your cube and dimension tables should be shown.
2. Configure the PivotTable by bringing fact data, amounts, or values from your cube into the **Values** section.
3. Bring dimensions that describe the fact data in as rows, columns, and filters of your PivotTable. Examples of these dimensions include cost centers, scenarios, regions, or years.
4. Auto detect relationships between cube and dimension tables.

A message at the top of the PivotTable pane notifies you that there are no relationships between the tables. It prompts you to either auto detect the relationships or manually create them. Confirm that auto detect relationships accurately set up the relationships. The relationships are generally based on the primary key (ID field) in dimension tables. Occasionally, you might have to manually create the relationships.

## Begin planning

To begin planning by using a cube, follow these steps.

1. On the Excel ribbon, select the **Planning** tab if it isn't selected.
2. If you're in **Viewing** mode, switch to **Editing** mode. You're prompted to authenticate.
3. Based on your permissions and access, you can modify values in the PivotTable and then use the **Save** option to save your changes back to Dataverse.
4. Optional: You should be able to modify the values at the top level (parent level) and/or the bottom level (child level) and apply allocations proportionately.
5. Optional: You can save the workbook locally and share it with coworkers to enable collaborative planning. Your coworkers must authenticate by using their credentials. They must also update the data from the **Data** tab of the Excel ribbon.
6. Optional: You can add comments to the cells that you're modifying the values for. These comments are workbook-specific and aren't stored on Dataverse. They aren't retained if a new workbook is downloaded or created from the business performance planning app.

To begin planning by using dimensions, follow these steps.

1. On the Excel ribbon, on the **Planning** tab, select **Edit dimension**. A list of all the dimensions that you can view and edit is shown.
2. Select a dimension to open its contents on another worksheet.
3. Based on your permissions and access, you can modify the values, modify entire rows, add new rows, and delete rows. You can then save your changes back to Dataverse.
4. Optional: You can add comments to the cells that you're modifying the values for. These comments are workbook-specific and aren't stored in Dataverse. They aren't retained if a new workbook is downloaded or created from the business performance planning app.
