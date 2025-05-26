---
title: Propose and post the impairment amount by using fixed asset journal
description: Learn how to propose and post the impairment amount by using a fixed asset journal for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 05/02/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset
ms.custom: 
  - bap-template
---

# Propose and post the impairment amount by using fixed asset journal

[!include [banner](../../includes/banner.md)]

This article explains how to propose and post the impairment amount by using a fixed asset journal for Japan in Microsoft Dynamics 365 Finance.

Before you complete the following procedure, you must confirm that an impairment test result is already created.

The procedure uses the demo data company JPMF.

To propose and post an impairment amount using a fixed asset journal, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Impairment proposal**.
1. In the **Impairment test ID** field, select the drop-down button to open the lookup.
1. In the list, select **JPMF-000004**.
1. Select **OK**. Two fixed assets in the impairment test are proposed with the fixed asset number, the impairment amount on credit, and the date of the impairment test.  
1. Select **Post**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
