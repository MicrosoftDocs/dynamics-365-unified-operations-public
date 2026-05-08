---
title: Advance payments that include tax
description: Learn how to create a customer advance payment journal, and then validate the tax information and financial entries, including a process for validating tax details.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Advance payments that include tax

[!include [banner](../../includes/banner.md)]

Complete the following procedures to create a customer advance payment journal, and then validate the tax information and financial entries.

## Create a customer advance payment journal

1. Go to **Accounts receivable > Payments > Payment journal**.
1. Create a record.
1. In the **Name** field, select a value.
1. On the **Setup** tab, select the **Amounts include sales tax** check box.
1. Select **Lines**.
1. Create a customer advance payment journal.
1. Save the record.
1. Select **Tax information**.
1. On the **GST** tab, in the **HSN code** field, select a value.
1. Select the **Customer tax information** tab, and then select **OK**.

## Validate the tax details

1. Select **Tax document**.

    **Example**

    **IGST:** 20 percent

1. Select **Close**.
1. Select **Post \> Post**.
1. Close the message that you receive.

## Validate the financial entries

To validate the financial entries, in the journal, select **Inquiries \> Voucher**. Here's an example.

:::image type="content" source="../media/Annotation-2019-05-21-131638.png" alt-text="Screenshot of financial entries example.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
