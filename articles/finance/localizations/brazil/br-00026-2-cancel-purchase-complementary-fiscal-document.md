---
title: Cancel a purchase complementary fiscal document (Brazil)
description: This article describes how to cancel an incorrect purchase complementary fiscal document and provide a reason for the cancellation in Brazil with Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Cancel a purchase complementary fiscal document (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to cancel an incorrect purchase complementary fiscal document and provide a reason for the cancellation in Brazil with Microsoft Dynamics 365 Finance.

You can cancel an incorrect purchase complementary fiscal document and provide a reason for the cancellation. When you cancel a purchase complementary fiscal document, a purchase complementary fiscal document is created that has a negative price amount, an Imposto Sobre Circulação de Mercadorias e Serviços (ICMS) amount, or an Imposto Sobre Produtos Industrializados (IPI) amount. When you post the negative purchase complementary fiscal document, the original complementary fiscal document is marked as canceled, and all the ledger transactions and financial transactions are reversed. The original purchase complementary fiscal document is reported in the fiscal books as canceled. The negative purchase complementary fiscal document isn't reported in the fiscal books. 

The following procedure uses the BRMF demo company.

To cancel an incorrect purchase complementary fiscal document and provide a reason for the cancellation, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Fiscal documents \> All purchase complementary fiscal documents**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Cancel fiscal document** to open the drop dialog.
1. In the **Reason code** field, enter or select a value.
1. Select **Create corrected invoice**. A negative purchase complementary fiscal document is created.  
1. Select **Post**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
