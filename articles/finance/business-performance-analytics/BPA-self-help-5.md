---

title: Business performance analytics self help - Mismatch between Debits and Credits
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

## Mismatch between Debits and Credits: Error Code: ERR00005 [ Type: Warning] 
Description: Error Code ERR00005 is logged in the BPA_SelfHelp_Log table under the following circumstances: 

When the total of values in the accountingcurrencyamount column of the generaljournalaccountentry table is not zero for a specific combination of ledger.id and gje.journalnumber. 

When the total of values in the reportingcurrencyamount column of the generaljournalaccountentry table is not zero for the same combination of ledger.id and gje.journalnumber. 

 

Resolution Steps: 

Please note that this information is provided for your awareness only. No action is required on your part regarding this matter. This warning highlights instances where the total values in certain columns don't balance to zero within specific ledger and journal number combinations. However, this might not necessarily indicate an error that needs immediate attention. Simply be aware of this information and consider it as part of your overall financial data assessment. 
