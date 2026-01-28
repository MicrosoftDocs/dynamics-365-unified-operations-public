---
title: Configure main accounts for asset retirement obligation posting and market discount rates
description: Learn how to configure main accounts for asset retirement obligation posting and market discount rates in Japan with Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetPosting, AssetDiscountRateSchedule_JP
ms.custom: 
  - bap-template
---

# Configure main accounts for asset retirement obligation posting and market discount rates

[!include [banner](../../includes/banner.md)]

This article explains how to configure main accounts for asset retirement obligation posting and market discount rates in Japan with Microsoft Dynamics 365 Finance.

For Japan, you need to assess and post an asset retirement obligation when you acquire a fixed asset with legal obligations at retirement. You must configure all the main accounts before posting any transaction of asset retirement obligation.

The following procedures walk you through how to configure the main accounts for asset retirement obligation posting. The procedures use the JPMF demo company data.

Before you complete the procedures, you must first select the **Fixed Asset** configuration key.

## Configure ledger accounts for asset retirement obligation posting

To configure ledger accounts for asset retirement obligation posting, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Fixed asset posting profiles**.
1. Expand the **Asset retirement obligation** section.
1. Select **Add**.
1. In the **Book** field, enter a value.
1. In the **Groupings** field, select an option.
1. In the **Fixed asset number** field, enter a value. Optionally, when you select **Groupings** as **Group** or **Table**, specify a fixed asset group or a fixed asset.  
1. In the **Main account** field, enter a value.
1. In the **Offset account** field, enter a value.
1. In the **Select** field, select an option.
1. Expand the **Disposal parameters by document type** section.
1. In the **Sale or scrap** field, select an option. You must set up both the **Sales and Scrap** type of disposal accounts before you can post transactions of those types.  
1. Select **New**.
1. In the **Book** field, enter a value.
1. In the **Valid for** field, select an option.
1. In the **Fixed asset relation** field, enter a value. Optionally, when you select **Valid for** as **Group** or **Table**, specify a fixed asset group or a fixed asset.  
1. In the **Main account** field, enter a value.
1. In the **Offset account** field, enter a value.

## Configure market discount rates

To configure market discount rates, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Cashflow discount rates**.
1. Select **New**.
1. In the **Start date** field, enter a date.
1. In the **Market discount rate percentage** field, enter a number.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
