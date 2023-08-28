---
title: Enable the Fiscal Establishment dimension
description: This article explains how to set up the Fiscal Establishment dimension for the SPED-Reinf.
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

# Enable the Fiscal Establishment dimension

[!include [banner](../includes/banner.md)]

SPED-Reinf events R-4010, R-4020, and R-4040 require that a fiscal establishment is determined for non-fiscal operations that are posted through a journal. Therefore, you must enable fiscal establishment as a dimension and select it on the lines of a journal.

Follow these steps to enable fiscal establishment as a dimension.

1. Go to **General ledger** \> **Chart of accounts** \> **Dimensions** \> **Financial dimensions** to add and configure the new dimension, **Fiscal Establishment**. Set the new dimension as **Active**.

    ![New dimension on the Fiscal dimensions page.](media/bra-fiscal-dimenssions.png)

2. Go to **General ledger** \> **Chart of accounts** \> **Dimensions** \> **Financial dimension sets**.
3. In the list, find and select the **Fiscal Establishment** dimension, and then select the left arrow to add it to the **Available financial dimensions** list.

    ![Adding the new dimension to the Available financial dimensions list on the Fiscal dimension sets page.](media/bra-fiscal-establishment.png)

4. Go to **General ledger** \> **Chart of accounts** \> **Structures** \> **Configure account structures**, and select the line that you want to configure the account structure for.
5. Select **Edit**, and make any necessary changes to the account structure.

    ![Edit button on the Account structures page.](media/bra-acc-structure.png)

6. While you're editing the account structure, select **Add segment**, and add **Fiscal Establishment**.
7. Select **Activate**, and add the dimension separator.

    ![Adding a segment to the account structure.](media/bra-add-segment.png)

After the **Fiscal Establishment** dimension is configured, it's available for selection among the financial dimensions for a journal line.

![Financial dimensions being selected for a journal line.](media/bra-sel-dim.png)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
