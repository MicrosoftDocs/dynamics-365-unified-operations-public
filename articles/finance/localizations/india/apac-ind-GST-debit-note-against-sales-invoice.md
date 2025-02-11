---
title: Create a debit note against a sales invoice
description: Learn how to create a debit note against a sales invoice, including step-by-step processes for validating tax details and validating financial entries.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/04/2019
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Create a debit note against a sales invoice

[!include [banner](../../includes/banner.md)]

1. Go to **General ledger** \> **Journals** \> **General journal**.
2. Create a journal.
3. Enter a name, and then select **Lines**.
4. In the **Account type** field, select **Customer**. Then, in the **Account** field, select a value.
5. In the **Debit** field, enter a value.
6. In the **Offset account type** field, select **Ledger**. Then, in the **Offset account** field, select a value.
7. Select **Tax information**.
8. On the **GST** tab, in the **HSN code** field, select a value.
9. Select **Ok**.

## Validate the tax details

1. Select **Tax document**.
2. Select **Header**, and then expand **Tax document** fastTab.
3. In the **Transaction type** field, select **Revised**.
4. In the **Original transaction id** field, select a value.
5. In the **Original transaction date** field, select a value.
6. In the **Tax details** fastTab verify tax amount. 
7. Select **Close**.
8. Select **Post** \> **Post**.
9. Close the message that you receive.

## Validate the financial entries

To validate the financial entries, select **Inquiries** \> **Voucher**.

![Example.](../media/Annotation-2019-05-20-161336.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
