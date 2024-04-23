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
# Configure and use the Excel add-in for business performance planning

[!include [banner](../includes/banner.md)]
[!INCLUDE [PEAP](../../../includes/peap-3.md)]

This article provides answers to frequently asked questions about the Microsoft Excel add-in for business performance planning.

## I do not see the Business Performance AddIn on my downloaded Excel workbook even after installing it from my canvas business performance planning app? 

Follow the steps below to see the Add-in tab on your Excel workbook. 

Ensure you click on Enable Content when you open the downloaded excel workbook. 

If this does not work, follow the instructions below. 

Ensure any other Add-ins are disabled and restart Excel. 

File -> Options -> This will open Excel Options Window 

Select Add-ins 

Select Manage Com Add-ins and click Go. 

It will show you the available Add-ins, uncheck the other COM (Component Object Model) Add-ins and click on OK. 

Close all open Excel workbooks. 

Restart your downloaded Excel workbook. 

Click on Enable Content 

## When I connect to data, I cannot select the cube/dimension tables because the selection window is inconsistently empty. 

This issue occurs when you are working with multiple monitors or more than just your laptop screen. This is a known bug that we are actively working to resolve. There is a workaround in the meantime.  
Either drag the table selection window to your main monitor (laptop screen) and the user interface should appear and let you interact with it. 
 - Or -   
Duplicate your screen so you can begin interacting with table selections and authentication prompts. 

## After connecting to data, I only see my Cube data connected. What about my Dimension data? 
After connecting to your database server, make sure to select all the Dimension tables and Cube that you want to bring in to your data model on Excel. Alternatively,  
1. Check the box to select multiple items.
2. Select your Cube.
3. Click on Select related tables.
4. Wait until Excel selects everything and then click on Load. 

## After creating my pivot table, I am not able to modify values in the pivot table. I get an error that the source table name is incorrect. 

It's likely that the relationship between your cube and dimension tables are not set up correctly. For more information, see [Configure and use the Excel add-in for business performance planning]. 
