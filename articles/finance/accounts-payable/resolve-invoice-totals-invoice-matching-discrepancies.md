---
title: Resolve discrepancies during invoice totals matching overview
description: You can use invoice totals matching to help guarantee that total invoice amounts don't deviate from expected amounts by more than an acceptable variance.
author: abruer
ms.date: 07/25/2019
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.collection: get-started
ms.assetid: 9ac42457-95b2-4191-ad06-c7e323704466
ms.search.form: VendTotalPriceTolerance
---

# Resolve discrepancies during invoice totals matching overview

[!include [banner](../includes/banner.md)]

One type of invoice matching validation is invoice totals matching. To specify that the system should perform invoice totals matching, on the **Accounts payable parameters** page, on the **Invoice validation** tab, set the **Match invoice totals** option **Yes**. 

You can use invoice totals matching to help guarantee that total invoice amounts don't deviate from expected amounts by more than an acceptable variance. Six totals are compared on the **Invoice totals matching details** page. If any one of the totals deviates from the expected corresponding purchase order total, a matching discrepancy is flagged. 

To review the invoice that has the totals matching discrepancies, in the **Vendor invoice entry** workspace, click the **Pending invoices** tile. Then, on the Action Pane, on the **Review** tab, click **Matching details**. If matching discrepancies have been detected, warning icons appear next to the invoice amount. You can view more detail about the totals by viewing the invoice totals matching details. 

After you identify a discrepancy, you might have to contact the vendor if you think that the information on the invoice is incorrect. Depending on the resulting agreement with the vendor, you can then take one of these actions:

-   Accept the price difference, and post the invoice that has matching discrepancies. Your system might be set up to require approval before it can post if there are matching discrepancies. In this case, you must approve the matching discrepancy and can optionally enter an approval comment. You can then select to post the invoice.
-   Revise the invoice amount to the expected amount, and post the invoice.
-   Request a full credit and a new, corrected invoice from the vendor.

For more information, see [Research/Resolve exceptions](tasks/research-resolve-exceptions.md).




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
