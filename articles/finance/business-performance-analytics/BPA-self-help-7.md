---

title: Business performance analytics self help - Missing Budget transaction header
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

## Missing Budget transaction header: Error Code: ERR00007 [ Type: Warning] 

Description: Error Code ERR00007 is logged in the BPA_SelfHelp_Log table when there are budget transaction line entries lacking corresponding budget transaction headers. Consequently, these records are excluded and won't be transferred to Fact tables. Certain pre-written Microsoft reports might display fields with no data or incomplete records, prompting you to consider duplicating and modifying these reports. 

 

Resolution Steps: 

No immediate action is needed. This issue might arise due to data synchronization delays. We recommend waiting for the next 2-3 BPA runs to see if the error resolves itself. If the problem persists, follow these steps: 

 

Verify Entries in Budget Transaction Header Table: 

Confirm whether the entries exist in the budget transaction header table in D365 Finance. If they are present in the source, proceed to the next step. 

Contact Microsoft Support: 

If the issue continues and the entries are indeed in the source, consider raising a support ticket with the Microsoft team for further assistance. 
