---
title: Enable the Fiscal Establishment dimension
description: Learn how to set up the Fiscal Establishment dimension for the SPED-Reinf, including a step-by-step process outlining how to enable fiscal establishment.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/04/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-11-30
---

# Enable the Fiscal Establishment dimension

[!include [banner](../../includes/banner.md)]

SPED-Reinf events R-4010, R-4020, and R-4040 require that you determine a fiscal establishment for non-fiscal operations that you post through a journal. Therefore, you must enable fiscal establishment as a dimension and select it on the lines of a journal.

Follow these steps to enable fiscal establishment as a dimension.

1. Go to **General ledger** > **Chart of accounts** > **Dimensions** > **Financial dimensions** to add and configure the new dimension, **Fiscal Establishment**. Set the new dimension as **Active**.

    :::image type="content" source="../media/bra-fiscal-dimenssions.png" alt-text="Screenshot of the new dimension on the Fiscal dimensions page.":::

1. Go to **General ledger** > **Chart of accounts** > **Dimensions** > **Financial dimension sets**.
1. In the list, find and select the **Fiscal Establishment** dimension, and then select the left arrow to add it to the **Available financial dimensions** list.

    :::image type="content" source="../media/bra-fiscal-establishment.png" alt-text="Screenshot of adding the new dimension to the Available financial dimensions list on the Fiscal dimension sets page.":::

1. Go to **General ledger** > **Chart of accounts** > **Structures** > **Configure account structures**, and select the line that you want to configure the account structure for.
1. Select **Edit**, and make any necessary changes to the account structure.

    :::image type="content" source="../media/bra-acc-structure.png" alt-text="Screenshot of the Edit button on the Account structures page.":::

1. While you're editing the account structure, select **Add segment**, and add **Fiscal Establishment**.
1. Select **Activate**, and add the dimension separator.

    :::image type="content" source="../media/bra-add-segment.png" alt-text="Screenshot of adding a segment to the account structure.":::

After you configure the **Fiscal Establishment** dimension, it's available for selection among the financial dimensions for a journal line.

:::image type="content" source="../media/bra-sel-dim.png" alt-text="Screenshot of financial dimensions being selected for a journal line.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
