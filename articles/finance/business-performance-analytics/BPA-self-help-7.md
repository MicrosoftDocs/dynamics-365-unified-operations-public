---

title: Business performance analytics self-help error - Missing budget transaction header
description: This article provides information about the Missing budget transaction header error (error code ERR00007) in business performance analytics.
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

# Business performance analytics self-help error - Missing budget transaction header

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Missing budget transaction header: Error code: ERR00007 [Type: Warning]

Error code *ERR00007* is logged in the `Transform Log` table in Microsoft Dataverse when there are budget transaction line entries that don't have corresponding budget transaction headers. These records are excluded and won't be transferred to fact tables. Some Microsoft reports might show either fields that have no data or incomplete records. In these cases, you might have to create modified versions of the reports to address the gaps and ensure accurate reporting.
 
No immediate action is required, because this issue might be caused by data synchronization delays. We recommend that you observe the next few business performance analytics runs to see whether the issue is fixed.

If the issue persists, follow these steps.

1. Verify entries in the Budget transaction header table.
2. Confirm that the entries exist in the Budget transaction header table in Dynamics 365 Finance.

If the entries exist, contact Support for further assistance.
