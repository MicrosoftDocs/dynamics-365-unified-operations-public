--- 
# required metadata 
 
title: Import OIOUBL electronic invoicing configurations
description: This procedure shows how to import OIOUBL electronic invoice configurations. 
author: mrolecki
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: ERWorkspace, ERVendorPart, ERSolutionRepositoryTable, ERSolutionImport   
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
# Import OIOUBL electronic invoicing configurations

[!include [banner](../../includes/banner.md)]

This procedure shows how to import OIOUBL electronic invoice configurations. 



This task was created using the demo data company USMF with the country/region of legal entity primary address updated to Denmark.



This is the first of six tasks that demonstrate the process of generating e-invoices using electronic reporting configurations. This task uses the OIOUBL e-invoice example, which is common for Denmark, Austria, and Norway.

1. Go to Organization administration > Workspaces > Electronic reporting.
2. In the list of Configuration providers, select Microsoft.
3. Click Set active.
4. Click Repositories.
5. Click Open.
6. Click Show filters.
7. Apply the following filters: Enter a filter value of "OIOUBL Sales invoice" on the "Configuration name" field using the "begins with" filter operator
8. Click Import.
9. Click Yes.
10. Apply the following filters: Enter a filter value of "OIOUBL Sales credit note" on the "Configuration name" field using the "begins with" filter operator
11. Click Import.
12. Click Yes.
13. Apply the following filters: Enter a filter value of "OIOUBL Project invoice" on the "Configuration name" field using the "begins with" filter operator
14. Click Import.
15. Click Yes.
16. Apply the following filters: Enter a filter value of "OIOUBL Project credit note" on the "Configuration name" field using the "begins with" filter operator
17. Click Import.
18. Click Yes.

