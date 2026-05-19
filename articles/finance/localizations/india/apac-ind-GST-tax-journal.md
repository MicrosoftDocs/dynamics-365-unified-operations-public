---
title: Create a tax journal
description: Learn how to create a tax journal, including a step-by-step process for reversing charge transactions where tax credits should be claimed.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/01/2026
ms.reviewer: johnmichalak 
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Create a tax journal

[!include [banner](../../includes/banner.md)]

You can use a tax journal to post a tax adjustment journal. For reverse charge transactions where the tax credit should be claimed after the authority settlement, you can use a tax journal to claim the tax credit.

1. Go to **Tax** \> **Journals entries** \> **Tax journals**.
1. Create a record.
1. In the **Date** field, enter a value.
1. On the **Tax journal lines** FastTab, select **Add**.
1. On the **Tax account** FastTab, in the **Account type** field, select **Tax**.
1. In the **Tax type** field, select **GST**.
1. In the **Tax component** field, select a value.
1. In the **Tax posting type** field, select **Interim recoverable**.
1. In the **Account** field, select a value.
1. In the **Offset account type** field, select **Tax**.
1. In the **Tax type** field, select **GST**.
1. In the **Tax component** field, select a value.
1. In the **Tax posting type** field, select **Tax recoverable**.
1. In the **Account** field, select a value.
1. On the journal line, in the **Credit** field, enter a value, and then select **Tax information**.
1. On the **GST** tab, select **OK**.
1. Select **Tax document**.
1. Select **Close**, and then select **Post**.
1. Close the message that you receive, and then select **Voucher**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
