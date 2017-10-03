--- 
# required metadata 
 
title: Set up Japan consumption tax report (Japan)
description: This task walks you through setting up the system to support the Japan consumption tax report. 
author: ShylaThompson
manager: AnnBe 
ms.date: 02/15/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up Japan consumption tax report (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task walks you through setting up the system to support the Japan consumption tax report. In this task, you will modify General ledger parameters, a legal entity, sales tax reporting accounts and a sales tax code. 

This task was created using the demo data company JPMF.




## Enable the consumption tax report
1. Go to Tax > Setup > Parameters > General ledger parameters.
2. Click the Sales tax tab.
3. Expand the Japanese tax reporting section.
4. Select Yes in the Consumption tax reports field.

## Tax reporting accounts
1. Go to Tax > Setup > Sales tax > Tax reporting accounts.
2. Click Edit.
3. In the Bad debt field, specify the desired values.
    * Example: 84720  
4. In the Collected bad debt field, specify the desired values.
    * Example: 84710  

## Enter Japan reporting information for a legal entity
1. Go to Organization administration > Organizations > Legal entities.
2. Expand the Registration numbers section.
3. Click Edit.
4. In the Accounting personnel field, type a value.
5. In the Company representative field, type a value.

## Enter report setup information for a sales tax code
1. Go to Tax > Indirect taxes > Sales tax > Sales tax codes.
2. Use the Quick Filter to find records. For example, filter on the Sales tax code field with a value of 'JP Cons'.
3. Expand the Report setup section.
4. Click Edit.
    * Confirm the reporting codes were configured properly.   

