---
title: Enable the Fiscal establishment dimension
description: This article explains how to set up the Fiscal establishment dimension for the SPED-Reinf.
author: AdamTrukawka
ms.date: 08/07/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Brazil
ms.author: atrukawk
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: 8.1
ms.search.form: 
---

# Enable the Fiscal establishment dimension

[!include [banner](../includes/banner.md)]
  
SPED Reinf events: R-4010, R-4020 and R-4040 require a fiscal establishment be determined for non fiscal operations posted through a journal. Therefore, it's necessary to enable a **Fiscal establishment** dimension, and select it in the lines of a journal. Follow these steps to enable fiscal establishment as a dimension:

1.  Go to **General Ledger** \> **Chart of accounts** \> **Dimensions** \> **Financial dimensions** to add and configure the new dimension, **Fiscal Establishment**. Set the new dimension as **Active**.
    ![Fiscal Dimensions.](media/bra-fiscal-dimenssions.png)

2.  Go to **General Ledger** \> **Chart of accounts** \> **Dimensions** \> **Financial dimension**.
3.  In the list, find and select the **Fiscal Establishment** dimension and use the left arrow to add it to the **Available Financial Dimensions** list.
    ![Fiscal Establishment.](media/bra-fiscal-establishment.png)

4.  Go to **General Ledger** \> **Chart of accounts** \> **Structures** \> **Configure account structures** and select the line for which you want to configure the account structure.
5.  Select **Edit** and make any necessary changes to the account structure.  
    ![Edit button for account structure changes.](media/bra-acc-structure.png)

6.  While editing an account structure, select **Add segment** and then add **Fiscal Establishment**.
7.  Select **Activate** and add the dimensions separator.  
    ![Adding a segment to the account structure.](media/bra-add-segment.png)

After the **Fiscal Establishment** is configured as a dimension, it's available for selection in the **Financial dimensions** of a journal line.
    ![Preparation items parameters.](media/bra-sel-dim.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
