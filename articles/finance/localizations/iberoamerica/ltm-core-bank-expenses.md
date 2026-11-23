---
title: Post bank expenses for Latin America
description: Learn how to post bank expenses for Latin America, including prerequisites and a process for post bank expenses with LATAM information.
author: Fhernandez0088
ms.author: v-federicohe 
ms.topic: how-to
ms.date: 11/23/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Post bank expenses for Latin America

[!INCLUDE [banner](../../includes/banner.md)]

[!include [does not apply to](includes/does-not-apply-to.md)]

You can post journals for bank expenses directly to the bank account reconciliations for Latin American countries and regions.

## Prerequisites

Before you post a bank expense journal that has LATAM information, make sure you complete the following prerequisites:

- Enable the **LATAM** globalization feature with a valid country or region.
- Go to **Organization administration** > **Setup** > **LATAM** > **Bank Parameters – LATAM**, enable the use of bank expenses, and select a journal name to use.
- Create a document class that's configured as a vendor invoice for the bank expenses.

> [!NOTE]
> Globalization for LATAM doesn't currently cover advanced bank reconciliation functionality. To post bank expenses with LATAM information, follow the LATAM-specific process described in this article.

## Post bank expenses with LATAM information

To post a bank expense that has LATAM information, follow these steps:

1. Go to **Cash and bank management** > **Bank accounts** > **Bank accounts**, and select a bank account.
1. On the Action Pane, select **Account reconciliation**.
1. Select an existing record, or create a new one.
1. Select **Transactions**, and then, on the Action Pane, select **LATAM** > **Bank expenses**.
1. On the **Setup** tab, set the **Amounts include sales tax** option to **Yes**.
1. On the Action Pane, select **Lines**.
1. Complete the new journal with the bank expenses that you need to post by using a ledger account.
1. Select a vendor to represent the bank.
1. On the **Invoice** tab, select the cash payment terms.
1. Complete the required LATAM information for the vendor line.
1. Select the cash payment ledger account as the offset account for the bank line, and then select **Post**.

## View LATAM information from the posted journal

You can view the LATAM information from either the bank transactions or the general journal entries.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
