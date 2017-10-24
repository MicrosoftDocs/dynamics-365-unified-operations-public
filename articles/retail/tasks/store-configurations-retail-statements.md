--- 
# required metadata 
 
title: Store configurations for Retail statements
description: This procedure walks through configurations for the Retail store that affect how Retail statements get created and posted. 
author: jashanno
manager: AnnBe 
ms.date: 11/14/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Store configurations for Retail statements

[!include[task guide banner](../includes/task-guide-banner.md)]

This procedure walks through configurations for the Retail store that affect how Retail statements get created and posted. Financial dimensions on Retail stores are covered in another procedure. This procedure uses the USRT demo company.

1. Go to Retail and commerce > Channels > Retail stores > All retail stores.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
    * The settings in the Statement/closing section affect the statement creation, validation, and posting for the store.  Open the Statement/closing section.  
    * Select the method you want to use to to group the statement lines by.  
    * Select "Yes" if there should only be one statement created per day when creating statements from the statement creation batch job.  
    * The Tender declaration calculation field defines whether tender declarations should be added together or if the last one should be used.  
    * Select the ledger account to post rounding differences into.  
    * In the Maximum rounding difference field, you can enter the maximum rounding difference allowed.  
    * In the Posting field, you can enter the maximum total posting difference allowed for a statement.  
    * In the Shift field, you can enter the maximum total difference within a shift in a statement.  
    * In the Transaction field, you can enter the maximum total difference in a statement line.  
    * In the Closing method field, you can define whether transactions that will be included in a statement should be part of a closed shift or if they can be any transactions within the defined date/time range.  
    * In the End of business day field, you can enter a time if transactions that happen after midnight should be posted with the previous day.  
    * Select "Yes" if transactions that happen after midnight should be posted as part of the previous day.  
    * Select "Yes" to get statements created for each statement method defined. This can be useful if the performance of the posting needs to be improved for stores with high transaction volumes since it will create many smaller statements that can be processed in parallel.  
    * In the Default customer field, you can select the customer account to use for sales to walk-in customers.  

