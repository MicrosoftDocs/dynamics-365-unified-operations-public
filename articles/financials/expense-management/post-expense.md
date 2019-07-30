---
# required metadata

title: Post an expense report
description: This topic explains how to post an expense report to the general ledger.
author: saraschi2
manager: AnnBe
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  TrvPerDiems
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Post an expense report

[!include [banner](../includes/banner.md)]

After an expense report has been approved and transferred to the general journal, it can be posted to the general ledger. When you post an expense report, expenses that are eligible for recovery of value-added tax (VAT) are identified. The task of verifying and recovering VAT payments is assigned to the employee who is responsible for verifying the expense report.

If expenses on an expense report are charged to a company other than the company that employs the employee, you must verify the company that those expenses are owed to and the company that the expenses are owed from. For example, the employee who submitted an expense report works for the DAT company but charged an expense to the DIR company. In this case, DAT is the company that the expense is owed to, and DIR is the company that the expense is owed from. After you verify these journal lines, you can post the expense lines to the general ledger.

To post an expense report, on the **Approved expense reports** page, select the expense report, and then, on the Action Pane, select **Post**.

You can also post all the expense reports in the list at the same time. Select all the expense reports, and then select **Post**.
