--- 
# required metadata 
 
title: Create a fixed asset
description: This task guide uses the USMF demo company. 
author: saraschi2
manager: AnnBe 
ms.date: 07/01/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: AssetTable, AssetBook   
audience: Application User 
# ms.devlang:  
ms.reviewer: roschlom
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create a fixed asset

[!include [banner](../../includes/banner.md)]

This procedure will create a new fixed asset using the **Fixed asset** list page.

You can also import fixed assets using the Excel add-in or by running an import job from the **Data management** workspace. Values for fields that are required for the import job should be entered into the templated before running the import. If you import asset records using the Excel add-in, the system will create a fixed asset record for each imported asset, and automatically increment the asset number for each one. The system will not automatically increment asset numbers for assets that are imported using the Data management workspace. In this case, an administrator must update the asset numbers manually. 

You do have the option to let the system assign the next asset number based on the number sequence that’s assigned to the fixed asset group. If you import assets using the fixed asset template using the Excel add-in or an import job, the system will create fixed asset records and increment the number automatically. 

1. Go to **Navigation pane > Modules > Fixed assets > Fixed assets > Fixed assets**.
2. On the **Action pane**, click **New**.
3. In **the Fixed asset group** field, enter or select a value. The **Number** field will default if you have enabled **Autonumber fixed assets functionality** in the **Fixed assets parameters** and the **Fixed asset group**.  If not, you must enter a unique number to identify the fixed asset.  
4. In the **Name** field, type a value. Enter the additional information that your business needs for this asset.  
5. On the **Action pane**, click **Books**.
6. In the **Acquisition date** field, enter a date.
7. In the **Acquisition price** field, enter a number.
    - Enter the additional information that your business needs for this book.  
    - Enter the additional information that your business needs for the remaining books.  
8. Close the page.

