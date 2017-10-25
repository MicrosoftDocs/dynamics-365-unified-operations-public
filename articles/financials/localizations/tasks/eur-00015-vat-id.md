--- 
# required metadata 
 
title: Set up VAT ID
description: This procedure walks you through VAT ID registration prerequisites, such as setting up a registration type and assigning it to a registration category. 
author: v-oloski
manager: AnnBe 
ms.date: 10/25/2016
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
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
# ms.search.industry: 
ms.author: v-oloski
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up VAT ID

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure walks you through VAT ID registration prerequisites, such as setting up a registration type and assigning it to a registration category. You can find additional information about registration IDs and registration ID processing, including required prerequisites, in the Registration IDs help topic. 

The information here applies to all European countries/regions. The task was created using the demo data company DEMF with Germany as the legal entity primary address. This task is intended for system administrators. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

1. Go to Organization administration > Global address book > Registration types > Registration types.
2. Click New to open the drop dialog.
3. In the Name field, type 'VAT ID'.
4. In the Description field, VAT number.
5. In the Country/region field, enter or select a value DEU
6. Select Yes in the Unique field.
    * Select this check box to verify if the VAT ID is unique.  
7. Select Yes in the Primary for country field.
    * Select this check box if the VAT ID should be effective for all addresses belonging to the specified country/region.  
8. Click Create.
9. Click Add.
10. In the Country/region field, enter or select a value ITA
11. In the Format field, type '###########'.
    * When you enter a registration ID of this type for the selected country/region, the registration ID will be verified against this format.  
12. Select the Unique check box.
    * Select this check box to verify if the VAT ID is unique.  
13. Select the Primary for country check box.
    * Select this check box if the VAT ID should be effective for all addresses belonging to the specified country/region.  
14. Click Save.
15. Go to Organization administration > Global address book > Registration types > Registration categories.
16. Click New.
17. In the Country/region field, enter or select a value VAT ID, DEU
18. In the Registration category field, select 'VAT ID'.
    * Assign the registration type that you created earlier to a predefined Registration category.  
19. Click New.
20. In the Country/region field, enter or select a value VAT ID, ITA
21. In the Registration category field, select 'VAT ID'.
    * Assign the registration type that you created to a predefined registration category.  
22. Click Save.

