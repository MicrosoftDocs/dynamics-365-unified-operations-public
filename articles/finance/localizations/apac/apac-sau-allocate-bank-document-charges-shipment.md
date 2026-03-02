---
title: Allocate bank document charges to a shipment
description: This article explains how you can allocate document bank charges to a shipment on a purchase order.
author: AdamTrukawka
ms.author: atrukawk
ms.date: 03/02/2026
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Saudi Arabia
ms.search.validFrom: 2019-11-29
ms.dyn365.ops.version: 10.0.8

---
 
# Allocate bank document charges to a shipment

[!include [banner](../../includes/banner.md)]

You can allocate bank document charges that you post in the general journal to purchase order lines. The purchase order should have a related letter of credit or import collection.

## Prerequisites

Before you start to allocate the bank document charges, [set up bank facilities and posting profiles for letters of credit](../../cash-bank-management/tasks/set-up-bank-facilities-posting-profiles-letter-credit.md), and create a purchase order that has an [imported letter of credit](../../cash-bank-management/tasks/import-letter-credit.md).

## Set up a charge code for bank document charges

Follow these steps to set up a charge code for bank document charges.

1. Go to **Accounts payable** \> **Setup** \> **Charges setup** \> **Charges code**.
1. On the **Posting** FastTab, in the **Debit** section, in the **Type** field, select **Item**. The **Bank document charge code** option in the **Bank document charge** section becomes available.
1. Set the **Bank document charge code** option to **Yes**. The **Type** field in the **Credit** section is automatically set and can't be edited.

:::image type="content" source="../media/apac-sau-bank-document-charge-setup.PNG" alt-text="Screenshot of setting up a charge code for bank document charges.":::

## Allocate bank document charges

Follow these steps to allocate bank document charges.

1. Create a purchase order that has a letter of credit or an import collection. For more information, see [Import letter of credit](../../cash-bank-management/tasks/import-letter-credit.md).

    > [!NOTE]
    > You must confirm the letter of credit or import collection before you can allocate bank document charges.

1. Go to **General ledger** \> **Journal entries** \> **General journals**.
1. On the Action Pane, select **Lines**.
1. On the **Payment** tab, in the **Letter of credit/import collection** section, set the fields as you require.

    > [!NOTE]
    > The system automatically sets the **Offset account type** and **Offset account** fields.

    :::image type="content" source="../media/apac-sau-general-journal-voucher.PNG" alt-text="Screenshot of entering the bank document charge code on a journal line."
:::

1. On the **List** tab, set the **Account** and **Debit** fields.
1. On the **Letter of credit/import collection** page, on the Action Pane, select **Bank document** \> **Bank document charge**.

    :::image type="content" source="../media/apac-sau-allocate-bank-docment-charge.PNG" alt-text="Screenshot of allocating bank document charges."
:::

    The letter of credit or import collection that you created in the purchase order opens. It shows the bank document charge that you posted in the general journal for this letter of credit or import collection.

    :::image type="content" source="../media/apac-sau-lc-bank-document-transactions.PNG" alt-text="Screenshot of letter of credit and import collection bank document transactions."
:::

1. Select the bank document charge transaction in **Edit** mode, and then select **Letter of credit/import collection** to allocate the selected bank document charge.

    > [!TIP]
    > You can validate the allocation by selecting **Shipment charge transactions** on the **Lines** FastTab.

1. To allocate shipment charge transactions to the purchase order lines, on the Action Pane, on the **Purchase** tab, in the **Charges** group, select **Maintain charges**, and then select **Allocate**. The bank document charge that you allocated to letter of credit or import collection lines appears in the list.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
