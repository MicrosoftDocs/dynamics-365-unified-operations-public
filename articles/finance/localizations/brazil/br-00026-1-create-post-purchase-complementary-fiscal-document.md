---
title: Create and post a purchase complementary fiscal document (Brazil)
description: This article describes how to create a purchase complementary fiscal document to adjust a purchase fiscal document that was generated for an incorrect price for Brazil in Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2024
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Create and post a purchase complementary fiscal document (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to create a purchase complementary fiscal document to adjust a purchase fiscal document that was generated for an incorrect price for Brazil in Microsoft Dynamics 365 Finance.

Use the following procedure to create a purchase complementary fiscal document to adjust a purchase fiscal document that was generated for an incorrect price, Imposto Sobre Produtos Industrializados (IPI) amount, or Imposto Sobre Circulação de Mercadorias e Serviços (ICMS) amount. The procedure uses the BRMF demo company.

To create a purchase complementary fiscal document to adjust a purchase fiscal document that was generated for an incorrect price, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Fiscal documents \> All fiscal documents**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Complementary fiscal document**.
1. Select **Price**.
1. Expand the **Complementary invoice header** section.
1. In the **Document model** field, enter or select a value.
1. In the **Access key** field, enter the access key for the electronic fiscal document (NF-e).     
1. In the list, mark the selected row.
1. In the **Corrected line amount** field, enter the corrected line amount in the transaction currency. The difference between the amount in the **Corrected line amount** field and the amount in the **Original line amount** field is updated in the **Net amount** field.  
1. Select **Save**.
1. Select **Post**.
1. Close the page.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
