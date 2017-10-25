--- 
# required metadata 
 
title: Define financial dimensions
description: This task guide demonstrates adding an entity backed financial dimension and a custom financial dimension. 
author: aprilolson
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
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Define financial dimensions

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide demonstrates adding an entity backed financial dimension and a custom financial dimension.  The guide uses the USMF demo company.


## Create an entity backed financial dimension
1. Go to General ledger > Chart of accounts > Dimensions > Financial dimensions.
2. Click New.
3. In the User values from field, select a system-defined entity to base the financial dimension on. 
4. In the Dimension name field, type a value to describe the financial dimension.
    * The name can be different than the system-defined entity but cannot contain spaces or special characters.  
5. Click Activate.
    * Activating the financial dimension updates the table with the financial dimension name and removes deleted dimensions. You can enter dimension values before you activate a financial dimension, but a financial dimension cannot be used until it is activated.  
6. Click Close on the activation message.
7. Click Activate.
    * Dimension activation can be scheduled to run by batch at a specific date and time.  
8. Click Dimension values.
    * Some dimension values are company specific. You can verify if they are company specific by if the company name is showing in the dimension values list.  

## Create a custom financial dimension
1. Close the page.
2. Click New.
3. In the Use values from field, select <Custom dimension>.
4. In the Dimension name field, type a value to describe the financial dimension.
    * The name cannot contain spaces or special characters.  
    * You can also specify an account mask to limit the amount and type of information that you can enter for dimension values.   
    * You can enter characters that remain the same for each dimension value, such as letters or a hyphen. You can also enter number signs (#) and ampersands (&) as placeholders for letters and numbers that will change every time that a dimension value is created. Use a number sign (#) as a placeholder for a number and an ampersand (&) as a placeholder for a letter.  Example: To limit the dimension value to the letters CC and three numbers, you enter CC-### as the format mask.  
5. Click Activate.
    * Activating the financial dimension updates the table with the financial dimension name and removes deleted dimensions. You can enter dimension values before you activate a financial dimension, but a financial dimension cannot be used until it is activated.  
6. Click Activate.
    * Dimension activation can be scheduled to run by batch at a specific date and time.  
7. Click Dimension values.
8. Click New.
9. In the Dimension value field, type a name to describe your financial dimension value.
10. In the Description field, type a description that describes your financial dimension value.

