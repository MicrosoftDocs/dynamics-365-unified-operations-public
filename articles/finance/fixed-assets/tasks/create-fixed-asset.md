--- 
# required metadata 
 
title: Create a fixed asset
description: This topic lists the steps for creationg a new fixed asset record from the **Fixed asset** list page. 
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

This topic lists the steps for creationg a new fixed asset record from the **Fixed asset** list page.

The system will assign the asset number based on the number sequence that’s assigned to the fixed asset group. If you use the fixed asset template to import assets with  the Excel add-in, or use another an import job, the system will create fixed asset records and increment the asset number automatically. To manually create an asset record, complete the following steps. 

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

You can also import fixed assets using the Excel add-in or by running an import job from the **Data management** workspace. Enter the values for required fields into the template before running the import. 

If you didn't define the fixed asset number in the template of Excel add-in or in Data management the system will create a fixed asset number for each imported asset,  and automatically increment the next number sequence for each one. However, if you import assets and define asset numnbers in the template, the system *will not* automatically increment the next number sequence. In this case, an administrator might need to update the next number sequence manually. But if you decided to define the fixed asset number in Excel add-in template the system will use the defined fixed asset number and increment the next number sequence.
