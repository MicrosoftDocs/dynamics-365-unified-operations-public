--- 
# required metadata 
 
title: Register and post a postdated check for a vendor
description: You can register the details of a postdated check before you issue the check to a vendor by using the journal voucher. 
author: kweekley
ms.date: 11/15/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerJournalTable, LedgerJournalTransVendPaym   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Register and post a postdated check for a vendor

[!include [banner](../../includes/banner.md)]

You can register the details of a postdated check before you issue the check to a vendor by using the journal voucher. You can also post the postdated check and generate financial transactions. Before you register and post a postdated check from a vendor, complete the following task: 

Set up postdated checks in the **Cash and bank management** page. 

The role of this task guides is Treasurer. This task uses the USMF demo company.

1. Go to **Acounts payable > Payments > Payment journal**.
2. Click **New**.
3. In the **Name** field, type 'VendPay'.
4. Click **Lines**.
5. In the **Account** field, specify the desired values.
6. In the list, mark the selected row.
7. In the **Debit** field, enter a number.
8. In the **Method of payment** field, click the drop-down button to open the lookup.
    * Select the method of payment for the postdated check  
9. In the list, find and select the desired record.
10. In the list, click the link in the selected row.
11. Click the **Postdated checks** tab.
12. In the **Check number** field, type a value.
    * Enter or modify the number of the postdated check.  
13. In the **Issuing bank name** field, type a value.
    * Enter the bank details for the issuing bank.  
14. Click the **List** tab.
15. Click **Post**.
16. Close the page.
17. Click the Postdated checks tab.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
