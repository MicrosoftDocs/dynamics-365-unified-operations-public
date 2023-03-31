--- 
# required metadata 
 
title: Configure credit card processing
description: This procedure walks through how to view the list of payment providers and how to configure a payment account for accounts receivable. 
author: jashanno
ms.date: 11/14/2016
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Configure credit card processing

[!include [banner](../includes/banner.md)]

This procedure walks through how to view the list of payment providers and how to configure a payment account for accounts receivable. This procedure uses the USRT company in demo data and is intended for Administrators and IT Professionals.


## View a list of payment providers
1. Go to Accounts receivable > Payments setup > Payment services.
2. Click View available providers.

## Configure payment account
1. Click New.
2. In the Payment service field, type a value.
3. In the Payment connector field, select an option.
4. Toggle the expansion of the Payment service account section.
5. In the Environment: field, type 'PROD'.
6. Click Credit card types.
7. In the Payment journal field, click the drop-down button to open the lookup.
8. In the list, click the link in the selected row.
9. Click Add.
10. In the Currency field, type a value.
11. In the list, find and select the desired record.
12. In the Payment journal field, click the drop-down button to open the lookup.
13. In the list, click the link in the selected row.
14. Click Add.
15. In the Currency field, type a value.
16. In the list, find and select the desired record.
    * You can repeat these steps for as many card types as you need.  
17. In the Payment journal field, click the drop-down button to open the lookup.
18. In the list, click the link in the selected row.
19. Click Add.
20. In the Currency field, type a value.
21. Click Save.
22. Close the page.
23. Click Validate.
24. Click the Default processor for new credit cards checkbox.
25. Click Save.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]