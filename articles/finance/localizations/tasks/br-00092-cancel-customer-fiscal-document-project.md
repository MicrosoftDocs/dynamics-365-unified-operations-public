---
title: Cancel a customer fiscal document (project) (Brazil)
description: You can cancel a customer invoice for a project.
author: AdamTrukawka
ms.date: 06/26/2017
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Brazil
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Cancel a customer fiscal document (project) (Brazil)

[!include [banner](../../includes/banner.md)]

You can cancel a customer invoice for a project. When you cancel a project invoice, a negative project invoice is created. When you post the negative project invoice, the original and negative project invoices are marked as canceled, and all the ledger and financial transactions are reversed. The original transaction is reported as canceled in the fiscal books, but the negative transaction isn't reported in the fiscal books. You can't cancel a project invoice that is partially or fully settled. Additionally, you can't cancel a project invoice if the posting date of the invoice is in a fiscal period that is closed. This task uses the BRMF demo company.

1. Go to Project management and accounting > Projects > All projects.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Click Invoice journals.
5. Use the Quick Filter to find records. For example, filter on the Invoice field with a value of '04000006'.
6. Click Invoice cancellation.
7. Click Yes.
8. In the Reason code field, enter or select a value.
9. In the Canceling invoice date field, enter a date.
10. Click Cancel project invoice.
11. Select No in the Print invoice field.
12. Click OK.
13. Click OK.
14. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
