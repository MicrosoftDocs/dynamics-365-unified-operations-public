--- 
# required metadata 
 
title: Set up OIOUBL electronic invoicing
description: This procedure walks you through setting up OIOUBL electronic invoicing. 
author: mrolecki
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustParameters, OMLegalEntity, UnitOfMeasure, ExtCodeTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Denmark
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up OIOUBL electronic invoicing

[!include [banner](../../includes/banner.md)]

This procedure walks you through setting up OIOUBL electronic invoicing. 



This task was created using the demo data company USMF with the country/region of legal entity primary address updated to Denmark.



This is the second procedure, out of six, that demonstrates the process of generating e-invoices using electronic reporting configurations. This task uses the OIOUBL e-invoice example, which is common for Denmark, Austria, and Norway.

Before you can complete this task, you must import the OIOUBL electronic invoicing electronic reporting configurations.


## Set up electronic invoice formats
1. Go to Accounts receivable > Setup > Accounts receivable parameters.
2. Click the Electronic documents tab.
3. Expand the Electronic reporting section.
4. In the Sales and Free text invoice field, enter or select a value.
    * Choose the electronic reporting format that represents the required document. You might have separate format configurations per document type or one configuration for all document types.  
5. In the Sales and Free text credit note field, enter or select a value.
    * Choose the electronic reporting format that represents the required document. You might have separate format configurations per document type or one configuration for all document types.  
6. In the Project invoice field, enter or select a value.
    * Choose the electronic reporting format that represents the required document. You might have separate format configurations per document type or one configuration for all document types.  
7. In the Project credit note field, enter or select a value.
    * Choose the electronic reporting format that represents the required document. You might have separate format configurations per document type or one configuration for all document types.  
8. Click Save.

## Set up a legal entity
1. Go to Organization administration > Organizations > Legal entities.
2. Click Edit.
3. Expand the Bank account information section.
4. In the Routing number field, type a value.
    * For example, enter 12070918.  
5. Expand the Tax registration section.
6. In the Tax registration number field, type a value.
    * For example, enter 55568510.  

## Set up external codes for units of measure
1. Go to Organization administration > Setup > Units > Units.
2. Use the Quick Filter to find records. For example, filter on the Unit field with a value of 'pcs'.
3. Click External codes.
4. In the list, mark the selected row.
5. In the Code field, type a value.
    * For example, enter PCSEA.  
6. In the External code definition field, type a value. For example, OIOUBL EA code..
7. Select the Standard code check box.
8. Click Add.
9. In the Value field, type a value.
    * For example, enter EA.  
10. Click Save.

