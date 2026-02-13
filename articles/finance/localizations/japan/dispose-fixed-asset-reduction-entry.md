---
title: Dispose of a fixed asset with reduction entry
description: Learn how to dispose of a fixed asset with reduction entry for Japan in Microsoft Dynamics 365 Finance.
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

# Dispose of a fixed asset with reduction entry

[!include [banner](../../includes/banner.md)]

This article explains how to dispose of a fixed asset with reduction entry for Japan in Microsoft Dynamics 365 Finance.

Use this task to learn how to dispose of a fixed asset with reduction entry for Japan.

The following procedure uses the JPMF demo data company.

Before you complete the procedure, select the **Fixed Asset** configuration key.

To dispose of a fixed asset with reduction entry, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Disposal - scrap**.
1. Enter the date of disposal transaction.
1. Select **Filter**.
1. In the **Criteria** field, enter a value.
1. Select **OK**.
1. Select **OK**.
1. Enter the main accounts to which the fixed asset disposal expenses are posted. You can also choose to enter the disposal expenses later in a journal. The fixed asset main account, accumulated depreciation main account, and other fixed asset related accounts are automatically determined by the configuration in the fixed asset posting profile.  
    - The disposal of reduction entry document is separated from that of the fixed asset.  
    - The original subsidy amount and accumulated amortization amount are automatically determined by the configuration in the fixed asset posting profile.  
1. Select **Post**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
