---
title: Issue customer fiscal documents (for SUFRAMA customers) (Brazil)
description: This article describes how to set up tax exemptions for the Superintendência da Zona Franca de Manaus (SUFRAMA) region in Brazil with Microsoft Dynamics 365 Finance.
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

# Issue customer fiscal documents (for SUFRAMA customers) (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to set up tax exemptions for the Superintendência da Zona Franca de Manaus (SUFRAMA) region in Brazil with Microsoft Dynamics 365 Finance.

Use the following procedure to set up tax exemptions for the SUFRAMA region. The procedure uses the BRMF demo company.

To set up tax exemptions for the SUFRAMA region, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Customers \> All customers**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Expand the **Fiscal information** section.
1. Select **Edit**.
1. In the **SUFRAMA** field, select **Yes**.
1. In the **SUFRAMA number** field, enter a value.
1. In the **Discount PIS and COFINS** field, select **Yes**.
1. Select **Save**.
1. Close the page.
1. Go to **Tax \> Indirect taxes \> Sales tax \> Item sales tax groups**.
1. In the list, find and select the desired record.
1. Select **Edit**.
1. In the list, find and select the desired record.
1. Select the **Exempt** checkbox.
1. In the **Taxation code** field, enter or select a value. To specify the taxes that don't have a tax credit, select **Without Credit/Debit (other)**.  
1. Select **Save**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
