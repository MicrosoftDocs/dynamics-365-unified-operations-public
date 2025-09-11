---
title: Write off deferrals (Russia)
description: Learn how to write off a deferral and how to reverse the writing off of a deferral for Russia in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 09/12/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2019-06-28
---

# Write off deferrals (Russia)

[!include [banner](../../includes/banner.md)]

This article explains how to write off a deferral and how to reverse the writing off of a deferral for Russia in Microsoft Dynamics 365 Finance.

## Write off deferrals

To write off deferrals, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger** \> **Journal entries** \> **Deferrals journal**.
1. On the Action Pane, select **New**.
1. In the **Name** field, select a journal name.
1. On the Action Pane, select **Lines** to open the **Journal voucher** page.
1. On the Action Pane, select **Group operations** \> **Writing off** to open the **Deferrals writing off** dialog.
1. In the **Transaction date** field, select the transaction date.
1. On the **Records to include** FastTab, select **Filter** to open the **Inquiry** dialog, where you can set up the selection criteria.
1. Select **OK** to return to the **Journal voucher** page. Details for deferrals write-off vouchers that have a status of **In Process** are shown, based on the filter parameters that you set up in the **Inquiry** dialog.

    ![Journal voucher page.](../media/rus-write-off-deferral-01.png)

1. On the Action Pane, select **Functions** \> **Edit line** to edit the deferrals journal before you post it.
1. On the Action Pane, select **Post** \> **Post** to post the deferrals write-off voucher details.

You can create a journal line for a single write-off.

To create a journal line for a single write-off, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger** \> **Journal entries** \> **Deferrals journal**.
1. On the Action Pane, select **New**.
1. In the **Name** field, select a journal name.
1. On the Action Pane, select **Lines** to open the **Journal voucher** page.
1. On the **Overview** tab, select **New** to create a line.
1. In the **Transaction type** field, select **Writing off**.
1. In the **Deferral ID** field, select the deferral to create a receipt transaction for.

    The fields in the **Correction** section of the **Create new line** dialog are used to create a corrective transaction for a closed period.

    ![Create new line dialog.](../media/rus-write-off-deferral-02.png)

1. Select **OK**. Voucher lines are created for the selected deferral on the **Journal voucher** page.
1. On the Action Pane, select **Functions** \> **Edit line** to edit the deferrals journal before you post it.
1. On the Action Pane, select **Post** \> **Post** to post the deferrals write-off voucher details.

## Reverse the writing off of deferrals

To reverse the writing off of deferrals, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger** \> **Journal entries** \> **Deferrals journal**.
1. On the Action Pane, select **New**.
1. In the **Name** field, select a journal name.
1. On the Action Pane, select **Lines** to open the **Journal voucher** page.
1. On the Action Pane, select **Group operations** \> **Writing off reversal** to open the **Writing off reversal** dialog.
1. In the **Reversal date** field, select the transaction date.
1. On the **Records to include** FastTab, select **Filter** to open the **Inquiry** dialog, where you can set up the selection criteria.
1. Select **OK** to return to the **Journal voucher** page.
1. On the Action Pane, select **Post** \> **Post** to post the reversal voucher. The deferrals and ledger transactions that are specified in the posting profile are generated.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
