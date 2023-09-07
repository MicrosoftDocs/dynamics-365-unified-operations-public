---

title: Business performance analytics self help - Mismatch between debits and credits
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

# Business performance analytics self help error - Mismatch between debits and credits

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Mismatch between debits and credits: Error code: ERR00005 [ Type: Warning] 
Error code ERR00005 is logged in the BPA_SelfHelp_Log table when the total of values:
 - In the accountingcurrencyamount column of the generaljournalaccountentry table isn't zero for a specific combination of ledger.id and gje.journalnumber.
 - In the reportingcurrencyamount column of the generaljournalaccountentry table isn't zero for the same combination of ledger.id and gje.journalnumber. 

>[!NOTE]
>This information is provided for your awareness only and no action is required.

This warning highlights instances where the total values in certain columns don't balance to zero within specific ledger and journal number combinations. This might not indicate an error that needs immediate attention. Consider this information as part of your overall financial data assessment. 
