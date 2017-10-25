--- 
# required metadata 
 
title: Set up PIS and COFINS tables (Brazil)
description: Before the PIS and COFINS tax assessment can be created, you must set up the tables for the credit source and credit type. 
author: sndray
manager: AnnBe 
ms.date: 06/26/2017
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
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up PIS and COFINS tables (Brazil)

[!include[task guide banner](../../includes/task-guide-banner.md)]

Before the PIS and COFINS tax assessment can be created, you must set up the tables for the credit source and credit type. As a reference, you should use tables 4.3.7 and 4.3.6 that are published by the tax authority. This task uses the BRMF demo company.

1. Go to Fiscal books > Setup > PIS and COFINS tables > CFOP and Credit base source.
2. Click New.
3. In the CFOP field, type a value.
    * Use table 4.3.7 that is published by the tax authority as a reference to enter the values of credit sources by CFOP for the PIS and COFINS tax assessment.  
4. In the CFOP description field, type a value.
5. In the Credit base source field, select an option.
6. In the Valid From Date field, enter a date.
7. Click Save.
8. Close the page.
9. Go to Fiscal books > Setup > PIS and COFINS tables > Credit types.
10. Click New.
11. In the Credit type field, type a value.
    * Use table 4.3.6 that is published by the tax authority as a reference to enter the values of credit types for the PIS and COFINS tax assessment.  
12. In the Description field, type a value.
13. In the Valid From Date field, enter a date.
14. Click Save.
15. Close the page.

