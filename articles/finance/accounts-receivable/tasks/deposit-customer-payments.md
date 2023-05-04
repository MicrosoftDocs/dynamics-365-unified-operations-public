--- 
# required metadata 
 
title: Deposit customer payments
description: Deposit customer payments. 
author: ShivamPandey-msft
ms.date: 07/18/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerJournalTable, LedgerJournalTransCustPaym, CustTableLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Deposit customer payments

[!include [banner](../../includes/banner.md)]

Deposit customer payments. This task uses the USMF demo company.

1. Go to **Navigation pane > Modules > Accounts receivable > Payments > Payment journal**.
2. Select **New**.
3. In the **Name** field, select **CustPay** in the drop-down menu.
4. Select **Lines**.
5. In the **Account** field, select the customer for whom you are recording the payment.
6. In the **Credit** field, enter the amount of the payment. You can choose to leave the amount blank, and have the system calculate it by selecting the invoices which were paid.  
7. In the **Payment reference** field, type a value. The payment reference could be the check number for the payment you are entering. The payment reference is required in order to include the payment on a deposit slip.  
8. Mark the box Use a deposit slip. If the payment should be included in the deposit, change this setting to Yes.  
9. Select **New**.
10. In the **Account** field, select the customer for the next payment.
11. In the **Credit** field, enter the payment amount.
12. In the **Payment reference** field, type a value.
13. Mark the box **Use a deposit slip**.
14. Select **Post**. Payments must be posted before the deposit slip can be generated. This is to ensure that the payments don't change after the deposit slip is generated.  
15. Select **Functions**.
16. Select **Deposit slip**.
17. Select **OK**. The first page is used to create the deposit slip.  
18. Select **OK**. The second step is to print the deposit slip, but this step is not required.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
