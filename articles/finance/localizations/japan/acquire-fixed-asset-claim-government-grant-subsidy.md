---
title: Acquire a fixed asset and claim for the government grant subsidy
description: Learn how to acquire a fixed asset and claim it for a government grant in Japan with Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 04/10/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm
ms.custom: 
  - bap-template
---

# Acquire a fixed asset and claim for the government grant subsidy

[!include [banner](../../includes/banner.md)]

This article explains how to acquire a fixed asset and claim it for a government grant in Japan with Microsoft Dynamics 365 Finance.

The following procedures walk you through how to acquire a fixed asset and claim it for a government grant. The procedures use the JPMF demo data.

Before you complete the procedures, you must first select the **Fixed Asset** configuration key.

## Acquire the fixed asset

To acquire the fixed asset, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a name.
1. Select **Lines**.
1. In the **Date** field, enter a date.
1. In the **Account** field, select the fixed asset to acquire.  
1. In the **Book** field, enter a value.
1. In the **Debit** field, enter a number.
1. Select **Save**.
1. Select **Post**.

## Claim the fixed asset for a government grant

To claim the fixed asset for a government grant, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Select **Save**.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Reduction entry proposal**.
1. Select **Filter**. You can filter to help find the fixed asset faster.  
1. In the **Criteria** field, enter a value.
1. Select **OK**.
1. Select **OK**.
1. In the **Date** field, enter the accounting date on which to journalize the subsidy.  
1. In the **Credit** field, enter the amount of the government grant.  
1. Select **Post**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
