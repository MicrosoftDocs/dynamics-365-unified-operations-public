---
# required metadata

title: Resolve discrepancies during invoice totals matching | Microsoft Docs
description: 
author: twheeloc
manager: AnnBe
ms.date: 2016-03-08 22:51:03
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 101
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 63413
ms.assetid: 52a4200e-368f-49e1-8e25-b828c533b6ea
ms.region: Global
# ms.industry: 
ms.author: abruer

---

# Resolve discrepancies during invoice totals matching



One type of invoice matching validation is invoice totals matching. To specify that the system should perform invoice totals matching, on the **Accounts payable parameters** page, on the **Invoice validation** tab, set the **Match invoice totals** option **Yes**. You can use invoice totals matching to help guarantee that total invoice amounts don't deviate from expected amounts by more than an acceptable variance. Six totals are compared on the **Invoice totals matching details** page. If any one of the totals deviates from the expected corresponding purchase order total, a matching discrepancy is flagged. To review the invoice that has the totals matching discrepancies, in the **Vendor invoice entry** workspace, click the **Pending invoices** tile. Then, on the Action Pane, on the **Review** tab, click **Matching details**. If matching discrepancies have been detected, warning icons appear next to the invoice amount. You can view more detail about the totals by viewing the invoice totals matching details. After you identify a discrepancy, you might have to contact the vendor if you think that the information on the invoice is incorrect. Depending on the resulting agreement with the vendor, you can then take one of these actions:

-   Accept the price difference, and post the invoice that has matching discrepancies. Your system might be set up to require approval before it can post if there are matching discrepancies. In this case, you must approve the matching discrepancy and can optionally enter an approval comment. You can then select to post the invoice.
-   Revise the invoice amount to the expected amount, and post the invoice.
-   Request a full credit and a new, corrected invoice from the vendor.


