---
title: Depreciate and accrue the interest expense for asset retirement obligations
description: Learn how to depreciate and accrue the interest expense for asset retirement obligations for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 04/18/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm
ms.custom: 
  - bap-template
---

# Depreciate and accrue the interest expense for asset retirement obligations

[!include [banner](../../includes/banner.md)]

This article explains how to depreciate and accrue the interest expense for asset retirement obligations (ARO) for Japan in Microsoft Dynamics 365 Finance.

For Japan, the depreciation of ARO is processed along with the fixed asset. Interest expenses need to be accrued to recognize the full amount of the ARO.

The following procedures were completed using the JPMF demo company data.

Before you complete the procedures, you must first select the **Fixed Asset** configuration key.

## Depreciate a fixed asset with asset retirement obligation

To depreciate a fixed asset with asset retirement obligation, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, select a value.
1. Select **Save**.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Depreciation proposal**.
1. In the **To date** field, enter a date.
1. Select **Filter**.
1. In the **Criteria** field, enter a value.
1. Select **OK**.
1. Select **OK**. The depreciation of asset retirement obligation is indicated by **Document type** field value.  
1. Select **Post**.

## Accrue the interest expense

To accrue the interest expense, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Select **Save**.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Asset retirement obligation - accretion expense**.
1. In the **To date** field, enter a date.
1. Select **Filter**.
1. In the **Criteria** field, enter a value.
1. Select **OK**.
1. Select **OK**. Confirm that the records for interest expenses are proposed. The interest expenses are indicated by the transaction type.  
1. Select **Post**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
