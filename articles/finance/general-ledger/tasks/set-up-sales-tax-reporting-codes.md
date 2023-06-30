--- 
# required metadata 
 
title: Set up sales tax reporting codes
description: The Sales tax reporting codes refer to a field number that's listed on a sales tax report.  
author: twheeloc
ms.date: 08/08/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TaxReportCollection   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up sales tax reporting codes

[!include [banner](../../includes/banner.md)]

The **Sales tax reporting codes** refer to a field number that's listed on a sales tax report. They are used on country/region-specific report layouts. They're also used on the Sales tax payment by code report. That report shows sales tax amounts for a settlement period summarized for each reporting code. After you create **Sales tax reporting codes**, you can refer to those codes on the **Report setup** FastTabs, which you can access from the **Sales tax code** page. 

This recording uses the DEMF demo company.

1. In the **Navigation pane**, go to **Tax > Setup > Sales tax > Sales tax reporting codes**.
2. Click **New**.
3. Select the report layout that the reporting code belongs to. This layout is used to filter the available reporting codes for a sales tax code. Each sales tax code belongs to a settlement period, which belongs to a Sales tax authority, which uses a report layout.  
4. In the **Reporting code** field, enter a number.
5. In the **Report text** field, enter a description to display on reports.
6. In the **Brief description** field, enter a description for internal purposes.
7. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
