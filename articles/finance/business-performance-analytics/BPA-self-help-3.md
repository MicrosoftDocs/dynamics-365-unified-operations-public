---

title: Business performance analytics self help - Missing main account in budget
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

# Business performance analytics self help error -  Missing main account in budget

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Missing main account in budget: Error code: ERR00003 [Type: Warning] 
Error code ERR00003 occurs in the BPA_SelfHelp_Log table when Budget transaction lines in Dynamics 365 Finance are missing the main account in the ledger dimension column. Consequently, transactions in the budget will be linked to a generalledgeraccountkey of -1. 

### Resolution 
If your transaction doesn't require the use of the main account, this issue might not need immediate action. However, certain Microsoft reports could display fields with no data or incomplete records. In such cases, you might need to create modified versions of these reports to address the gaps and ensure accurate reporting.  

The following is an example of the error:  
1 records in BudgetTransactionLine have missing MAINACCOUNT - [Row(BudgetTransactionLine_RECID=Decimal('5637145719'))]

>[!NOTE]
>There are no specific steps required to address this scenario and doesn't require correction. 

 
