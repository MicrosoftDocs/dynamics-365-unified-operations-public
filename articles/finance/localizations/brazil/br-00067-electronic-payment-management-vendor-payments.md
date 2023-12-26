---
title: Electronic payment management for vendor payments (Brazil)
description: You can make electronic payments by transferring files between a legal entity and a bank.
author: AdamTrukawka
ms.date: 06/27/2017
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Brazil
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
ms.search.industry: Manufacturing;Distribution;Service industries
---
# Electronic payment management for vendor payments (Brazil)

[!include [banner](../../includes/banner.md)]

You can make electronic payments by transferring files between a legal entity and a bank. You can generate and send an electronic remittance file to a bank. In this case, the export file contains information about invoices that must be received or paid, requests for return invoices, or changes to customer or vendor addresses. Alternatively, you can import a return file from a bank. In this case, the return file contains either information about the acceptance of an invoice together with the payment number that is provided by the bank, or information about the payments that are received from a customer or paid to a vendor. This task uses the BRMF demo company.

1. Go to Purchase ledger > Payments > Payment transfers.
2. In the list, mark the selected row.
3. Click Return file - vendor.
4. In the Method of payment field, enter or select a value.
5. Click OK.
6. Click OK.
    * The status of the payments is updated in the Payments status field on the Payment transfers page. The new status is based on the status of the payment in the return file.  
7. Click Post.
8. In the New journal name field, type a value.
9. Click OK.
10. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
