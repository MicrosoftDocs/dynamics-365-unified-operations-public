---
# required metadata

title: Business performance planning excel add-in FAQ
description: This article provides answers to frequently asked questions about the Microsoft Excel add-in for business performance planning.
author: ShielaSogge
ms.date: 04/23/2024
ms.topic: article
ms.reviewer: twheeloc

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
# Excel add-in for business performance planning FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about the Microsoft Excel add-in for business performance planning.

## I don't see the Business performance add-in on my downloaded Excel workbook after installing it from my business performance planning app? 

To see the add-in tab on your Excel workbook, follow these steps:
 - Click **Enable content** when you open the downloaded excel workbook. 

If this doesn't work, follow the instructions below. 
1. Confirm other add-ins are disabled and restart Excel.
2. **File** > **Options**. This opens Excel options.
3. Select **Add-ins**.
4. Select **Manage com add-ins**, click **Go**.
5. The available add-ins are displayed. Uncheck the other COM (Component Object Model) add-ins, click **OK**.
6. Close all open Excel workbooks.
7. Restart your downloaded Excel workbook.
8. Click **Enable content**. 

## When I connect to data, I can't select the cube/dimension tables because the selection window is inconsistently empty. 

This issue occurs when working with multiple monitors or more than just your laptop screen. This is a known bug that is being actively worked on to resolve. 
To work around this issue:
Either drag the table selection window to your main monitor (laptop screen). The user interface should appear. 
 - Or -   
Duplicate your screen and begin interacting with table selections and authentication prompts. 

## After connecting to data, I only see my Cube data connected. What about my Dimension data? 
After connecting to your database server, confirm that all the Dimension tables and Cube that you want to bring into your data model in Excel are selected. 
You can also follow these steps:  
1. To select multiple items, check the box.
2. Select your Cube.
3. Click **Select related tables**.
4. Wait until Excel selects everything. Click **Load**. 

## After creating my pivot table, I'm not able to modify values in the pivot table. I get an error that the source table name is incorrect. 
The relationship between your cube and dimension tables aren't set up correctly. For more information, see [Configure and use the Excel add-in for business performance planning](use-excel-addin.md). 
