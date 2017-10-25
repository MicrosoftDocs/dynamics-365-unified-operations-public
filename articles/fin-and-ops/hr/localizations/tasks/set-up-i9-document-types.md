--- 
# required metadata 
 
title: Set up I-9 document types
description: This procedure shows how to view and set up document types that are used for I-9 verification. 
author: ShielaSogge
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
ms.reviewer: rschloma
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shielas
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up I-9 document types

[!include[task guide banner](../../../includes/task-guide-banner.md)]

This procedure shows how to view and set up document types that are used for I-9 verification. Before you set up I-9 document types, you must also set up the issuing agencies and identification types. The demo data company used to create this procedure is USMF, which includes examples of the issue agencies and identification types that are needed to complete the procedure.

1. Go to Human resources > Workers > I-9 > I-9 document types.
2. Click New.
3. In the I-9 document type field, type a value.
    * Example: School ID.  
4. Select the identification type.  Example:  School ID
    * Examples of identification types include a Social Security number (SSN), visa number, passport ID, or driver's licence.  
5. Select the I-9 document list that is used for the document type.
    * As part of the I-9 process, employees must present documentation that shows the employer their identity and employment authorization. The US Citizenship and Immigration Services website contains information about which documents are acceptable, and which list they belong to.  http://www.uscis.gov  
6. In the Form field, Enter the official form number for the document type. Example: School ID.
    * The official form numbers can be found on the US Citizenship and Immigration Services website.  http://www.uscis.gov  
7. Check or uncheck the Active checkbox.
8. In the Expire field, set the date to '2019-10-27'.
    * The expiration date is optional.  
9. Select the agency that issued the document type. Example: Province/territory
10. Click Save.

