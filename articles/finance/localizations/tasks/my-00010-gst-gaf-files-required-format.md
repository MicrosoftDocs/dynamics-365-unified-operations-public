--- 
# required metadata 
 
title: MY-00010 GST - Generate GAF files in the required format
description: This procedure walks you through generating the Malaysia GAF file. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ERWorkspace, ERSolutionTable, DefaultDashboard, LedgerParameters, EnumLookupForm_RU   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Malaysia
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# MY-00010 GST - Generate GAF files in the required format

[!include [banner](../../includes/banner.md)]

This procedure walks you through generating the Malaysia GAF file. You must be in the Accounting manager role to complete this procedure.  Before you can complete this procedure, you must have already uploaded your GAF format files into your active electronic reporting configuration. This procedure was created using the demo data company MYMF.


## Specify the GAF file format to use in the General ledger parameters
1. Go to General ledger > Ledger setup > General ledger parameters.
2. Click the Sales tax tab.
3. Expand or collapse the GST options section.
4. In the Format mapping field, click the drop-down button to open the lookup.
5. In the list, click the link in the selected row.
6. Click Save.

## Generate a GAF xml report for posted transactions
1. Go to Tax > Declarations > Sales tax > Generate GAF file.
2. In the Settlement period field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. In the From date field, enter a date.
6. In the Creation date field, enter a date.
7. In the Posting layer field, click the drop-down button to open the lookup.
8. In the list, find and select the desired record.
9. Click OK.
    * Save the GAF xml report.  
    * Click Save as and navigate to the location to save the file.    
    * Open and validate the GAF xml file.  
    * Click Open and select Internet explorer'.  Validate the GAF xml file and then close the xml file.    



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]