--- 
# required metadata 
 
title: Run a format that uses horizontally-expandable ranges to dynamically add columns in Excel reports for electronic reporting (ER)
description: The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to generate reports as OPENXML worksheets (Excel) files in which the required columns can be created dynamically as horizontally expandable ranges. 
author: NickSelin
manager: AnnBe 
ms.date: 10/28/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Run a format that uses horizontally-expandable ranges to dynamically add columns in Excel reports for electronic reporting (ER)

[!include[task guide banner](../../includes/task-guide-banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to generate reports as OPENXML worksheets (Excel) files in which the required columns can be created dynamically as horizontally expandable ranges. These steps can be performed in the DEMF company.

To complete these steps, you must first complete the steps in the “ER Use horizontally expandable ranges to dynamically add columns in Excel reports (Part 1: Design format)” procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Find created format
1. Go to Organization administration > Electronic reporting > Configurations.
2. In the tree, expand 'Financial dimensions sample model'.
3. In the tree, select 'Financial dimensions sample model\Sample report with horizontally expandable ranges'.

## Execute format to create Excel output
1. Click Run.
2. In the Dimension name field, type 'BusinessUnit;CostCenter;Department'.
    * In the Dimension name field, enter or select a value.  To select all dimensions for the current company, enter the following:  BusinessUnit;CostCenter;Department;ItemGroup;MainAccount;Project  
3. Expand the Records to include section.
4. Click Filter.
5. Select the row for the Ledger journal table and the Journal batch number field.
6. In the Criteria field, type '00057..00058'.
    * 00057..00058  
7. Click OK.
8. Click OK.
    * Review the generated output. Note that the newly created Excel file contains the same number of columns that were selected for financial dimensions. The report header in those columns represents financial dimensions’ names. The transactions’ lines in those columns represent financial dimensions. Run this report and select different dimensions to see that the report is not dependent on the number of selected dimensions or the number of dimensions configured for this Dynamics 365 for Finance and Operations, Enterprise edition instance.  

