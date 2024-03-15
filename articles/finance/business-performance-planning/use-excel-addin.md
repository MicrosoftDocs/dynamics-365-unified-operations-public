---
# required metadata

title: Configure and use the Excel add-in for business performance planning 
description: This article describes how to configure and use the Excel add-in for business performance planning. 
author: ShielaSogge
ms.date: 03/15/2024
ms.topic: article

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2023-12-03
ms.dyn365.ops.version: 

---
# Configure and use the Excel add-in for business performance planning 

This article describes how to configure and use the Excel add-in for business performance planning. 

The process of configuring and using the Excel add-in involves the following tasks: 
 - Prepare your Excel file
 - Connect to Dataverse and load your data model to your Excel file
 - Create a pivot table based on your data model
 - Begin planning in Excel

## Prepare your Excel file
To prepare your Excel file to use the add-in, follow these steps:
1. Confirm the Excel add-in is installed. For more information, see [Install the Excel add-in for business performance planning](install-excel-add.md).
2. In business performance planning, go to the cube of your choice.
3. Click **Plan in Excel**. This downloads the Excel file setting the context for the cube.
4. Open the file and click **Enable editing**.
5. On the Excel ribbon, a **Planning** tab as been added. 

### Connect to Dataverse and load your data model

To connect to dataverse and load a data model, follow these steps:
1. Go to the **Data** tab on the Excel ribbon.
2. Select **Get data**.
3. Select **From database** and then **SQL server database**.
4. Enter your server in the **Environment URL** field from the Power Platform environment **Details** section.
5. Click **OK**.
6. Use the same credentials that you log into your business performance planning application and click **Connect**.
7. After it's connected, a **Navigator** window displays all Dataverse tables in the environment.
8. Check **Select multiple items**.
9. Search and select your cube.
10. Click **Select related tables** to select all the dimensions automatically.
11. Click **Load**. This begins loading your data model and bringing data from dataverse to your Excel workbook.
It's recommended to save your workbook at this point. The data load may take some time depending on the volume of data in dataverse. 

### Create a pivot table based on your data model

To create a pivot table based on a data model, follow these steps:
1. Go to the **Insert** tab in Excel.
2. Click **Pivot table from data model**. Your cube and dimension tables should be displayed.
3. Configure the pivot table by bringing in fact data, amounts or values, from your cube to the **Values** section of the pivot table.
4. Bring in dimensions that describe the fact data as rows, columns, and filters of your pivot table such as cost centers, scenario, regions, or years. 

### Begin planning 

To begin planning, use a cube:
1. In case the **Planning** tab isn't selected, navigate to it. If you are in **Viewing** mode, change it to **Editing** mode. It will prompt you to authenticate. Based on your permissions and access, you should be able to modify values in the pivot table and save them back to Dataverse with the **Save** option.
2. Optional - you should be able to modify the values at the top level (parent level) and/or the bottom level (children level) and apply allocations proportionately.
3. Optional - you can save the workbook locally and share with co-workers to plan collaboratively. They'll need to authenticate with their credentials and refresh the data from the **Data** tab on your Excel ribbon.
4. Optional - you can add comments to the cells that you are modifying the values for. The comments are workbook specific and aren't stored on Dataverse. They're not retained if a new workbook is downloaded/created from the business performance planning app. 

To begin planning, use dimensions: 

1. Click **Edit dimension** on the **Planning** tab ribbon. This shows you a list of all the dimensions that you can view and edit.
2. Select a dimension to open its contents in another sheet.
3. Based on your access and permissions, you can modify the values, entire rows, add new rows and delete rows and save the changes back to Dataverse.
4. Optional: You can add comments to the cells that you are modifying the values for. The comments are workbook specific and aren't stored in Dataverse. They're not retained if a new workbook is downloaded/created from the business performance planning app. 
