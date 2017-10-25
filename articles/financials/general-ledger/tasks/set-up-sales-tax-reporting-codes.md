--- 
# required metadata 
 
title: Set up sales tax reporting codes
description: The Sales tax reporting codes refer to a field number on a sales tax report. 
author: twheeloc
manager: AnnBe 
ms.date: 11/14/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up sales tax reporting codes

[!include[task guide banner](../../includes/task-guide-banner.md)]

The Sales tax reporting codes refer to a field number on a sales tax report. They are used on country specific report layouts and the Sales tax payment by code report to print sales tax amounts for a settlement period summarized per reporting code. After you create Sales tax reporting codes, you can refer to them on the Report setup FastTabs in the Sales tax code page. 

This recording uses the DEMF demo company.



1. Go to Tax > Setup > Sales tax > Sales tax reporting codes.
2. Click New.
3. Select the report layout that the reporting code belongs to.
    * This layout is used to filter the available reporting codes for a Sales tax code. Each Sales tax code belongs to a settlement period which belongs to a Sales tax authority which uses a Report layout.  
4. Enter a number that refers to a field on a sales tax report.
5. In the Report text field, enter a description to display on reports.
6. In the Brief description field, enter a description for internal purposes.
7. Click Save.

