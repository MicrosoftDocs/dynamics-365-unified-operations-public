---
title: Initialize stock levels in the warehouse
description: Learn how to get the on-hand inventory updated manually using an Inventory movement journal, including a step-by-step process.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: InventJournalMovement, InventJournalCreate, InventItemIdLookupSimple, InventLocationIdLookup, WMSLocationIdLookup   
ms.topic: how-to
ms.date: 11/12/2025
ms.custom:
  - bap-template
---

# Initialize stock levels in the warehouse

[!include [banner](../../includes/banner.md)]

This procedure shows you how to manually update the on-hand inventory by using an Inventory movement journal. (You can also update on-hand inventory by importing transactions in data entities.) You can run this guide in demo data company *USMF* where all the prerequisites like journal name, item setup, posting profiles, and accounts are available. The guide suggests specific values for the item and dimensions that are used. If you choose a different item, you might need to enter values for different dimensions.

1. Go to **Inventory management** \> **Journal entries** \> **Items** \> **Movement**.
1. Select **New**.
1. In the **Name** field, select *IMov*. Use different journal name templates for different business purposes.  
1. In the list, select the link in the selected row.
1. In the **Offset account** field, enter the value *140200*. This offset account is the default account on the journal lines. You can override the default to assign different offset accounts per line.  
1. Select **OK**.
1. Select **New**.
1. In the **Item number** field, select *A0001*.
1. In the list, select the link in the selected row.
1. Select the **Inventory dimensions** tab.
1. In the **Site** field, select site *1*.
1. In the **Warehouse** field, select warehouse *13*.
1. In the list, select the link in the selected row.
1. In the **Location** field, select location *13*.
1. In the **Quantity** field, enter a number.
1. Select **Save**.
1. Select **Post**.
1. Check or uncheck the **Transfer all posting errors to a new journal** check box. If you enable this option, any lines that fail to post are copied to a new journal. You can use the information in the log to correct the issues and then re-post the lines.  
1. Select **OK**.
1. Close the page.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
