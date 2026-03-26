---
title: Propose and post the impairment amount on a cash generating unit
description: Learn how to propose and post impairment amounts that are recognized and calculated on a cash generating unit for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset
ms.custom: 
  - bap-template
---

# Propose and post the impairment amount on a cash generating unit

[!include [banner](../../includes/banner.md)]

This article explains how to propose and post impairment amounts that you recognize and calculate on a cash generating unit for Japan in Microsoft Dynamics 365 Finance.

For Japan, after you calculate the impairment amount, you can propose and post it in a fixed asset journal.

Before you complete the following procedure, you must create and confirm a recognition test, and also select the **Fixed Asset** configuration key.

The procedure uses the demo data company JPMF.

To propose and post impairment amounts that you recognize and calculate on a cash generating unit, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter or select a value.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Impairment proposal**.
1. In the **Impairment test ID** field, enter the ID of the recognition test that you want to post.
1. Select **OK**.
1. Select **Post**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]