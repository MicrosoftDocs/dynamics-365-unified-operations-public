---
title: Separate accounts for credit notes
description: Learn how to set up and use separate accounts for credit notes, including prerequisites and an outline on setting up posting accounts.
author: mrolecki
ms.author: johnmichalak
ms.topic: article
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2019-11-01
ms.search.form: 
ms.dyn365.ops.version: 10.0.7
---

# Separate accounts for credit notes

[!include [banner](../../includes/banner.md)]

In Italy, a company can define the accounting policy so that credit note amounts post to ledger accounts that differ from the revenue accounts. Use this approach to track the amount that you issue on credit notes.

## Prerequisites

- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, turn on the **Separate accounts for credit notes** feature. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up posting accounts

Define specific ledger accounts for sales orders. To complete the setup, on the **Posting** page, select the **Credit note** option, and then specify the ledger accounts.

Use the **Posting** page to set up different accounts for various combinations of customers, items, and related groups.

:::image type="content" source="../media/emea-ita-exil-separate-account-credit-pic1.jpg" alt-text="Screenshot of the Posting accounts setup page.":::

## Post credit notes

### Post a new credit note

When you post a new credit note, the system uses the ledger account instead of the standard revenue account that you defined on the sales order.

If you don't define a separate ledger account for the credit note, or if the required combination of a customer and an item isn't found, the system uses a standard sales order revenue account for posting.

### Post a credit note that you created from a sales order

If you create a credit note that's based on an existing sales order, clear the **Main account** field for each credit note line. A revenue account from the sales order might be automatically entered in the field.

:::image type="content" source="../media/emea-ita-exil-separate-account-credit-pic2.jpg" alt-text="Screenshot of clearing the main account field.":::

> [!NOTE]
> Separate accounts apply only to credit notes that are based on sales orders. They not apply to free-text credit notes, because free-text credit notes require that you explicitly enter a ledger account.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
