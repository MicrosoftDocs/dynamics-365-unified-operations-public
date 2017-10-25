--- 
# required metadata 
 
title: Issue ICMS tax credit fiscal documents (Brazil)
description: You can create a new tax fiscal document and generate a Nota Fiscal eletrônica (NF-e). 
author: sndray
manager: AnnBe 
ms.date: 06/24/2017
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
ms.search.industry: Manufacturing;Distribution;Service industries
ms.author: sndray
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Issue ICMS tax credit fiscal documents (Brazil)

[!include[task guide banner](../../includes/task-guide-banner.md)]

You can create a new tax fiscal document and generate a Nota Fiscal eletrônica (NF-e). When you post the document, an NF-e XML message is generated and submitted to the Secretaria da Fazenda (SEFAZ). This task uses the BRMF demo company.

1. Go to General ledger > Journal entries > All tax fiscal documents.
2. Click New.
3. In the Tax fiscal document type field, select an option.
    * Select the type of tax transfer fiscal document, either ICMS tax transfer between fiscal establishments or ICMS tax credit installment.  
4. In the Fiscal establishment ID field, enter or select a value.
5. In the Account type field, select an option.
    * While you're doing an ICMS tax transfer, select a vendor to receive the tax credit from another fiscal establishment, or select a customer to transfer the tax credit to another fiscal establishment.  
6. In the Account number field, enter or select a value.
    * The fiscal establishment must be a vendor or customer.  
7. In the Document model field, enter or select a value.
8. In the Access key field, type a value.
9. In the Date field, enter a date.
10. Click Save.
11. Click Add line.
12. In the Item description field, type a value.
13. In the list, mark the selected row.
14. In the CFOP field, enter or select a value.
15. In the Sales tax code field, enter or select a value.
16. In the Amount field, enter a number.
17. Click Save.
18. Click Post.
19. Click OK.
20. Close the page.
21. Close the page.

