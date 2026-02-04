---
title: Set up PIS and COFINS tables (Brazil)
description: This article describes how to set up PIS and COFINS tables in Brazil with Microsoft Dynamics 365 Finance.
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

# Set up PIS and COFINS tables (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to set up Program of Social Integration (PIS) and Contribution for the Financing of Social Security (COFINS) tables in Brazil with Microsoft Dynamics 365 Finance.

Before the PIS and COFINS tax assessment can be created, you must set up the tables for the credit source and credit type. As a reference, you should use tables 4.3.7 and 4.3.6 that are published by the tax authority. 

The following procedure uses the BRMF demo company.

To set up PIS and COFINS tables, follow these steps:

1. In Dynamics 365 Finance, go to **Fiscal books \> Setup \> PIS and COFINS tables \> CFOP and Credit base source**.
1. Select **New**.
1. In the **CFOP** field, enter a value. Use table 4.3.7 that is published by the tax authority as a reference to enter the values of credit sources by Código Fiscal de Operações e Prestações (CFOP) for the PIS and COFINS tax assessment.  
1. In the **CFOP** description field, enter a value.
1. In the **Credit base source** field, select an option.
1. In the **Valid From Date** field, enter a date.
1. Select **Save**.
1. Close the page.
1. Go to **Fiscal books \> Setup \> PIS and COFINS tables \> Credit types**.
1. Select **New**.
1. In the **Credit type** field, enter a value. Use table 4.3.6 that is published by the tax authority as a reference to enter the values of credit types for the PIS and COFINS tax assessment.  
1. In the **Description** field, enter a value.
1. In the **Valid From Date** field, enter a date.
1. Select **Save**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
