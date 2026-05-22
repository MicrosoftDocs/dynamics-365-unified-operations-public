--- 
title: Store configurations for Retail statements
description: Learn about store configurations for Retail statements in Microsoft Dynamics 365 Commerce. 
author: jashanno
ms.date: 08/08/2019
ms.topic: how-to 
ms.search.form: RetailStoreTable   
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2016-06-30 
ms.custom: 
  - bap-template 
---
# Store configurations for Retail statements

[!include [banner](../includes/banner.md)]

This article explains store configurations for Retail statements in Microsoft Dynamics 365 Commerce.

The following procedure walks through store configurations that affect how Commerce statements are created and posted. This procedure uses the USRT demo company.

To set up a store configuration for a Retail statement, follow these steps.

1. In Commerce headquarters, go to **Modules > Retail and Commerce > Channels > Stores > All stores**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Edit**.
1. The settings in the **Statement/closing** FastTab affect the statement creation, validation, and posting for the store. Expand the **Statement/closing** FastTab.  
1. In the **Statement method** field, select the method you want to use to group the statement lines by.  
1. Select **Yes** in **One statement per day** if there should only be one statement created per day when creating statements from the statement creation batch job.  
1. The **Tender declaration calculation** field defines whether tender declarations should be added together or if the last one should be used.  
1. In the **Rounding** field, select the ledger account to post rounding differences into.  
1. In the **Maximum rounding difference** field, enter the maximum rounding difference allowed.
1. In the **Posting** field, enter the maximum total posting difference allowed for a statement.
1. In the **Shift** field, enter the maximum total difference within a shift in a statement.  
1. In the **Transaction** field, enter the maximum total difference in a statement line.  
1. In the **Closing method** field, define whether transactions that are included in a statement should be part of a closed shift or if they can be any transactions within the defined date and time range.  
1. In the **End of business day** field, enter a time if transactions that happen after midnight should be posted with the previous day.  
1. Select **Yes** in **Post as business day** if transactions that happen after midnight should be posted as part of the previous day.  
1. Select **Yes** in **Split by Statement method** to get statements created for each statement method defined. This action can be useful if the performance of the posting needs to be improved for stores with high transaction volumes since it creates many smaller statements that can be processed in parallel.  
1. In the **General** FastTab, in the **Default customer** field, select the customer account to use for sales to walk-in customers.  

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
