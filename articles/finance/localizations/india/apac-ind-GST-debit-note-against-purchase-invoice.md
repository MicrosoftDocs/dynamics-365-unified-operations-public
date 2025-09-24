---
title: Create a debit note against a purchase invoice
description: Learn how to create a debit note against a purchase order invoice in Microsoft Dynamics 365 Finance.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/10/2025
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2019-06-01
---

# Create a debit note against a purchase invoice

[!include [banner](../../includes/banner.md)]

This article explains how to create a debit note against a purchase order invoice in Microsoft Dynamics 365 Finance.

To create a debit note against a purchase invoice, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger** \> **Journals** \> **General journal**.
1. Create a journal, and name it.
1. Select **Lines**.
1. In the **Account type** field, select **Vendor**. 
1. In the **Account** field, select a value.
1. In the **Credit** field, enter a value.
1. In the **Offset account type** field, select **Ledger**. 
1. In the **Offset account** field, select a value.
1. On the **General** tab, in the **Original purchase invoice** section, in the **Original invoice number** field, select a value.
1. Verify that the **Original invoice date** field is automatically set, based on the original invoice.

    > [!NOTE]
    > You can post a revised debit note by selecting **Revised** in the **Invoice type** field and then adding a reference to the original debit note.

1. Select **Tax information**.
1. On the **GST** FastTab, in the **HSN code** field, select a value.
1. Select the **Vendor tax information** FastTab.
1. Select **OK**.

## Validate the tax details

To validate the tax detail, follow these steps.

1. Select **Tax document**.
1. Select **Close**.
1. Select **Post** \> **Post**.
1. Close the message that you receive.

### Validate the financial entries

To validate the financial entries, select **Inquiries** \> **Voucher**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
