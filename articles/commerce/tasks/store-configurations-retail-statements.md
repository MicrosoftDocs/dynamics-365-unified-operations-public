--- 
# required metadata 
 
title: Store configurations for Retail statements
description: This procedure walks through configurations for the store that affect how Commerce statements get created and posted. 
author: jashanno
ms.date: 08/08/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: RetailStoreTable   
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
# Store configurations for Retail statements

[!include [banner](../includes/banner.md)]

This procedure walks through configurations for the store that affect how Commerce statements get created and posted. Financial dimensions on stores are covered in another procedure. This procedure uses the USRT demo company.

1. In the **Navigation pane**, go to **Modules > Retail and Commerce > Channels > Stores > All stores**.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Click **Edit**.
5. The settings in the **Statement/closing** FastTab affect the statement creation, validation, and posting for the store. Expand the **Statement/closing** FastTab.  
6. In the **Statement method** field, select the method you want to use to group the statement lines by.  
7. Select "Yes" in **One statement per day** if there should only be one statement created per day when creating statements from the statement creation batch job.  
8. The **Tender declaration calculation** field defines whether tender declarations should be added together or if the last one should be used.  
9. In the **Rounding** field, select the ledger account to post rounding differences into.  
10. In the **Maximum rounding difference** field, enter the maximum rounding difference allowed.
11. In the **Posting** field, enter the maximum total posting difference allowed for a statement.
12. In the **Shift** field, enter the maximum total difference within a shift in a statement.  
13. In the **Transaction** field, enter the maximum total difference in a statement line.  
14. In the **Closing method** field, define whether transactions that will be included in a statement should be part of a closed shift or if they can be any transactions within the defined date/time range.  
15. In the **End of business day** field, enter a time if transactions that happen after midnight should be posted with the previous day.  
16. Select "Yes" in **Post as business day** if transactions that happen after midnight should be posted as part of the previous day.  
17. Select "Yes" in **Split by Statement method** to get statements created for each statement method defined. This action can be useful if the performance of the posting needs to be improved for stores with high transaction volumes since it will create many smaller statements that can be processed in parallel.  
18. In the **General** FastTab, in the **Default customer** field, you can select the customer account to use for sales to walk-in customers.  



[!INCLUDE[footer-include](../../includes/footer-banner.md)]