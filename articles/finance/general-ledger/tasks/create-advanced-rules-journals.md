--- 
# required metadata 
 
title: Create advanced rules for journals
description: This procedure steps through creating advanced rules for journals. 
author: aprilolson
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerJournalSetup, LedgerJournalControl, CompanyLookup, LedgerJournalPostControl   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create advanced rules for journals

[!include [banner](../../includes/banner.md)]

This procedure steps through creating advanced rules for journals. This includes setting up journal control and user posting restrictions. This procedure uses the USMF demo data company.


## Set up journal control
1. Go to **General ledger > Journal setup > Journal names**.
2. In the list, find and select the desired record.
3. On the **Action pane**, click **Journal control**.
4. In the **Which account types can be posted** FastTab, click **Add**.
5. In the **Company accounts** field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.
8. In the **Which segment values are valid for this journal** FastTab, click **Add**.
9. In the **Account structure** field, click the drop-down button to open the lookup.
10. In the list, find and select the desired record.
11. In the list, click the link in the selected row.
12. In the **Segment** field, click the drop-down button to open the lookup.
13. In the list, click the link in the selected row.
14. In the **From value** field, click the drop-down button to open the lookup.
15. In the list, find and select the desired record.
16. In the list, click the link in the selected row.
17. In the **To value** field, click the drop-down button to open the lookup.
18. In the list, find and select the desired record.
19. In the list, click the link in the selected row.

## Set up posting restrictions
1. Close the page.
2. Click **Posting restrictions**.
3. In the **How do you want to set up posting restrictions** field, select **By user group**.
4. In the tree, check **The group that you want to allow posting for this journal name**.
5. Click **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
