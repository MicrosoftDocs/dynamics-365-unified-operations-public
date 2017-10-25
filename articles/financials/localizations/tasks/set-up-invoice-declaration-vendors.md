--- 
# required metadata 
 
title: Set up an invoice declaration for vendors (Iceland)
description: This procedure walks you through setting up the Icelandic invoice declaration. 
author: mrolecki
manager: AnnBe 
ms.date: 05/09/2016
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
ms.search.region: Iceland
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up an invoice declaration for vendors (Iceland)

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure walks you through setting up the Icelandic invoice declaration. The demo data company used to create this procedure is DEMF with the country of legal entity primary address updated to Iceland.


## Import invoice declaration GER configurations
1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Set active.
3. Click Repositories.
4. Click Open.
5. Click Show filters.
    * Please add a criterion to filter by the Configuration name and enter Vendor invoice declaration (IS) or find the configuration in the list, select it and move to the next step.  
6. Apply the following filters: %3
7. Click Import.
8. Click Yes.
9. Add filter
    * Add a criterion to filter by the Configuration name and enter Vendor invoice declaration report (IS) or find the configuration in the list, select it and move to the next step.  
10. Apply the following filters: %3
11. Click Import.
12. Click Yes.

## Enable vendor invoice declaration
1. Go to Accounts payable > Setup > Vendor invoice declaration.
2. Click New.
3. In the Invoice declaration field, type 'SubC'.
4. In the Description field, type 'Sub-contractor'.
5. In the Reporting code field, type '06'.
6. Click New.
7. In the Invoice declaration field, type 'Gift'.
8. In the Description field, type 'Gifts'.
9. In the Reporting code field, type '34'.
10. In the Record type field, select 'LA'.
11. Click Save.

