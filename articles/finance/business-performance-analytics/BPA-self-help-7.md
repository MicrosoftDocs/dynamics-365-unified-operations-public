---

title: Business performance analytics self help - Missing budget transaction header
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

# Business performance analytics self help error - Missing budget transaction header

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Missing budget transaction header: Error dode: ERR00007 [ Type: Warning] 
Error Code ERR00007 is logged in the BPA_SelfHelp_Log table when there are budget transaction line entries without corresponding budget transaction headers. These records are excluded and won't be transferred to Fact tables. Some Microsoft reports might display fields with no data or incomplete records, prompting you to consider duplicating and modifying these reports. 
 

No immediate action is needed and this issue might arise due to data synchronization delays. It's recommended to wait for the next copule of business performance analytics runs. 
If the problem continues, follow these steps: 
1. Verify entries in the Budget transaction header table.
2. Confirm the entries exist in the budget transaction header table in Dynamics 365 Finance.

If the entries exist, contact support for further assistance. 
