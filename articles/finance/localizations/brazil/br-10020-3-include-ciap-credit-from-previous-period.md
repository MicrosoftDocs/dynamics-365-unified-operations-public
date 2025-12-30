---
title: Include CIAP credit from a previous period (Brazil)
description: This article describes how to use the CIAP fixed asset transactions page to create CIAP credit installments in Brazil with Microsoft Dynamics 365 Finance.
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

# Include CIAP credit from a previous period (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to use the Imposto Sobre Circulação de Mercadorias e Prestação de Serviços (ICMS) Credit Control of Fixed Assets (CIAP) fixed asset transactions page to create CIAP credit installments in Brazil with Microsoft Dynamics 365 Finance.

You can use the CIAP fixed asset transactions page to create CIAP credit installments. If a CIAP installment wasn't included in a previous booking period, an installment must be created so that the installment is processed as an ICMS tax assessment in the current booking period. 

The following procedure uses the BRMF demo company.

To use the CIAP fixed asset transactions page to create CIAP credit installments, follow these steps:

1. In Dynamics 365 Finance, go to **Fiscal books \> Common \> Booking period**.
1. Select **Create new booking period** to open the drop dialog.
1. In the **Fiscal establishment** field, enter or select a value.
1. In the **Month** field, select a month.
1. In the **Year** field, enter a year.
1. Select **OK**.
1. In the list, mark the selected row.
1. Select **ICMS**.
1. Select **ICMS tax assessment** to open the drop dialog.
1. Select **OK**.
1. Select **CIAP assessment**.
1. Select **Add line**.
1. In the list, mark the selected row.
1. In the **CIAP asset ID** field, enter or select a value.
1. In the **Date** field, enter a date.
1. In the **Transaction type** field, select **Credit of ICMS installment**.  
1. In the **Installment number** field, enter a number.
1. In the **Installment amount** field, enter a number.
1. Select **Save**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
