--- 
# required metadata 
 
title: Configure financial cross-company data sharing
description: This procedure shows how to configure, enable, validate, and resolve conflicts when sharing data between companies. 
author: aprilolson
manager: AnnBe 
ms.date: 06/22/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: margoc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Configure financial cross-company data sharing

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to configure, enable, validate, and resolve conflicts when sharing data between companies. It uses the USMF company and the Financial data sharing template.



This task guide requires Dynamics AX platform 7.1 or later.

1. Go to System administration > Workspaces > Data management.
2. Click Import.
3. In the Name field, type a value.
4. In the Source data format field, select the Package type.
    * Click Upload. Navigate to the location of the Financial data sharing template package file and select that file.  
5. Click Save.
6. In the list, mark the selected row.
    * Select the data sharing policy that was just created.  
7. Click Import.
8. Click Close.
9. Refresh the page.
10. Close the page.
11. Close the page.
12. Close the page.
13. Go to System administration > Setup > Configure cross-company data sharing.
14. In the list, find and select Payment days.
15. Click Add.
16. In the list, mark the selected row.
17. In the Company field, type 'USSI'.
18. Click Add.
19. In the Company field, type 'USMF'.
20. Click Save.
21. Click Enable.
22. Click Yes.
23. Click Find sharing issues.
24. Click Yes.
25. Click Update field value.
26. Click Use value from company 1.
27. Refresh the page.
28. Close the page.

