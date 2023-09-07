---

title: Business performance analytics self help - Missing Main Account in Budget
description: This article provides information about common errors in business performance analytics.
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 09/09/2023
ms.topic: welcome
ms.prod: 
ms.technology:
ms.custom:
ms.search.form: business-performance-analytics
audience: Application User
---

# Business performance analytics self help error

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate
> in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Missing Main Account in Budget: Error Code: ERR00003 [Type: Warning] 

Description: Error Code ERR00003 is registered in the BPA_SelfHelp_Log table when Budget transaction lines in D365 Finance are missing the main account in the ledger dimension column. Consequently, transactions in the Budget fact will be linked to a generalledgeraccountkey of -1. 

Resolution: If your situation doesn't demand the use of the main account, this issue might not demand immediate action. However, certain pre-written Microsoft reports could display fields with no data or incomplete records. In such cases, you might need to create modified versions of these reports to address the gaps and ensure accurate reporting  

Sample record: 

“1 records in BudgetTransactionLine have missing MAINACCOUNT - [Row(BudgetTransactionLine_RECID=Decimal('5637145719'))]” 

 

Steps to Rectify: Not Applicable 

Note: There are no specific steps required to address this scenario. The issue does not necessitate corrective actions in this context. 

 
