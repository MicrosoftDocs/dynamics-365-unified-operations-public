---
title: Propose and post accelerated depreciation
description: Learn how to propose and post accelerated depreciation for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 05/02/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset, AssetAcceleratedDepDocument_JP
ms.custom: 
  - bap-template
---

# Propose and post accelerated depreciation

[!include [banner](../../includes/banner.md)]

This article explains how to propose and post accelerated depreciation for Japan in Microsoft Dynamics 365 Finance.

For Japan, you can propose an accelerated depreciation based on the data on confirmed accelerated depreciation documents. The accelerated depreciation proposal doesn't propose ordinary depreciation. The following procedure must be completed after you post ordinary depreciation.

Before you complete the procedure, you must first select the **Fixed Asset** configuration key.

The procedure was created using the demo data company JPMF.

To propose and post accelerated depreciation, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Select **Save**.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Accelerated depreciation proposal**.
1. In the **To date** field, enter a date. 
1. Select **OK**.
1. Confirm that the accelerated depreciation is proposed. The ordinary depreciation isn't handled, so you still need to propose and post it.  
1. Select **Post**.
1. Close the page.
1. Go to **Fixed assets \> Periodic tasks \> Accelerated depreciation \> Accelerated depreciation document**.
1. Confirm that the status of posted document has been updated.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
