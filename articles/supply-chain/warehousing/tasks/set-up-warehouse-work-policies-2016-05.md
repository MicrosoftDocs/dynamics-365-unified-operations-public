--- 
# required metadata 
 
title: Set up warehouse work policies (Application, May 2016)
description: Warehouse processes don't always include warehouse work. 
author: johanhoffmann
manager: tfehr 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSWorkPolicy, WMSLocationIdLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up warehouse work policies (Application, May 2016)

[!include [banner](../../includes/banner.md)]

Warehouse processes don't always include warehouse work. By defining a work policy, you can prevent the creation of work for raw material picking and put-away of finished goods for a set of products at specific locations. The USMF demo data company was used to create this recording. This task guide requires Dynamics AX application 7.0.1 or later.

1. Go to Warehouse management > Setup > Work > Work policies.
2. Click New.
3. In the Work policy name field, type 'No put-away work'.
4. Click Save.
5. Click Add.
6. In the list, mark the selected row.
7. In the Work order type field, select 'Finished goods put away'.
8. Click Add.
9. In the list, mark the selected row.
10. In the Work order type field, select 'Co-product and by-product put away'.
11. Expand the Inventory locations section.
12. Click Add.
13. In the list, mark the selected row.
14. In the Warehouse list, enter '51'.
15. In the Location field, enter or select '001'.
16. Expand the Products section.
17. In the Product selection field, select 'Selected'.
18. Click Add.
19. In the list, mark the selected row.
20. In the Item number field, enter or select 'L0101'.
21. Click Save.

