---
title: Cancel a purchase complementary fiscal document (Brazil)
description: You can cancel an incorrect purchase complementary fiscal document and provide a reason for the cancellation.
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
# Cancel a purchase complementary fiscal document (Brazil)

[!include [banner](../../includes/banner.md)]

You can cancel an incorrect purchase complementary fiscal document and provide a reason for the cancellation. When you cancel a purchase complementary fiscal document, a purchase complementary fiscal document is created that has a negative price amount, an Imposto Sobre Circulação de Mercadorias e Serviços (ICMS) amount, or an Imposto Sobre Produtos Industrializados (IPI) amount. When you post the negative purchase complementary fiscal document, the original complementary fiscal document is marked as canceled, and all the ledger transactions and financial transactions are reversed. The original purchase complementary fiscal document is reported in the fiscal books as canceled. The negative purchase complementary fiscal document isn't reported in the fiscal books. This task uses the BRMF demo company.



1. Go to Accounts payable > Fiscal documents > All purchase complementary fiscal documents.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Click Cancel fiscal document to open the drop dialog.
5. In the Reason code field, enter or select a value.
6. Click Create corrected invoice.
    * A negative purchase complementary fiscal document is created.  
7. Click Post.
8. Close the page.
9. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
