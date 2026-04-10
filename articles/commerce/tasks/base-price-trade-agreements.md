--- 
title: Base price and trade agreements
description: Learn how to create channel-specific sales price trade agreements in Microsoft Dynamics 365 Commerce. 
author: josaw1
ms.date: 02/06/2026
ms.topic: how-to 
ms.search.form: PriceDiscGroup, RetailStoreTable, RetailChannelPriceGroup, EcoResProductDetailsExtended, PriceDiscAdmTable, PriceDiscAdm   
ms.reviewer: v-griffinc 
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-06-30 
ms.custom: 
  - bap-template
---
# Base price and trade agreements

[!include [banner](../includes/banner.md)]

This article explains how to create channel-specific sales price trade agreements in Microsoft Dynamics 365 Commerce.

Price groups are how trade agreements are assigned to specific channels. Using price groups to assign trade agreements to a channel enables channel-specific pricing.  

The following procedure walks through creating channel-specific sales price trade agreements. This procedure uses the USRT demo data company.

To create channel-specific sales price trade agreements, follow these steps:

1. In Commerce headquarters, go to **Modules > Retail and Commerce > Pricing and discounts management > Price groups > All price groups**. 
1. Select **New**.
1. In the **Price groups** field, type a value.
1. In the **Name** field, type a value.
1. Select **Save**.
1. Close the page.
1. In the **Navigation pane**, go to **Modules > Retail and Commerce > Channels > Stores > All stores**.
1. In the list, select 'New York'
1. On the Action Pane, select **Store**.
1. Select **Price groups**.
1. Select **New**.
1. In the **Price groups** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. Select **Save**.
1. Close the page.
1. Close the page.
1. In the **Navigation pane**, go to **Modules > Retail and Commerce > Products and categories > Released products by category**.
1. In the list, select the link in the selected row.
1. Select **Edit**.
1. Expand the **Sell** FastTab.
1. In the **Price** field, enter a number. This price is used if no applicable trade agreements are found.  
1. Select **Save**.
1. On the **Action Pane**, select **Sell**.
1. Select **Create trade agreements**.
1. Select **New**.
1. In the **Name** field, select the drop-down button to open the lookup.
1. In the list, select **Commerce**. In the demo data, the **Commerce** journal name has the default relation of **Price (sales)**. That means all new lines created default to sales price trade agreements.  
1. On the **Action pane**, select **Lines**.
1. In the **Party code type** field, select 'Group'.
1. In the **Account selection** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record. This selection completes the link from channel to price group to trade agreement.    
1. In the **Item relation** field, type a value.
1. In the **Amount in currency** field, enter a number.
1. On the **Details** FastTab, check or uncheck the **Find next** checkbox. When **Find next** is set to **Yes**, the pricing engine continues to search for applicable trade agreements with a lower sale price. When **Find next** is set to **No**, the price engine stops searching and uses the trade agreement.    
1. Select **Post**.
1. Select **OK**.
1. Close the page.
1. On the **Action Pane**, select Sell.
1. Select **Sales price**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]