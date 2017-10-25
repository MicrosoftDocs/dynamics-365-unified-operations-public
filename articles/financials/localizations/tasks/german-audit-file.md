--- 
# required metadata 
 
title: Generate audit file (Germany)
description: This procedure shows how to generate the German audit file. 
author: mrolecki
manager: AnnBe 
ms.date: 02/18/2016
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
ms.search.region: Germany
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Generate audit file (Germany)

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to generate the German audit file. This procedure was created using the demo data company DEMF with Germany as the country/region of legal entity primary address.

1. Go to General ledger > Periodic tasks > Data export.
2. In the Format mapping field, enter or select a value.
    * If the list is empty, it means that there is no German audit file export format configuration imported and active. You must import a German audit file export format configuration before you can continue.  
3. Click OK.
4. In the Comment field, type a value.
5. In the Media field, type a value.
6. In the Version field, type a value.
7. In the Table Group field, enter or select a value.
    * For example, select 'Kunden' to export customer master data and transactions.  
8. In the Period - date from field, enter a date.
9. In the Period - date to field, enter a date.
10. Click OK.

