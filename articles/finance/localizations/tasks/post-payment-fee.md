--- 
# required metadata 
 
title: Generate and post payment fee
description: This task walks you through generating and posting a payment fee for Japan. 
author: ShylaThompson
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerJournalTable, LedgerJournalTransVendPaym, VendTableLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Generate and post payment fee

[!include [banner](../../includes/banner.md)]

This task walks you through generating and posting a payment fee for Japan.



This task was created using the demo data company JPMF.

1. Go to Accounts payable > Payments > Payment journal.
2. Click New.
3. In the Name field, click the drop-down button to open the lookup.
4. In the list, click the link in the selected row.
5. Click Lines.
6. In the Account field, specify the desired values.
    * For example: enter 'JPMF-000001'  
7. In the Debit field, enter a number.
    * For example: enter '200000'  
8. Click Save.
9. Click the Payment fee tab.
    * Verify that the payment fee is generated correctly.  
    * You can also try to change the amount of payment, third party bank account, or the bank account to see that different combinations of these fields will result in a different payment fee amount.  
10. Click Post.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]