---
title: Propose special depreciation
description: Learn how to propose special depreciations for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm
ms.custom: 
  - bap-template
---

# Propose special depreciation

[!include [banner](../../includes/banner.md)]

This article explains how to propose special depreciations for Japan in Microsoft Dynamics 365 Finance.

In Japan, a special depreciation is permitted under certain conditions. For the reserve method, this task involves two steps: you post the reserve, and then you post the reserve allocation. For the direct-off method, you just post the reserve allocation. 

Before you complete the following procedure, confirm that you acquired the fixed asset, and select the **Fixed Asset** configuration key.

The following procedures use the JPMF demo company data.

## **Post** reserve

To post the reserve, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Select **Save**.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Extraordinary depreciation proposal**.
1. In the **To date** field, enter a date.
1. Select **Filter**.
1. In the **Criteria** field, enter a value.
1. Select **OK**.
1. Select **OK**.
1. Select **Post**.

## **Post** reserve allocation

To post the reserve allocation, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Select **Save**.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Extraordinary depreciation proposal**.
1. In the **To date** field, enter a date. Depending on the allocation start convention, the reserve allocation start date might be different.  
1. Select **Filter**.
1. In the **Criteria** field, enter a value.
1. Select **OK**.
1. Select **OK**.
1. Select **Post**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
