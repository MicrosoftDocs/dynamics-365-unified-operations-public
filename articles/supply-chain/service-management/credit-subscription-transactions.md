---
title: Credit subscription transactions  
description: Learn how to credit subscription transactions, including a step-by-step process for crediting subscription transactions.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMASubscriptionTable
ms.topic: how-to
ms.date: 01/06/2025
ms.custom: 
  - bap-template
---

# Credit subscription transactions

[!include [banner](../includes/banner.md)]

1. Go to **Service management** \> **Service subscriptions** \> **All service subscriptions**.
1. Select the subscription attached to the subscription transaction for which you want to create a credit note.
1. Select the **Analyze** tab, and then select the **Fee transactions** button on the Action Pane.
1. From the **Fee transactions** page, select the transaction for which you want to create a credit note.
1. Select **Functions** \> **Select for credit note**.
1. From the **Select for credit note** page, select the transaction that you want to credit and then select **OK**.

> [!NOTE]
> When you create the credit note, make sure that you select **Credit notes**. This is found in the **Invoicing method** list in the **Create invoice** dialog box.

If the **Reverse accruals on crediting** field on the **Service management parameters** page is set to *Manual*, you have to reverse each accrued revenue transaction individually before you create a credit note proposal for the transaction.

## Related information

- [Invoice subscription transactions](invoice-subscription-transactions.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
