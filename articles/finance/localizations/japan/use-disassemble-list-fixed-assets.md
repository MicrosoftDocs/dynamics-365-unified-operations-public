---
title: Use disassemble list for fixed assets
description: Learn how to use a disassemble list for fixed assets for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 05/09/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetTable, AssetComponentList_JP, AssetComponentPriceCalcDropDialog_JP, LedgerJournalTable, LedgerJournalTransAsset
ms.custom: 
  - bap-template
---

# Use disassemble list for fixed assets

[!include [banner](../../includes/banner.md)]

This article explains how to use a disassemble list for fixed assets for Japan in Microsoft Dynamics 365 Finance.

In Japan, you can transfer a component of a fixed asset to inventory. 

The following procedures walk you through how to use the disassembly list to write down the fixed asset and create the inventory concurrently.

Before you can complete the procedures, you must first complete the tasks in [Use assemble list of a fixed asset](use-assemble-list-fixed-asset.md). 

The procedures use the demo data company JPMF.

## Enter the disassembly list

To enter the disassembly list, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. In the list, mark the selected row.
1. On the Action Pane, select **Fixed asset**.
1. Select **Components**.
1. In the list, mark the selected row.
1. Select **Add to disassembly list**.
1. In the **Add** field, enter a number.
1. Select **OK**.
1. Select the **Disassembly list** FastTab.
1. Verify that the record was added to the disassembly list.  
1. Optionally, you can also choose to add the item to the disassembly list by selecting **Add**.  
1. Select **Calculate prices** to open the drop dialog.
1. Select **Calculate**.
1. Verify that the costs are updated.  
1. You can modify the market value, which is entered in the journal as the credit amount for the write down of the fixed asset.  

## Post the disassembly list

To post the disassembly list, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed asset \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Select **Lines**.
1. In the **Date** field, enter a date.
1. In the **Transaction** type field, select **Write down adjustment**.
1. In the **Account** field, entert a value.
1. Verify that the credit amount is automatically retrieved as the cost from the disassembly list.  
1. You can modify the credit amount.  
1. Select **Post**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
