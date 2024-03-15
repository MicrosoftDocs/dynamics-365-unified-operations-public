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
1. Prepare your Excel file. 
2. Connect to Dataverse and load your data model to your Excel file. 
3. Create a Pivot table based on your data model. 
4. Begin planning on Excel. 

## Prepare your Excel file

Ensure you have the AddIn installed. Learn more here on Installation (need to link it to Install AddIn page). 

Navigate to the cube of your choice on your business performance planning app and click on Plan in Excel. This will download the Excel file setting the context for the cube. 

Open the file and click Enable Editing. 

You should see the Planning tab on the Excel ribbon added. 

### Connect to Dataverse and load your data model

1. Navigate to Data tab on Excel ribbon and select Get Data.
2. Then select From Database and finally SQL server Database.
3. Enter your server as your Environment URL from your Power Platform environment Details section and click OK.
4. Use the same credentials that you use to login to your business performance planning application and click Connect.
5. Once it is connected, you will see Navigator window that will show you all your Dataverse tables in the environment.
6. Check the box for Select multiple items.
7. Search for your cube and select it.
8. Click Select Related Tables at the bottom of the window to select all the dimensions automatically and then click Load.
9. This will begin the process of loading your data model and bring in your data from dataverse to your Excel workbook.
10. It is recommended to save your workbook at this point since data load may take some time depending on the volume of data you have in dataverse. 

### Create a Pivot table based on your data model. 

1. Navigate to Insert tab on Excel ribbon and click on Pivot table From Data Model.
2. You should see your cube and dimension tables there.
3. Configure your Pivot table by bringing in your fact data (amount/values) from your cube to the values section of the pivot table.
4. Bring in dimensions that describe the fact data as rows, columns and filters of your pivot table such as cost centers, scenario, regions, Years etc. 

### Begin Planning 

Cube 
1. In case the Planning tab on the ribbon is not selected, you’d need to navigate to it. You are in Viewing mode currently, change it to Editing mode. It will prompt you to authenticate. Based on your permissions
and access, you should be able to modify values in the pivot table and save them back to Dataverse with the Save option in the Planning tab ribbon.
Optional: you should be able to modify the values at the top level (parent level) and/or the bottom level (children level) and apply allocations proportionately. 
Optional: You can save the workbook locally/on OneDrive/SharePoint and share with co-workers to plan collaboratively. Keep in mind they will need to authenticate with their credentials and refresh the data from
under the Data tab on your Excel ribbon. 
Optional: You can add comments to the cells that you are modifying the values for; however, the comments are workbook specific and do not get stored on Dataverse. Hence, they will not be retained if a new workbook
is downloaded/created from the business performance planning app. 

Dimensions 

1. Click on Edit dimension in the Planning tab ribbon. This will show you a list of all the dimensions that you can view and edit.
2. Select the dimension of your preference. It will open that dimension with its contents in another sheet.
3. Based on your access and permissions, you can modify the values, entire rows, add new rows and delete rows and save the changes back to Dataverse.
4. Optional: You can add comments to the cells that you are modifying the values for; however, the comments are workbook specific and do not get stored on Dataverse. Hence, they will not be retained if a new
workbook is downloaded/created from the business performance planning app. 
