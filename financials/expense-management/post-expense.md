---
# required metadata

title: Post an expense report to the General ledger
description: After an expense report has been approved and transferred to the general journal, the report can be 
posted to the general ledger.
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer:  twheeloc
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi2
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: AX 7.0.0
---

# Post an expense report to the General ledger

[!include[banner](../includes/banner.md)]

After an expense report has been approved and transferred to the general journal, the report can be posted to the general ledger. 
When you post an expense report, expenses that are eligible for Value Added Tax (VAT) recovery are identified. The task of verifying and 
recovering VAT payments is assigned to the employee who is responsible for verifying the expense report. 

If an expense report contains expenses that are charged to a company other than the company that employs the employee, you must verify 
which company the expense is owed to and which company the expense is owed from. For example, if the employee who submitted the expense
report works for company DAT but charged an expense to company DIR, DAT is the owed-to company and DIR is the owed-from company. 
After you verify these journal lines, you can post the expense lines to the general ledger. 

To post an expense report, go to the **Approved expense reports** page, select the expense report that you want to post, and click 
**Post** > **Selected**.

You can approve all of the expense reports in the list by clicking **Post** > **All**. 
