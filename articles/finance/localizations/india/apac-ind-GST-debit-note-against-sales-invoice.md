---
title: Create a debit note against a sales invoice
description: Learn how to create a debit note against a sales invoice in Microsoft Dynamics 365 Finance.
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

# Create a debit note against a sales invoice

[!include [banner](../../includes/banner.md)]

This article explains how to create a debit note against a sales invoice in Microsoft Dynamics 365 Finance.

To create a debit note against a sales invoice, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger \> Journals \> General journal**.
1. Create a journal.
1. Enter a name.
1. Select **Lines**.
1. In the **Account type** field, select **Customer**. 
1. In the **Account** field, select a value.
1. In the **Debit** field, enter a value.
1. In the **Offset account type** field, select **Ledger**. 
1. In the **Offset account** field, select a value.
1. Select **Tax information**.
1. On the **GST** tab, in the **HSN code** field, select a value.
1. Select **OK**.

## Validate the tax details

To validate the tax details, follow these steps:

1. Select **Tax document**.
1. Select **Header**.
1. Expand the **Tax document** FastTab.
1. In the **Transaction type** field, select **Revised**.
1. In the **Original transaction id** field, select a value.
1. In the **Original transaction date** field, select a value.
1. On the **Tax details** FastTab, verify the tax amount. 
1. Select **Close**.
1. Select **Post \> Post**.
1. Close the message that you receive.

## Validate the financial entries

To validate the financial entries, select **Inquiries \> Voucher**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
