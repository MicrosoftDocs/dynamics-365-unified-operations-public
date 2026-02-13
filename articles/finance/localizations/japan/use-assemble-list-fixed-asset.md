---
title: Use the assembly list of a fixed asset
description: Learn how to use the assembly list of a fixed asset for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetTable, AssetComponentList_JP, LedgerJournalTable, LedgerJournalTransAsset
ms.custom: 
  - bap-template
---

# Use assembly the list of a fixed asset

[!include [banner](../../includes/banner.md)]

This article explains how to use the assembly list of a fixed asset for Japan in Microsoft Dynamics 365 Finance.

In Japan, you can transfer an inventory item to a fixed asset. 

The following procedures walk you through how to use the assembly list to consume inventory items and create the fixed asset concurrently.

The procedures use the demo data company JPMF.

## Assign component in an assembly list

To assign component in an assembly list, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. In the list, select the row.
1. Select the fixed asset to which you want to assign the assembly list.  
1. On the Action Pane, select **Fixed asset**.
1. Select **Components**.
1. Select **Add**.
1. In the **Item number** field, enter a value.
1. Select **Save**.

## Use the assembly list to post a fixed asset write-up transaction

To use the assembly list to post a fixed asset write-up transaction, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Select **Lines**.
1. In the **Date** field, enter a date.
1. In the **Transaction type** field, select **Write up adjustment**.
1. In the **Account** field, select the fixed asset number that you assigned to the assembly list.  
1. In the **Debit** field, enter the cost of the inventory item.  
1. Select **Post**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
