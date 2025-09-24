---
title: Set up adjustment codes for ICMS taxes on fiscal documents (Brazil)
description: This article describes how to create tax adjustment codes to manually adjust ICMS tax amounts on fiscal documents in Brazil with Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/20/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Set up adjustment codes for ICMS taxes on fiscal documents (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to create tax adjustment codes to manually adjust Imposto Sobre Circulação de Mercadorias e Prestação de Serviços (ICMS) tax amounts on fiscal documents in Brazil with Microsoft Dynamics 365 Finance.

You can create tax adjustment codes to manually adjust ICMS tax amounts on fiscal documents. When the Sistema Publico de Escrituração Digital (SPED) fiscal file is generated, record C197 includes the information about manual tax adjustments over the fiscal document's ICMS tax amount. These adjustments on fiscal documents might be required because of deferral, suspension, differences in tax rates, anticipation, and other situations of exception in ICMS tax. 

The following procedure uses the BRMF demo company.

To create tax adjustment codes to manually adjust ICMS tax amounts on fiscal documents, follow these steps.

1. In Dynamics 365 Finance, go to **Fiscal books \> Setup \> Tax adjustment codes \> Adjustment and information for fiscal documents**.
1. Select **New**.
1. In the **Identification** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Tax type** field, select an option.
1. In the **State** field, enter or select a value.
1. In the **Classification** field, select an option.
1. In the **Assessment type** field, select an option.
1. In the **Responsibility** field, select an option.
1. In the **Tax payment type** field, select an option.
1. In the **Occurrence code** field, enter a value.
1. In the **Valid From Date** field, enter a date.
1. Expand the **Posting** section.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Company accounts** field, enter or select a value.
1. In the **Sales tax code** field, enter or select a value.
1. In the **Main account** field, enter a value.
1. Select **Save**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
