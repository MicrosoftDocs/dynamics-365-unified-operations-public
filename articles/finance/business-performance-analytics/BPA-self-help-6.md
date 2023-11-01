---

title: Business performance analytics self-help error - Missing budget data
description: This article provides information about the Missing budget data error (error code ERR00006) in business performance analytics.
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

# Business performance analytics self-help error - Missing budget data

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Missing budget data: Error code: ERR00006 [Type: Warning]

Error code *ERR00006* is logged in the `Transform Log` table in Microsoft Dataverse when no budget is created in Dynamics 365 Finance, and no budget data is available for reports.

Here's an example of a record:

> BudgetFact is empty due to one or more missing inputs \['mserp_budgettransactionlinebientity', 'mserp_budgettransactionheaderbientity'\]

This warning is for information only. No action is required.

The warning indicates that there's no budget in Dynamics 365 Finance, and no budget data is available for reports. This issue doesn't require immediate attention. Instead, consider this information as part of your overall financial data assessment.
