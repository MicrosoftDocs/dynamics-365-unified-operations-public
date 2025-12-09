---
title: Propose additional depreciation
description: Learn how to propose additional depreciation for Japan in Microsoft Dynamics 365 Finance.
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

# Propose additional depreciation

[!include [banner](../../includes/banner.md)]

This article explains how to propose additional depreciation for Japan in Microsoft Dynamics 365 Finance.

In Japan, you can use additional depreciation under certain conditions.

Use the following procedure to propose additional depreciation. Before you begin, make sure that you acquired the fixed asset and posted the ordinary depreciation.

Before you complete the procedure, you must first select the **Fixed Asset** configuration key.

The procedure uses the JPMF demo company data.

To propose additional depreciation, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Extraordinary depreciation proposal**.
1. In the **To date** field, enter a date.
1. Select **Filter**. Using the filter helps speed up the process by focusing only on the fixed assets with the specified criteria.  
1. In the **Criteria** field, enter a value.
1. Select **OK**.
1. Select **OK**.
1. Select **Post**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
