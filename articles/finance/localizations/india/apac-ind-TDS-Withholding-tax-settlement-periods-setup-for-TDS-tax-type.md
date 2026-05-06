---
title: Set up withholding tax settlement periods for the TDS tax type
description: Learn how to set up settlement periods for Tax Deducted at Source (TDS) settlement periods, including a step-by-step process.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/01/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
---

# Set up withholding tax settlement periods for the TDS tax type

[!include [banner](../../includes/banner.md)]

This article explains how to set up settlement periods for Tax Deducted at Source (TDS) settlement periods.

1. Go to **Tax \> Indirect taxes \> Withholding tax \> Withholding tax settlement periods**.

    :::image type="content" source="../media/apac-ind-TDS-13.png" alt-text="Screenshot of the Withholding tax settlement periods page.":::

1. In the **Tax type** field, select **TDS** to set up withholding tax settlement periods for the TDS tax type.
1. Select **New** to create a line.
1. In the **Settlement period** field, enter a name for the TDS settlement period.
1. In the **Description** field, enter a description.
1. In the **Withholding tax authority** field, select the TDS authority that you're defining the TDS settlement period for.
1. On the **General** FastTab, in the **Period interval** field, select the type of period interval for the TDS settlement period.
1. In the **Number of units** field, specify the number of units for the period interval type.
1. On the **Periods** FastTab, in the **From date** field, select the start date for the TDS settlement period. In the **To date** field, select the end date.
1. To create a subsequent TDS settlement period for an existing period, based on the period interval and period units, select **New period**.
1. To view the details of the periodic TDS settlement that is run for a specific settlement period, select **Withholding tax payments** to open the **Withholding tax payment** page.

    > [!NOTE]
    > To run the periodic TDS settlement process, go to **General ledger \> Periodic \> Withholding tax \> Withholding tax payment**.

    :::image type="content" source="../media/apac-ind-TDS-15.png" alt-text="Screenshot of the Withholding tax payment page.":::

1. Close the page.
