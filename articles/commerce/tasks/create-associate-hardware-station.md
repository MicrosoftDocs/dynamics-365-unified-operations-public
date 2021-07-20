--- 
# required metadata 
 
title: Create and associate a hardware station
description: This procedure walks through how to create a new hardware station. 
author: jashanno
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: RetailHardwareStation, RetailStoreTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create and associate a hardware station

[!include [banner](../includes/banner.md)]

This procedure walks through how to create a new hardware station. A new hardware profile will be created and used to add new hardware stations to a pre-defined store (channel). This procedure uses the USRT company in demo data.

1. Go to Commerce essentials > Channels > .. > .. > .. > Hardware station profiles.
2. Click New.
3. In the Hardware station ID field, type 'TestHWProfile'.
4. In the Name field, type a value.
5. In the Port number field, enter a number.
6. In the Hardware profile field, click the drop-down button to open the lookup.
7. In the list, find and select the desired record.
8. In the list, click the link in the selected row.
9. In the Package name field, click the drop-down button to open the lookup.
10. In the list, click the link in the selected row.
    * This is the standard package that comes with a new environment. The version number may vary.  
11. Click Save.
12. Close the page.
13. Go to Retail and Commerce > Channels > All stores.
14. In the list, select row 17.
    * If you are using the USRT demo data company, this is the Houston store.  
15. In the list, click the link in the selected row.
16. Toggle the expansion of the Hardware stations section.
17. Click Add.
18. In the list, mark the selected row.
19. In the Profile ID field, click the drop-down button to open the lookup.
20. In the list, find and select the desired record.
    * This must be the new hardware station profile that was created in the previous steps.  
21. In the list, click the link in the selected row.
22. In the Host name field, type a value.
23. In the EFT terminal ID field, type a value.
24. Click Save.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]