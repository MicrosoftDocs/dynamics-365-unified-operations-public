---
title: Set up adjustment codes for ICMS tax (Brazil)
description: This article describes how to set up adjustment codes for the ICMS tax in Brazil with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/20/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Set up adjustment codes for ICMS tax (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to set up adjustment codes for the Circulação de Mercadorias e Serviços (ICMS) tax in Brazil with Microsoft Dynamics 365 Finance.

In the Sistema Publico de Escrituração Digital (SPED) fiscal text file, record C197 includes information about any adjustments of ICMS information on fiscal documents. These adjustments can occur because of deferral, suspension, differential of tax rates, anticipation, and other situations of exception in the ICMS tax. The adjustments require an adjustment code. 

Use the following procedure to set up adjustment codes. The procedure uses the BRMF demo company.

To set up adjustment codes for the ICMS tax, follow these steps.

1. In Dynamics 365 Finance, go to **Fiscal books \> Setup \> Tax adjustment codes \> ICMS, ICMS-ST, and ICMS-DIF adjustment codes**.
1. Select **New**.
1. In the **Identification** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **State** field, enter or select a value.
1. In the **Occurrence code** field, enter a value.
1. In the **Valid From Date** field, enter a date.
1. Expand the **Payment** section.
1. Expand the **Posting** section.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Company accounts** field, enter or select a value.
1. In the **Sales tax code** field, enter or select a value.
1. In the **Main account** field, enter a value.
1. Select **Save**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
