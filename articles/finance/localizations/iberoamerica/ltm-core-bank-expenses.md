---
title: Post bank expenses for Latin America
description: Learn how to post bank expenses for Latin America, including prerequisites and a process for post bank expenses with LATAM information.
author: Fhernandez0088
ms.author: v-federicohe 
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Post bank expenses for Latin America

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](includes/does-not-apply-to.md)]

You can post journals for bank expenses directly to the banks account reconciliations for Latin American countries/regions.

## Prerequisites

Before you post a bank expense journal that has LATAM information, the following prerequisites must be met:

- Enable the **LATAM** globalization feature with a valid country/region.
- Go to **Organization administration** \> **Setup** \> **LATAM** \> **Bank Parameters – LATAM**, enable the use of bank expenses, and select a journal name to use.
- Create a document class that's configured as a vendor invoice for the bank expenses.

## Post bank expenses with LATAM information

Follow these steps to post a bank expense that has LATAM information.

1. Go to **Cash and bank management** \> **Bank accounts** \> **Bank accounts**, and select a bank account.
1. On the Action Pane, select **Account reconciliation**.
1. Select an existing record, or create a new one.
1. Select **Transactions**, and then, on the Action Pane, select **LATAM** \> **Bank expenses**.
1. On the **Setup** tab, set the **Amounts include sales tax** option to **Yes**.
1. On the Action Pane, select **Lines**.
1. Complete the new journal with the bank expenses that must be posted by using a ledger account.
1. Select a vendor to represent the bank.
1. On the **Invoice** tab, select the cash payment terms.
1. Complete the required LATAM information for the vendor line.
1. Select the cash payment ledger account as the offset account for the bank line, and then select **Post**.

## View LATAM information from the posted journal

You can view the LATAM information from either the bank transactions or the general journals entries.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
