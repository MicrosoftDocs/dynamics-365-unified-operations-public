---
title: Adjustment of the asset retirement obligation estimate
description: Learn how to adjust the asset retirement obligation (ARO) estimate in Japan with Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetTable, AssetRetirementObligation_JP, AssetRetirementObligationLine_JP, LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm
ms.custom: 
  - bap-template
---

# Adjustment of the asset retirement obligation estimate

[!include [banner](../../includes/banner.md)]

This article explains how to adjust the asset retirement obligation (ARO) estimate in Japan with Microsoft Dynamics 365 Finance.

The following procedures walk you through how to adjust and post the ARO amount. The procedure was created using the demo data company JPMF.

Before you complete the procedures, you must first select the **Fixed Asset** configuration key.

## Adjust the ARO estimate

To adjust the ARO estimate, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Asset retirement obligations \> Fixed assets**.
1. In the list, find and select the desired record.
1. On the Action Pane, select **Fixed asset**.
1. Select **Asset retirement obligation**.
1. Select **Upward** to open the drop dialog. You can also select **Downward** for minus adjustment.  
1. In the **Transaction date** field, enter the date on which to post the adjustment amount.
1. In the **Upward** field, enter the amount of adjustment.
1. Select **OK**.

## Post the adjustment

To post the adjustment, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Asset retirement obligations \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a name.
1. Select **Save**.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Capitalized asset retirement obligation**.
1. In the **To date** field, enter a date.
1. Select **Filter**.
1. In the **Criteria field**, enter a value.
1. Select **OK**.
1. Select **OK**. Confirm the adjustment is proposed. The amount proposed is discounted to the present value.  
1. Select **Post**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
